---
title: "Network disconnects every ~5 minutes"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by estebistec on 2009-07-09
For some reason today, my network is disconnecting or resetting every five minutes. I can see xchat disconnect/reconnect on this interval. dmesg and syslog, however, show nothing on this interval at all.

My connection is over eth0. I'm on a Dell Latitude 6500. Here is some more relevant info from lspci:

[FONT="Courier New"]
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection[/FONT]

---

### Post by slugmax on 2009-07-09
It doesn't have to be your network that is the issue, it could be the IRC server, or some point in-between you and the server. You could start a long-running ping out to the internet in a terminal window and just watch it, if you experience a dropout but don't see a gap in the ping sequence, it's likely not you. Something like 'ping yahoo.com' will work.

---

### Post by estebistec on 2009-07-09
> **slugmax said:**
> It doesn't have to be your network that is the issue, it could be the IRC server, or some point in-between you and the server. You could start a long-running ping out to the internet in a terminal window and just watch it, if you experience a dropout but don't see a gap in the ping sequence, it's likely not you. Something like 'ping yahoo.com' will work.

It's def. not just the IRC server. The others on my server aren't getting kicked off, and I lose access to pages in the browser at the same time.

But yes, I suspect it may have been routers or some other network component from the specific physical plug I would using. I just wanted to make sure I wasn't missing some common issue that would be indicated by my symptoms (the 5 minute intervals).

Thanks.

---

### Post by superprash2003 on 2009-07-09
take a look at [http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367)

---

### Post by estebistec on 2009-07-10
> **superprash2003 said:**
> take a look at [http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367)

Well, I wasn't using wifi. I've verified the problem was based on the port I was plugged into.

---

