---
title: "configure postfix as localhost smtp server and send email? problems..."
date: 2010-05-25
forum: Networking &amp; Wireless
---

### Post by pythonscript on 2010-05-25
I'm trying to set up a basic smtp server on my local computer that I can send basic, unencrypted email through on port 25. I installed postfix, and I chose the following options:

Internet Site, 
System Mail Name:  localhost
Root and postmaster mail recipient:  *I left this blank*
For other domains to accept mail, I entered :  NONE, localhost
No force synchronous mail updates
Local networks:  127.0.0.0/8
No mailbox size limit
Local address extension character:  +
Use all internet protocols


Now I'm trying to send an email to myself, from my gmail address, so here's what I typed in the terminal with its output
```

**telnet localhost 25**
Trying ::1...
Connected to localhost.
Escape character is '^]'.
220 MY_COMPUTER_NAME ESMTP Postfix (Ubuntu)
**helo localhost**
250 MY_COMPUTER_NAME
**mail from: *address*@gmail.com**
250 2.1.0 Ok
**rcpt to: *address*@gmail.com**
554 5.7.1 <*address*@gmail.com>: Relay access denied

```My commands are in bold. Sorry about the long post, but what am I doing wrong? Are there any config files I need to post, or what? I *really *want to have this smtp server working.... Thank you!

---

### Post by pythonscript on 2010-05-25
After doing a bit more research, I guess I'm trying to set up an "open relay" for just my local machine? Is this possible? My apologies for my complete ignorance of computer networking; I'm starting to realise just how much is out there! Thanks!

---

### Post by pythonscript on 2010-05-30
Moved to this thread:

[http://ubuntuforums.org/showthread.php?t=1494072](http://ubuntuforums.org/showthread.php?t=1494072)

---

