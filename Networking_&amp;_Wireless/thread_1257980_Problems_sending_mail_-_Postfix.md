---
title: "Problems sending mail - Postfix"
date: 2009-09-04
forum: Networking &amp; Wireless
---

### Post by w1z8it on 2009-09-04
I'm getting various errors when I try to send mail using the following:

```
MAIL FROM: root@chaotic-realms.com
250 2.1.0 Ok
RCPT TO: w1z8it@hotmail.com
250 2.1.5 Ok
DATA
354 End data with <CR><LF>.<CR><LF>
SUBJECT: Test
This is a test!
.
250 2.0.0 Ok: queued as E511238C076
421 4.4.2 mail.chaotic-realms.com Error: timeout exceeded

```[B]

Helpful information:

ehlo localhost
[/B]```
250-mail.chaotic-realms.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH LOGIN CRAM-MD5 PLAIN NTLM DIGEST-MD5
250-AUTH=LOGIN CRAM-MD5 PLAIN NTLM DIGEST-MD5
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
```[B]

mail.info
[/B]```
Sep  4 19:11:55 server postfix/master[2592]: daemon started -- version 2.5.5, configuration /etc/postfix
Sep  4 19:11:56 server postfix/qmgr[2615]: 1116438C06B: from=<root@chaotic-realms.com>, size=381, nrcpt=1 (queue active)
Sep  4 19:11:56 server postfix/smtp[2684]: 1116438C06B: to=<w1z8it@hotmail.com>, relay=none, delay=1632, delays=1632/0.48/0/0, dsn=4.4.3, status=deferred (Host or domain name not found. Name service error for name=hotmail.com type=MX: Host not found, try again)
Sep  4 19:12:07 server postfix/master[2592]: reload configuration /etc/postfix
Sep  4 19:12:07 server postfix/qmgr[3423]: 1116438C06B: from=<root@chaotic-realms.com>, size=381, nrcpt=1 (queue active)
Sep  4 19:12:07 server postfix/qmgr[3423]: DB02F38C075: from=<root@chaotic-realms.com>, size=384, nrcpt=1 (queue active)
Sep  4 19:12:39 server postfix/smtp[3435]: connect to mx1.hotmail.com[65.55.37.88]:25: Connection timed out
Sep  4 19:12:39 server postfix/smtp[3443]: connect to mx3.hotmail.com[65.55.37.72]:25: Connection timed out
Sep  4 19:12:39 server postfix/smtpd[3558]: warning: ::1: address not listed for hostname localhost
Sep  4 19:12:39 server postfix/smtpd[3558]: connect from unknown[::1]
Sep  4 19:13:05 server postfix/smtpd[3558]: E511238C076: client=unknown[::1]
Sep  4 19:13:09 server postfix/smtp[3435]: connect to mx2.hotmail.com[65.55.92.152]:25: Connection timed out
Sep  4 19:13:09 server postfix/smtp[3443]: connect to mx2.hotmail.com[65.55.37.88]:25: Connection timed out
Sep  4 19:13:23 server postfix/cleanup[3567]: E511238C076: message-id=<20090904171305.E511238C076@mail.chaotic-realms.com>
Sep  4 19:13:23 server postfix/qmgr[3423]: E511238C076: from=<root@chaotic-realms.com>, size=383, nrcpt=1 (queue active)
Sep  4 19:13:39 server postfix/smtp[3435]: connect to mx1.hotmail.com[65.55.92.136]:25: Connection timed out
Sep  4 19:13:39 server postfix/smtp[3443]: connect to mx4.hotmail.com[65.55.37.120]:25: Connection timed out
Sep  4 19:13:53 server postfix/smtp[3574]: connect to mx4.hotmail.com[65.55.37.88]:25: Connection timed out
Sep  4 19:14:09 server postfix/smtp[3443]: connect to mx2.hotmail.com[65.55.37.120]:25: Connection timed out
Sep  4 19:14:09 server postfix/smtp[3435]: connect to mx4.hotmail.com[65.55.37.104]:25: Connection timed out
```[B]

