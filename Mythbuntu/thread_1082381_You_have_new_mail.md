---
title: "You have new mail"
date: 2009-02-27
forum: Mythbuntu
---

### Post by uncle hammy on 2009-02-27
This morning I logged into my backend via putty, and noticed a message at the very end f the login output..."You have new mail". 

I installed mailx, and typed "mail" to see the messages, and I have 6 messages that started being delivered Jan18 and every 7 days there after.  The message is.....
> Message 1:
From root@myth-backend Sun Jan 18 06:40:18 2009
Envelope-to: root@myth-backend
Delivery-date: Sun, 18 Jan 2009 06:40:18 -0500
From: root@myth-backend (Cron Daemon)
To: root@myth-backend
Subject: Cron <root@myth-backend> test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
Content-Type: text/plain; charset=ANSI_X3.4-1968
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin>
X-Cron-Env: <HOME=/root>
X-Cron-Env: <LOGNAME=root>
Date: Sun, 18 Jan 2009 06:40:18 -0500

/etc/cron.daily/logrotate:
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

They appear to be being done by something to do with cron, but I can't for the life of me think of any changes that I have done that would start this behavior.  I can't seem to figure out what is generating these messages.  I also can't seem to delete them.  If I go "mail" I do "delete" which I understand should delete message 1.  The command takes, but it does not take.

Any suggestions?

Thanks,
Scott

---

### Post by uncle hammy on 2009-02-27
I noticed I get the same "cannot resolve" message if I tried to restart apache2.

I added the following to /etc/apache2/httpd.conf (which was completely empty)

ServerName = machine_name

and the error went away while restarting apache, which I assume will also fix the error that the email is reporting, and presumably stop the emails.

However, I don't know why that error suddenly started being generated.

---

### Post by ian dobson on 2009-02-28
Hi,

If looks as if logrotate is being called by cron and if a cron job produces any output cron sends the outut as email to root.

To stop the job producing any output just redirect the output to to null with :-

nano /etc/cron.daily/logrotate

then change the line /usr/sbin/logrotate /etc/logrotate.conf to read 
/usr/sbin/logrotate /etc/logrotate.conf > /dev/null

Regards
Ian Dobson

---

### Post by uncle hammy on 2009-03-01
Hey, thanks for that!  It appears getting the servername into my apache2 httpd.conf file has supressed the output (because no error was prodduced).

However, the explanation you gave gives me a bit more understanding into the magical world of Linux :).

What exactly does the > dev/null mean?

---

### Post by ian dobson on 2009-03-02
Hi,

> /dev/null means direct all "normal" output to the device null (ie just loose it). All errors still go to stderr which cron should catch.

Regards
Ian Dobson

---

