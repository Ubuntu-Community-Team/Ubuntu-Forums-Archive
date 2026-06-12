---
title: "Connections refused at night"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by maxum on 2010-03-03
I have just installed Ubuntu 9.10 Server (64-bit) and configured it as a mail / web server. The problem is it refuses connections every night. 

Sometime between 7 and 8 pm it stops responding to network requests, I have tried ping, making an ssh connection with putty, and having outlook connect using a pop3. Then between 6 and 7 AM it starts accepting them again. During the day I can connect any time problem free.

If I go to the console and send a ping from the box it seems to wake it back up and it works again. Cron is configured to automatically send and email just after midnight and that seems to go out.

I configured the mail server using courier-new, postfix, phpmyadmin, and squirellmail. Apache is also running. 

There doesn’t seem to be anything in the syslog to indicate something stopped. It shows an Outlook account collecting mail every 2 minutes then it just stops, this account is left open allnight. The same thing when it starts again. 

Here is the syslog for just before it stops
2-Mar	17:26:01	ubuntu	pop3d: Connection, ip=[::ffff:10.20.2.5]
2-Mar	17:26:01	ubuntu	pop3d: LOGIN, user=joe@joe.com, ip=[::ffff:10.20.2.5], port=[3163]
2-Mar	17:26:01	ubuntu	pop3d: LOGOUT, user=joe@joe.com, ip=[::ffff:10.20.2.5], port=[3163], top=0, retr=0, rcvd=12, sent=39, time=0
2-Mar	17:28:03	ubuntu	pop3d: Connection, ip=[::ffff:10.20.2.5]
2-Mar	17:28:03	ubuntu	pop3d: LOGIN, user=joe@joe.com, ip=[::ffff:10.20.2.5], port=[3171]
2-Mar	17:28:04	ubuntu	pop3d: LOGOUT, user=joe@joe.com, ip=[::ffff:10.20.2.5], port=[3171], top=0, retr=0, rcvd=12, sent=39, time=1
2-Mar	17:39:01	ubuntu	CRON[2630]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
2-Mar	18:09:01	ubuntu	CRON[2641]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
2-Mar	18:17:01	ubuntu	CRON[2652]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

Here is it when Outlook stats again. 
Mar  3 06:38:13 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="761" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Mar  3 06:39:01 ubuntu CRON[3118]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Mar  3 06:56:46 ubuntu pop3d: Connection, ip=[::ffff:10.20.2.5]
Mar  3 06:56:46 ubuntu pop3d: LOGIN, user=joe@joe.com, ip=[::ffff:10.20.2.5], port=[1546]
Mar  3 06:56:46 ubuntu pop3d: LOGOUT, user=joe@joe.com, ip=[::ffff:10.20.2.5], port=[1546], top=0, retr=0, rcvd=12, sent=39, time=0
Mar  3 06:58:50 ubuntu pop3d: Connection, ip=[::ffff:10.20.2.5]
Mar  3 06:58:50 ubuntu pop3d: LOGIN, user=joe@joe.com, ip=[::ffff:10.20.2.5], port=[1561]
Mar  3 06:58:50 ubuntu pop3d: LOGOUT, user=joe@joe.com, ip=[::ffff:10.20.2.5], port=[1561], top=0, retr=0, rcvd=12, sent=39, time=0
Mar  3 07:00:53 ubuntu pop3d: Connection, ip=[::ffff:10.20.2.5]

There is nothing in the messages file either.If more information is need let me know.  I need to figure out why this is happening before I can make the server live.

---

### Post by Iowan on 2010-03-03
Does it quit responding to local (net) queries - or just from Internet?

---

### Post by maxum on 2010-03-03
The server is only accessible from our local network. There are no external connections allowed.

---

