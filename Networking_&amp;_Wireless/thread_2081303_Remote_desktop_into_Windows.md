---
title: "Remote desktop into Windows"
date: 2012-11-06
forum: Networking &amp; Wireless
---

### Post by Reddoug on 2012-11-06
Hi All

 I am trying to setup remote desktop into a Win 2000 computer. I have my VPN set and I can telnet into a access server, but there is a computer in the lab that has ASDM on it to setup an ASA 5510  firewall. I can do this with my Windows computer but I am trying to do it with my Ubuntu comp also and not have any luck. I have the okay from my instructor to do this with Ubuntu. I have tried the remote desktop come with Ubuntu. Does Ubuntu use a different port than what Windows uses?

Thanks, Doug

---

### Post by The Cog on 2012-11-06
I kmnow of 3 different remote desktop clients that come with Ubuntu. I used to use vinagre but that's broken in 12.10 so I've started using remmina. There is also a plain rdesktop (command line launched) and its GUI grdesktop that I don't think I've tried.

It would not make sense for these to use different ports, as being clients they have to connect to whatever port the windows server is listening on.

What problem are you having?

---

### Post by ahallubuntu on 2012-11-06
Windows Remote Desktop uses an entirely different protocol than the VNC protocol used by Ubuntu.


In Ubuntu, you need to install a Remote Desktop Client like Remmina.  This will give you access to a Windows Remote Desktop like the one in Windows 2000.

---

### Post by Reddoug on 2012-11-06
Thanks for the reply's. I will give them a try.

Doug

---

### Post by Reddoug on 2012-11-08
Thanks for the info. I installed Remmina and got it work.

Thanks again, Doug

---

### Post by dannyboy79 on 2012-11-08
edit the thread and mark it solved

---

