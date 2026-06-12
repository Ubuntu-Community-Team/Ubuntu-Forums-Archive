---
title: "Network GUI"
date: 2010-11-19
forum: Networking &amp; Wireless
---

### Post by craigbert on 2010-11-19
Hello All,
 
Both Network Manager Applet (0.8.1) and WiFi Radar seem to have problems connecting to any wireless network consistantly. Sometimes they do, sometimes they don't. Is there a better way to consistantly connect to a wireless network? GUI or non-GUI, I don't care. I just want consistant and stable.
 
Thanks,
 
Craigbert

---

### Post by pytheas22 on 2010-11-19
Have you checked to rule out problems with your wireless driver?  If the connection works fine sometimes but not other times, I'd suspect something is going wrong there--or that your computer is only just barely within range of your router or that there's interference from some other device.

If you want an alternative to NetworkManager and Wifi Radar, you can always connect from the command line.  The steps required range from quite simple if the network you want to connect to is unencrypted, to slightly more complicated if it uses WEP, to relatively complex if it uses WPA.  But there's a very good tutorial [here]("http://ubuntuforums.org/showthread.php?t=571188") that covers all the different likely scenarios.

---

