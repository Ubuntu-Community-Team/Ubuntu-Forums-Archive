---
title: "Postfix SASL + MySQL Issue"
date: 2013-03-07
forum: Networking &amp; Wireless
---

### Post by atom94 on 2013-03-07
Hi all. I'm trying to set up a mailserver using Postfix, Courier and MySQL for the user database. So far I've got Postfix and Courier working properly, now I want to get SASL authentication working. I've set up SASL for both IMAP and SMTP and neither will let me log in. At the moment I'm only trying to fix SMTP and will deal with IMAP later, although I think it's the same problem with both so hopefully fixing one will fix the other too.

I'm following this tutorial: [http://flurdy.com/docs/postfix/#config-secure-auth](http://flurdy.com/docs/postfix/#config-secure-auth)

I've made the following changes to /etc/postfix/main.cf:
```
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain=

smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, warn_if_reject, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:10023, permit
```

And to /etc/default/saslauthd:
```
START=yes
OPTIONS="-r -c -m /var/spool/postfix/var/run/saslauthd"
```

I can post the full files on request if necessary. I also added a new file at /etc/postfix/sasl/smtpd.conf:
```
pwcheck_method: saslauthd
mech_list: plain login cram-md5 digest-md5
log_level: 7
allow_plaintext: true
auxprop_plugin: sql
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: mail
sql_passwd: [removed]
sql_database: maildb
sql_select: select crypt from users where id='%u@spherical-sphinx.com' and enabled = 1;
```

Finally I added /etc/pam.d/smtp:
```
auth required pam_mysql.so user=mail passwd=[removed] host=127.0.0.1 db=maildb table=users usercolumn=id passwdcolumn=crypt crypt=1
account sufficient pam_mysql.so user=mail passwd=[removed] host=127.0.0.1 db=maildb table=users usercolumn=id passwdcolumn=crypt crypt=1
```

I then tried connecting with the following SMTP settings in Thunderbird:[INDENT]**Server Name:** mail.spherical-sphinx.com
**Port:** 25
**Connection security:** None (I plan on setting up TLS eventually, but need to get email working to validate my domain with the CA first).
**Authentication method:** Encrypted password
**User Name:** [EMAIL="webmaster@spherical-sphinx.com"]webmaster@spherical-sphinx.com[/EMAIL][/INDENT]

When I try to send an email, I get a warning that the login has failed, and am prompted to re-enter my password. I'm sure that the password is right because I have entered it multiple times, and have reset it on the server already. Also, everything works fine if I use cleartext passwords, so the problem must be with the SASL authentication, not with the MySQL database or another part of the system.

The following gets added to /var/log/mail.log on each login attempt:
```
Mar  7 19:58:57 sirius postfix/smtpd[2614]: connect from portal[192.168.1.1]
Mar  7 19:58:57 sirius postfix/smtpd[2614]: warning: SASL authentication failure: incorrect digest response
Mar  7 19:58:57 sirius postfix/smtpd[2614]: warning: portal[192.168.1.1]: SASL CRAM-MD5 authentication failed: authentication failure
Mar  7 19:59:02 sirius postfix/smtpd[2614]: disconnect from portal[192.168.1.1]
```

I'm also seeing this in /var/log/auth.log:
```
Mar  7 19:58:57 sirius postfix/smtpd[2614]: sql auxprop plugin using mysql engine
Mar  7 19:58:57 sirius postfix/smtpd[2614]: sql plugin Parse the username webmaster@spherical-sphinx.com
Mar  7 19:58:57 sirius postfix/smtpd[2614]: sql plugin try and connect to a host
Mar  7 19:58:57 sirius postfix/smtpd[2614]: sql plugin trying to open db 'maildb' on host '127.0.0.1'
Mar  7 19:58:57 sirius postfix/smtpd[2614]: begin transaction
Mar  7 19:58:57 sirius postfix/smtpd[2614]: sql plugin create statement from userPassword webmaster spherical-sphinx.com
Mar  7 19:58:57 sirius postfix/smtpd[2614]: sql plugin doing query select crypt from users where id='webmaster@spherical-sphinx.com' and enabled = 1;;
Mar  7 19:58:57 sirius postfix/smtpd[2614]: sql plugin create statement from cmusaslsecretCRAM-MD5 webmaster spherical-sphinx.com
Mar  7 19:58:57 sirius postfix/smtpd[2614]: sql plugin doing query select crypt from users where id='webmaster@spherical-sphinx.com' and enabled = 1;;
Mar  7 19:58:57 sirius postfix/smtpd[2614]: commit transaction
Mar  7 19:58:57 sirius postfix/smtpd[2614]: sql plugin Parse the username webmaster@spherical-sphinx.com
Mar  7 19:58:57 sirius postfix/smtpd[2614]: sql plugin try and connect to a host
Mar  7 19:58:57 sirius postfix/smtpd[2614]: sql plugin trying to open db 'maildb' on host '127.0.0.1'
```

I've tried changing all sorts of settings but can't get anything to work in SASL. Plaintext login works fine but SASL fails.

---

### Post by InToSSH on 2013-10-17
Hello,
I know this question is old, but I am now installing mail server on my Ubuntu machine following the same tutorial and I have ran across the same problem as described here.. Could anyone, please, help me how to get this to work?
Thank you in advance.

---

### Post by erling@eph.dk on 2013-10-19
Hej 
Well i can try.
I run a server with that setup. And it is running smoothly.
I am however not an expert in support.
I can se he made the 11'th version I used version 10 with 10.04 now on the run updated to 12.04
Have you followed the guide to the letter?

/erling

---

### Post by erling@eph.dk on 2013-10-21
I had time too look it over and compare whith my own server.

If you look and the end af his paragrap about sasl, he writes:

In some situations SASL and TLS do not play well together. 		Those situations are in combinations of storing encrypted passwords, 		using MD5 authentication over encrypted traffic. 		I recommend, insisting on TLS traffic with your authenticating clients, 		which then negates the need for SASL.

I use tls on courier and postfix.
users can only login via tls or ssl.
they send the password in plain txt.
all passwords are stored encrypted in mysql.

I don't use sasl for courier

you wil need sasl to authenticate smtp to a encrypted mysql password.
this way the password wil only be in plaintext when postfix is checking it against the database.

/erling

---

### Post by InToSSH on 2013-10-22
Thank you for your response. Yes I followed the guide in every step.
Actually now I am just testing the SASL without TLS. I was able to get it to work but not with PAM and encrypted passwords in the DB. When I use plaintext passwords in my database for virtual mailboxes, than it works..
But now I think your solution is better to use TLS/SSL and have encrypted passwords in database, because I dont like having passwords as plaintext in my DB much, though its accessible only locally.
So now I will try to setup TLS properly and strict users to not to be able to login without it.

---

### Post by erling@eph.dk on 2013-11-06
Sorry i havn't been here for some time.
I have been bussy with my own server.
Hardware breakdown and some troublesome updates to Horde 5 groupware.
Did you get it up and running

/erling

---