mail.log
[/B]```
Sep  4 19:11:55 server postfix/master[2592]: daemon started -- version 2.5.5, configuration /etc/postfix
Sep  4 19:11:56 server postfix/qmgr[2615]: 1116438C06B: from=<root@chaotic-realms.com>, size=381, nrcpt=1 (queue active)
Sep  4 19:11:56 server postfix/smtp[2684]: 1116438C06B: to=<w1z8it@hotmail.com>, relay=none, delay=1632, delays=1632/0.48/0/0, dsn=4.4.3, status=deferred (Host or domain name not found. Name service error for name=hotmail.com type=MX: Host not found, try again)
Sep  4 19:12:07 server postfix/master[2592]: reload configuration /etc/postfix
Sep  4 19:12:07 server postfix/qmgr[3423]: 1116438C06B: from=<root@chaotic-realms.com>, size=381, nrcpt=1 (queue active)
Sep  4 19:12:07 server postfix/qmgr[3423]: DB02F38C075: from=<root@chaotic-realms.com>, size=384, nrcpt=1 (queue active)
Sep  4 19:12:39 server postfix/smtp[3435]: connect to mx1.hotmail.com[65.55.37.88]:25: Connection timed out
Sep  4 19:12:39 server postfix/smtp[3443]: connect to mx3.hotmail.com[65.55.37.72]:25: Connection timed out
Sep  4 19:12:39 server postfix/smtpd[3558]: warning: ::1: address not listed for hostname localhost
Sep  4 19:12:39 server postfix/smtpd[3558]: connect from unknown[::1]
Sep  4 19:13:05 server postfix/smtpd[3558]: E511238C076: client=unknown[::1]
Sep  4 19:13:09 server postfix/smtp[3435]: connect to mx2.hotmail.com[65.55.92.152]:25: Connection timed out
Sep  4 19:13:09 server postfix/smtp[3443]: connect to mx2.hotmail.com[65.55.37.88]:25: Connection timed out
Sep  4 19:13:23 server postfix/cleanup[3567]: E511238C076: message-id=<20090904171305.E511238C076@mail.chaotic-realms.com>
Sep  4 19:13:23 server postfix/qmgr[3423]: E511238C076: from=<root@chaotic-realms.com>, size=383, nrcpt=1 (queue active)
Sep  4 19:13:39 server postfix/smtp[3435]: connect to mx1.hotmail.com[65.55.92.136]:25: Connection timed out
Sep  4 19:13:39 server postfix/smtp[3443]: connect to mx4.hotmail.com[65.55.37.120]:25: Connection timed out
Sep  4 19:13:53 server postfix/smtp[3574]: connect to mx4.hotmail.com[65.55.37.88]:25: Connection timed out
Sep  4 19:14:09 server postfix/smtp[3443]: connect to mx2.hotmail.com[65.55.37.120]:25: Connection timed out
Sep  4 19:14:09 server postfix/smtp[3435]: connect to mx4.hotmail.com[65.55.37.104]:25: Connection timed out
Sep  4 19:14:23 server postfix/smtp[3574]: connect to mx2.hotmail.com[65.55.37.88]:25: Connection timed out
Sep  4 19:14:39 server postfix/smtp[3443]: connect to mx1.hotmail.com[65.55.37.88]:25: Connection timed out
Sep  4 19:14:39 server postfix/smtp[3435]: connect to mx4.hotmail.com[65.55.37.120]:25: Connection timed out
Sep  4 19:14:39 server postfix/smtp[3443]: DB02F38C075: to=<w1z8it@hotmail.com>, relay=none, delay=425, delays=274/1.4/150/0, dsn=4.4.1, status=deferred (connect to mx1.hotmail.com[65.55.37.88]:25: Connection timed out)
Sep  4 19:14:39 server postfix/smtp[3435]: 1116438C06B: to=<w1z8it@hotmail.com>, relay=none, delay=1795, delays=1644/1.4/150/0, dsn=4.4.1, status=deferred (connect to mx4.hotmail.com[65.55.37.120]:25: Connection timed out)
```[B]

mail.warn
[/B]```
Sep  4 19:12:39 server postfix/smtpd[3558]: warning: ::1: address not listed for hostname localhost
```[B]

mail.err (Empty)

postconf -n[/B]
```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
inet_interfaces = all
inet_protocols = all
mailbox_size_limit = 0
mydestination = mail.chaotic-realms.com, localhost, www.chaotic-realms.com
myhostname = mail.chaotic-realms.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost = 
smtp_tls_note_starttls_offer = yes
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = 
smtpd_sasl_security_options = noanonymous
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
```Any ideas?

---

### Post by w1z8it on 2009-09-04
Any takers?

If my ISP are blocking port 25, does this mean I'm fuxored? Is there any workaround for this?

---

### Post by aiharak on 2009-09-04
> **w1z8it said:**
> Any takers?

If my ISP are blocking port 25, does this mean I'm fuxored? Is there any workaround for this?

If your ISP blocks port 25, you could always use a different port.

---

### Post by w1z8it on 2009-09-04
> **aiharak said:**
> If your ISP blocks port 25, you could always use a different port.

That's what I thought but a friend who has better knowledge of these things than me said that it has to be port 25.

Does anything look wrong in the info I posted?

---

### Post by w1z8it on 2009-09-04
What my friend said the reason it won't work on another port:

> well, the problem is that they are only listening on port 25
like trying to ssh to a machine on port 100 when ssh only listens on port 22
 I have no idea about this tbh, what's your take?

---

### Post by aiharak on 2009-09-04
If you don't use port 25 for incoming mail, you probably won't be able to receive mail. You'll have to have someone else's server receive it first on port 25, then send it to you.

---

### Post by w1z8it on 2009-09-04
> **aiharak said:**
> If you don't use port 25 for incoming mail, you probably won't be able to receive mail. You'll have to have someone else's server receive it first on port 25, then send it to you.


I only want to send mail.

---

### Post by aiharak on 2009-09-04
You shouldn't have any problems sending mail out of a non standard smtp port

Did you try your ISP's SMTP server?

---

### Post by w1z8it on 2009-09-04
> **aiharak said:**
> You shouldn't have any problems sending mail out of a non standard smtp port

But I am having real difficulty, any ideas what might be wrong, do you need any more info? I'm at my witts end here.

---

### Post by aiharak on 2009-09-04
Try asking your ISP for their SMTP server and configure postfix to use that. On postfix's configuration, find "relayhost = " and add the hostname your ISP tells you and restart.

---

### Post by w1z8it on 2009-09-04
> **aiharak said:**
> Try asking your ISP for their SMTP server and configure postfix to use that. On postfix's configuration, find "relayhost = " and add the hostname your ISP tells you and restart.

You were right, my ISP have a specific server for this, I got their SMTP server and it works, thanks :)

---

