---
title: "Application that will notify if wireless router assigns IP address"
date: 2009-06-28
forum: Networking &amp; Wireless
---

### Post by SilvaRizla on 2009-06-28
I currently have a Dlink DL624 router that due to the drivers for my wireless card I can't use any encryption protection as they are not yet supported. 

According to the logs I have had a few people connecting, and would like to know if there is a program that will alert me (with a noise or on screen message) as soon as someone joins my network

---

### Post by jhannah on 2009-06-28
I'm not aware of a very user-friendly application that will accomplish that goal but you could use ARPWatch. ARPWatch works by logging new ARP requests, changed MAC addresses which is a pretty effective way to keep track of who is sending any traffic on your network.

The configuration you get out of the box should do the trick, but you might need to specify that you want to listen on a particular interface or use the -m option to e-mail yourself reports. If you opt not to, you can check /var/log/syslog for messages like the below:

```

Jun 28 18:11:24 octave arpwatch: Running as uid=123 gid=138
Jun 28 18:11:24 octave arpwatch: listening on eth0
Jun 28 18:12:08 octave arpwatch: new station 10.x.x.x xx:xx:xx:xx:xx eth0

```

The new station alerts should tell you when there is someone that arpwatch hasn't yet seen connected that is sending traffic.

Hope that helps, sorry there isn't really a more elegant solution.

---

