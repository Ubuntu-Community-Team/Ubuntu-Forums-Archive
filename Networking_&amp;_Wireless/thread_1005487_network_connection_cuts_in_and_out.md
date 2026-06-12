---
title: "network connection cuts in and out"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by Kymus on 2008-12-08
Recently, Ubuntu started something new to add to my list of problems (lucky me). From time to time the network will cut out and then it will come back anywhere from 5 to maybe 30 minutes later. I've noticed that this seems to happen only with web browsing, as bittorrent still works fine and it seems like I can still run updates during this period as well. When it cuts out, I get no warning or error message or anything and the same goes for when it comes back. I've tested the network with a laptop (running Vista) during these strange periods and it has run everything fine. So now, I am thoroughly confused (and very frustrated!).

I'm using the built-in network card on my motherboard, a *Foxconn NF4UK8AA*

---

### Post by Kymus on 2008-12-18
Well, since posting this issue, this problem has gotten better sometimes, and worse other times (right now it's pretty terrible). However, I've found (accidentally) that after closing my bittorrent program (KTorrent) the network will act completely normal again. Currently, when KTorrent is up, I can not access the web at all.. nothing will load.

---

### Post by The Cog on 2008-12-18
That sounds to me like ktorrent is flooding the link so that your other applications are losing too many packets and giving up. Try setting ktorrent (if possible) so that it limits both its upload and download speeds to around 2/3 of your actual link speeds.

---

### Post by Kymus on 2008-12-18
> **The Cog said:**
> That sounds to me like ktorrent is flooding the link so that your other applications are losing too many packets and giving up. Try setting ktorrent (if possible) so that it limits both its upload and download speeds to around 2/3 of your actual link speeds.

Thanks for the input!

I understand what you're saying for the most part, but I am unsure as to how I would "*set ktorrent so that it limits both its upload and download speeds to around 2/3 of your actual link speeds*".... can I get a clue? 

Actually, I think I understand.... check the speed of the connection and then set KTorrent's up/down limit speed to 2/3 of the total?

---

### Post by The Cog on 2008-12-18
That's the idea. But I've never used ktorrent so I don't know if you can set upload and download speed limits. And I don't know how you find out what your broadband link speeds are - for my broadband, my router has a web page that tells me what speed it's running at, typically 2M down and 600k up. Beware link speeds are often in bit/sec and other software often talks of speeds in bytes/sec. 1 byte/sec = 8 bit/sec.

---

### Post by AAllInFlynn on 2008-12-18
> **Kymus said:**
> Recently, Ubuntu started something new to add to my list of problems (lucky me). From time to time the network will cut out and then it will come back anywhere from 5 to maybe 30 minutes later. I've noticed that this seems to happen only with web browsing, as bittorrent still works fine and it seems like I can still run updates during this period as well. When it cuts out, I get no warning or error message or anything and the same goes for when it comes back. I've tested the network with a laptop (running Vista) during these strange periods and it has run everything fine. So now, I am thoroughly confused (and very frustrated!).

I'm using the built-in network card on my motherboard, a *Foxconn NF4UK8AA*

I have the same issue.  I have Intrepid installed on a ThinkPad T31 with a DLink DWA-652 pcmcia card installed.  While using Firefox and downloading a file the wlan0 just drops.  Then after about 60 seconds it comes back online. The process repeats over and over again.  This almost makes the PC unusable.  I am using the built in Atheros drivers but am going to switch over ndiswrapper versions tonight.  Hoping this helps.  And yes, this only happens when using my webbroswer and is most noticable when downloading files.  When I have been using the Transmission Torrent Client I do not notice the drop off.

---

### Post by AAllInFlynn on 2008-12-19
One of the easiest ways to tell if you have this issue (and granted this may not work for those with one PC) is to open a remote desktop session.  Mine used to drop every 30 seconds and I would have to reconnect.

After installing the ndiswrapper module and installing the correct wireless .inf and .sys file for the dlink dwa-652 adapter this issue went away for me.  So upon initial analysis the ath5008 drivers are not fully compatible with the dlink dwa-652 adapter just yet.

---

