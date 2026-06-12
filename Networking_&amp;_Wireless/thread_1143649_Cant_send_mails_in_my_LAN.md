---
title: "Cant send mails in my LAN"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by shade5 on 2009-04-30
Hello.

I want to send mails in my LAN. I instaled thoses packets to do it:

> postfix
libsasl2-modules 
mailx


But in vain. I am able to send mails to my own machine (localhost). But when I try to send it to other machines in my LAN they are not sent. 

This is what my MAILER-DAEMON says:

> From MAILER-DAEMON  Wed Apr 29 15:50:42 2009
X-Original-To: x@x-desktop
Date: Wed, 29 Apr 2009 15:50:42 +0200 (CEST)
From: MAILER-DAEMON@x-desktop (Mail Delivery System)
Subject: Undelivered Mail Returned to Sender
To: x@x-desktop
Auto-Submitted: auto-replied
MIME-Version: 1.0
Content-Type: multipart/report; report-type=delivery-status;
        boundary="3CECB40093.1241013042/x-desktop"

This is a MIME-encapsulated message.

--3CECB40093.1241013042/x-desktop
Content-Description: Notification
Content-Type: text/plain; charset=us-ascii

This is the mail system at host x-desktop.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to postmaster.

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                   The mail system

<x@x-laptop>: x-laptop

--3CECB40093.1241013042/x-desktop
Content-Description: Delivery report
Content-Type: message/delivery-status

Reporting-MTA: dns; x-desktop
X-Postfix-Queue-ID: 3CECB40093
X-Postfix-Sender: rfc822; x@x-desktop
Arrival-Date: Wed, 29 Apr 2009 15:50:42 +0200 (CEST)

Final-Recipient: rfc822; x@x-laptop
Action: failed
Status: 5.0.0
Diagnostic-Code: X-Postfix; x-laptop

--3CECB40093.1241013042/x-desktop
Content-Description: Undelivered Message Headers
Content-Type: text/rfc822-headers

Received: by x-desktop (Postfix, from userid 1000)
        id 3CECB40093; Wed, 29 Apr 2009 15:50:42 +0200 (CEST)
To: x@x-laptop
Message-Id: <20090429135042.3CECB40093@x-desktop>
Date: Wed, 29 Apr 2009 15:50:42 +0200 (CEST)
From: x@x-desktop (xxxx)

--3CECB40093.1241013042/x-desktop--

And this is my /etc/postfix/main.cf

> # See /usr/share/postfix/main.cf.dist for a commented, more complete version


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

myhostname = x-desktop
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = x, x-desktop, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.0.0/16
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
default_transport = smtp
relay_transport = smtp
inet_protocols = all

What could be the mistake?

Thanks and greetings.

---

### Post by coutts99 on 2009-04-30
[http://en.wikipedia.org/wiki/MX_record]("http://en.wikipedia.org/wiki/MX_record")

---

