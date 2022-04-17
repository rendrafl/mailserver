# Mailserver
Assignment Online-DNET


1. ##install postfix
- apt install postfix -> internet site -> domainsaya.com
- systemctl status postfix -> (active)

2. ##configure postfix
- postconf "home_mailbox = Maildir/"
- postconf -n

3. ##install dovecot
- apt install dovecot-imapd dovecot-pop3d dovecot-core
- systemctl status dovecot (active & enabled)
- systemctl reload postfix (status reloaded active)

4. setup mail

- vim /etc/dovecot/dovecot.conf -> add (protocols = imap imaps pop3 pop3s) -> systemctl restart dovecot

- cd /etc/dovecot/conf.d
- vim 10-mail.conf
- remark mail_location = maildir:~/Maildir
- mark mail_location
- doveconf -n
- cd /etc/skel/
- rm Maildir
- mkdir -p Maildir/.Drafts Maildir/.Drafts/cur Maildir/.Drafts/new Maildir/.Drafts/tmp
- mkdir -p Maildir/.Sent Maildir/.Sent/cur Maildir/.Sent/new Maildir/.Sent/tmp
- mkdir -p Maildir/.Trash Maildir/.Trash/cur Maildir/.Trash/new Maildir/.Trash/tmp
- mkdir -p Maildir/.Templates Maildir/.Templates/cur Maildir/.Templates/new Maildir/.Templates/tmp
- mkdir Maildir/cur Maildir/new Maildir/tmp
- chmod 700 -R Maildir/

5. add user
- adduser --gecos "" rendra
- adduser --gecos "" felani

6. checkdir
- su - rendra -> logout

7. config mutt
- apt install mutt
- cd .mutt/

set imap_user = "felani"
set imap_pass = "felani"

set folder = imaps://domainsaya.com
set spoolfile = +INBOX

set realname =  'Felani fl'
set from = "$imap_user"
set use_from = yes

mailboxes INBOX

set sidebar_visible = yes
set timeout=1
set sort=reverse-date
source ~/.mutt/mutt_colors

- vim muttrc
- vim mutt_colors
- su - rendra
- ssh felani@domainsaya.com


rendra
- mutt
- accept certificate

felani
- vim .mutt/muttrc
- set imap_user = "felani"
- set imap_pass = "felani"
- set_realname = 'Felani fl'

rendra
- vim .mutt/muttrc
- set imap_user = "rendra"
- set imap_pass = "rendra"
- set_realname = 'Rendra fl'


