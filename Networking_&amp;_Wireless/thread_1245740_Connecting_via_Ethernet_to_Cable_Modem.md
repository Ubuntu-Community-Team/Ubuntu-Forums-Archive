---
title: "Connecting via Ethernet to Cable Modem"
date: 2009-08-20
forum: Networking &amp; Wireless
---

### Post by Nolli on 2009-08-20
Just deleted Windows XP Pro from an IBM machine and have installed Ubuntu 9.04, which was successful. Now the ask is to connect to te Internet.  In the network manager, you have Auto Eth0 then to the right it says never.  Going through edit does not offer a removal.

The network tool in admin seems to suggest that the computer is connected to the modem. However acknowledge of this connection is not registered with the network manager.

What's going on? I just dislike when an easy-to-use software takes so much time and creating so much frustration!!!

I notice in other thread most people seem delete the Auto eth0 under wired. However no clear cut solution provided. Then there is Terminal and commands which seems to be a foreign matter.

Would someone please help? Thanks

---

### Post by pigwig on 2009-08-20
I am having the exact same issue---installed 9.04 on my Dell. Cant seem to get it to find the ethernet card...are your lights flashing on the card? Mine are not on at all.

I hope you get a response to your question--seems a lot of folks have similar issues...

regards,

---

### Post by Nolli on 2009-08-21
Just trying to get help by posting so it will be at the top.  It just seems that by default the Auto eth0 should allways be on, not never.  Almost all computer users get the computer to be on line.

Patiently await your help, thanks

---

### Post by Iowan on 2009-08-21
My laptop uses **Auto eth0** to connect to wired network after I disabled [rfc3442]("http://ubuntuforums.org/showthread.php?t=1156441"). The "never" refers to the last time the connection was used. From a terminal (which is the easiest way - once you get used to it) enter **ifconfig -a** to see if your interface got an IP address.  There are several other useful terminal commands - but we'll start slow.

---

### Post by Nolli on 2009-08-22
Well folks, we are online...problem solved.

Before getting into terminal with all those commands, I decided to call the cable internet service provider and have them reset the cable modem from their end. Once done, I simple select the Auto eth0 and wallah, I am online.

Thank you.

---

