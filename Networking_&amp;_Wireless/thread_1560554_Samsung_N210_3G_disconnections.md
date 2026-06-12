---
title: "Samsung N210 3G disconnections"
date: 2010-08-25
forum: Networking &amp; Wireless
---

### Post by pzico on 2010-08-25
I have Samsung N210 with 3G connection. Connection strenght is reported maximum, which is probably true based on my location. However, after some time 30s - couple of minutes the connection either disappears or gets closed (Connection strenght bar remains at the max). Typical example might be that I start opening [www.google.com](www.google.com) on the browser and it keeps loading and loading. Maybe after some minutes the page will load or the connection is reported disconnected. While connection is still reported to be on and google is still loading, I'm able to ping 3G gateway.

All tips and hints are highly appreciated!

---

### Post by pzico on 2010-08-27
Should I try installing ndiswrapper? It's currently not installed.

---

### Post by dineshs on 2010-08-27
I do not know whether this is related
[http://ubuntuforums.org/showthread.php?t=1549395](http://ubuntuforums.org/showthread.php?t=1549395)
Can you ping 4.2.2.1 when you have problems

---

### Post by pzico on 2010-08-30
> **dineshs said:**
> I do not know whether this is related
[http://ubuntuforums.org/showthread.php?t=1549395](http://ubuntuforums.org/showthread.php?t=1549395)
Can you ping 4.2.2.1 when you have problems

Thanks for the link! Now my connection doesn't keep dropping all the time anymore. Only problem remaining is the slowness of the connection, for example typical loading time of ubuntu forums mainpage is about 30s. My connection is 1MB/s.

---

### Post by dineshs on 2010-08-30
Hope you have configured your connection via Network Manager (mobile broadband tab)If yes try this
Right-click on the NM icon and then click on Edit Connections. 
Select the tab,Mobile broadband-select your connection-edit-ipv4
select method=Automatic PPP addresses only
give DNS as 4.2.2.1 and apply
Any progress?

---

