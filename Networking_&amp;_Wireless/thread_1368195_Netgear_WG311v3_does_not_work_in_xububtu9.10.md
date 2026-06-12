---
title: "Netgear WG311v3 does not work in xububtu9.10"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by andreas122 on 2009-12-30
hello...I have Xubuntu 9.10 and the my netgear wg311v3 card... it seams that doesn't work... I can't find enable wireless networks...it seam that xubuntu can't understand the netgear card
My Internet card works on Windows if I install the drivers but i don't find any drivers for Xubuntu!
What I can do ...to work my internet card???

---

### Post by bkratz on 2009-12-30
See if there is any help here

[http://ubuntuforums.org/showthread.php?t=1136959&highlight=WG311v3](http://ubuntuforums.org/showthread.php?t=1136959&highlight=WG311v3)

---

### Post by hexadecibel on 2010-02-10
I had just got this working in 9.10 by following this: [https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

Well, I screwed up my install and had to reinstall. When I tried getting the card working again I did everything as I had done the time before except this time I got this error when trying to start the device:
..........................
:~$ sudo modprobe ndiswrapper

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
...........................

I was stuck there for a long time. What the Internets told me was the message was irrelevant, some minor bug or what not... yet iwconfig wouldn't post my wireless card. Seemed like it just wasn't starting the device. What got it working for me this time was skipping to the end and editing: 
sudo gedit /etc/modules

and simply inputting "ndiswrapper" (no quotes) to the end of the file. Rebooted and viola!

Hope that helps you...

---

