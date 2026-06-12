---
title: "postfix using exclusively a smarthost with smtp-auth"
date: 2005-01-06
forum: Networking &amp; Wireless
---

### Post by fhd on 2005-01-06
well don't worry about that "with smtp-auth" in the topic, I deactivated it in my sendmails access.db exclusively for my workstation, for the sake of successfull mail delivery.

So I'll worry about smtp-auth later on.


This is the situation:
I have sendmail running perfectly on my mailserver, and now I want postfix to deliver all mail (except local (not leaving localhost)) using my sendmail mailserver as smarthost.
I just read about using smarthosts, I actually never did it before.


Nevermind. I tried to reach my goal with the following mail.cf:

```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version

# For better performance, chattr -S -R /var/spool/postfix, and use a
# journaled filesystem to achieve the same results as chattr +S gives.

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# Uncomment the next line to use procmail for delivery
#mailbox_command = procmail -a "$EXTENSION"

myhostname = zion.zaiyon.ath.cx
mydomain = zaiyon.ath.cx
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = $mydomain
#myorigin = /etc/mailname
#mydestination = smtp.zaiyon.ath.cx
#mynetworks = 192.168.0.0/24
relayhost = smtp.zaiyon.ath.cx
mailbox_command =
mailbox_size_limit = 0
recipient_delimiter = +

#smtp_sasl_auth_enable = yes
#smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
#smtp_sasl_security_options =
#smtp_use_tls = yes

home_mailbox = .maildir/

```

Looks a bit confusing, but I tried around, adding and removing thousands of hashs  and probably something of this shouldn't be commented out. That's out of my exact knowlegde.

In my /etc/mail/access on the server, I added the line:
```
192.168.0.2   RELAY
```
and performed the other necessary steps for sendmail to read the new access list.

So that means that 192.168.0.2 (my workstation) should be able to use my mailserver as relay without any problems.

Sending inter-domain-e-Mails is not quite satisfieing:
I send an e-Mail to [email]fhd@zaiyon.ath.cx[/email] (who is me on the server), on the workstation, I'm also fhd, so it just look equal, but it isn't, here is the full header:

```
Return-Path: fhd@zaiyon.ath.cx
Received: from zion.zaiyon.ath.cx (zion.zaiyon.ath.cx [192.168.0.2])
        by paron-02.zaiyon.ath.cx (8.12.11/8.12.11) with ESMTP id j06GafKY026089        for <fhd@zaiyon.ath.cx>; Thu, 6 Jan 2005 17:36:42 +0100
Received: by zion.zaiyon.ath.cx (Postfix, from userid 1000)
        id 9BA2A1B326; Thu,  6 Jan 2005 17:36:21 +0100 (CET)
Date: Thu, 6 Jan 2005 17:36:21 +0100
To: fhd@zaiyon.ath.cx
Subject: Testmail
Message-ID: <20050106163621.GA26988@localhost.localdomain>
Mime-Version: 1.0
Content-Type: text/plain; charset=us-ascii
Content-Disposition: inline
User-Agent: Mutt/1.5.6+20040907i
From: fhd@zaiyon.ath.cx

```

So this message was sent through zion.zaiyon.ath.cx (that's my workstations hostname)

What I now think: This message was sent through and delivered by postfix itself, not by the smarthost smtp.zaiyon.ath.cx (my server has a bunch of names, but I have only one)


The Mail at least arrives.
Now, trying to send a Message outside, I get the following text as part of an e-Mail from Postfix' MAILER-DAEMON:

> 
[-- Attachment #2: Delivery report --]
[-- Type: message/delivery-status, Encoding: 7bit, Size: 0.4K --]

Reporting-MTA: dns; zion.zaiyon.ath.cx
X-Postfix-Queue-ID: F23371B2DC
X-Postfix-Sender: rfc822; [email]fhd@zaiyon.ath.cx[/email]
Arrival-Date: Thu,  6 Jan 2005 16:47:14 +0100 (CET)

Final-Recipient: rfc822; [email]fdahlke@arcor.de[/email]
Action: failed
Status: 5.0.0
Diagnostic-Code: X-Postfix; host smtp.zaiyon.ath.cx[192.168.0.4] said: 550
    5.7.1 <fdahlke@arcor.de>... Relaying denied (in reply to RCPT TO
    command)


And now I'm stuck.
I'm neither a sendmail, nor a postfix guru, but I still want to make it work and understand what's happening here.

tia.

---

