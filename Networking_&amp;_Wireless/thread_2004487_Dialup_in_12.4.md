---
title: "Dialup in 12.4"
date: 2012-06-15
forum: Networking &amp; Wireless
---

### Post by Ziton on 2012-06-15
Hi 
Been awhile since I posted. I've installed Ubuntu 12.04. I have to use dialup for a while. I have a usr external serial modem.
I don't know where to start. Will I need to download some things to get it working?
I have a windows box working. What will I need to get it online?
Thanks
[INDENT][/INDENT]

---

### Post by Ziton on 2012-06-16
Is this the right forum for dialiup questions?
I cannot get Gnome-ppp to work on 12.04 I was able to get pppconfig working to some degree. I can hear it dialing on the usr serial modem. I can hear it trying to connect then it cuts off. When I run plog to see what went wrong I get.
Script /usr/sbin/chat -v -f /etc/chatscripts/provider finnished (pid 5695), status = 0x5
connect script failed
exit.
 I changed from chat to pap. I hear it dial and shake hands and again quite.
Checked plog and got almost the same thing.
Script /usr/sbin/chat -v -f /etc/chatscripts/provider finnished (pid 6311), status = 0x3
connect script failed
exit
what do I do now?

---

### Post by mbuell on 2012-06-26
I am having to set up a newly installed 12.04 system to use dialup also. I do not have an answer for you - other then to say there may be a problem with either the modem init string - or the ppp config. 

I would suggest you google "ubuntu howto dialup wiki" for the Ubuntu Wiki page for Dialupmodem How-to. There is some stuff there about the ppp configurations. 

I got both ppp and wvdial to go so far as dialing a number so far. I haven't tried to actually connect to anything. My Gnome PPP package is screwed up for some reason - which isn't relative to your question, but explains why I'm not using gppp at the moment. 

Good luck.

---

