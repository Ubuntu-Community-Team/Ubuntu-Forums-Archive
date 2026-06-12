---
title: "Postix and DNS configuration"
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by cellarosi on 2010-02-09
Hi, I've tried to install and configuring postfix and courier-imap on my virtual server.
It can send e-mail (because I do it by gmail ;) ) and it can receive the mail from itself to.

I've set a thunderbird account and it can read all mails in my mailbox.

The problem occurred when I try to send an e-mail from an external domain to my domain. 
For example if i try to send an e-mail from [email]example@gmail.com[/email] to 
[email]example@mydomain.com[/email], after few seconds in gmail account compare the mail where it says:

[INDENT]Delivery to the following recipient failed permanently:

     [EMAIL="example@mydomain.com"]example@mydomain.com[/EMAIL]

Technical details of permanent failure: 
Google tried to deliver your message, but it was rejected by the recipient domain. We recommend contacting the other email provider for further information about the cause of this error. The error that the other server returned was: 550 550 #5.1.0 Address rejected [EMAIL="example@mydomain.com"]example@mydomain.com[/EMAIL] (state 14).[/INDENT]

I can connect to my server by telnet on 25 and 143 ports. On 143 login successful.

The mail log file has no changes when i try to sent an external email to my mail server so i don't know if it's a server/postfix problem or DNS problem or what else. 

This is my main.cf postfix configuration file:

[INDENT]# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.
home_mailbox = Maildir/
myhostname = ovz-test
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mydomain.com, ovz-test, localhost.localdomain, localhost, $mydomain
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
[/INDENT]

MX record contains mail.mydomain.com and i have inserted a A record on my DNS manager that link mail.mydomain.com to my IP addres. In fact I can connect myself to mail.mydomain.com on 25 and 143 ports.
So i think that configuration file is right. 

Please help me and thanks in advance.

---

### Post by gombadi on 2010-02-09
> 
 The error that the other server returned was: 550 550 #5.1.0 Address rejected [email]example@mydomain.com[/email] (state 14).

I can connect to my server by telnet on 25 and 143 ports.


Being able to connect and getting the system to accept an email are different things. I don't think it is a dns issue.

Does the user example exist in your system as the above message is saying that your server can not find the example user.

> 
The mail log file has no changes when i try to sent an external email to my mail server so i don't know if it's a server/postfix problem or DNS problem or what else


Not sure why it is not showing up in the logs but /var/log/syslog should contain the logs from postfix unless you have changed the default logging config. If you find the postfix files then they should show you why the message is being rejected.

---

### Post by cellarosi on 2010-02-10
> Does the user example exist in your system as the above message is saying that your server can not find the example user.

Sure. In fact when I connect my pc to 25 ports of mydomain.com I can send an email and all works. But when I try to do it by thunderbird from gmail the error occurred. 

> Not sure why it is not showing up in the logs but /var/log/syslog should contain the logs from postfix unless you have changed the default logging config. If you find the postfix files then they should show you why the message is being rejected.

I tried in syslog file to but nothing is write about the reject.
Probably the problem is before.

Other ideas?? :(

---

