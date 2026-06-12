---
title: "Wireless Disabled Following Reboot"
date: 2010-09-05
forum: Networking &amp; Wireless
---

### Post by overzellous on 2010-09-05
I'm running Ubuntu 10.04 64-bit on an Acer 7551 laptop. Every time I reboot my laptop, my Atheros 9k wireless is disabled. It's a very simple process to enable it each time (and then it works perfectly), but a process I would like to avoid having to do every reboot. I'm not all that interested in WHY this is happening, just want to know how to fix it - either by changing some config or by simply writing a script to enable wireless on startup. Since I'm fairly new to linux/ubuntu, I'm not really sure how to proceed. 

A couple of notes - 
 - when I run "rfkill list" the wireless says it is "soft blocked".
 - "lshw -C network" shows network -DISABLED for the wireless.

Let me know if you need any further info. Thanks in advance for your assistance.

-Mark

---

### Post by wilee-nilee on 2010-09-05
Right click on the NM applet and then edit connections. make sure your wireless is set to auto connect and if it doesn't matter, available for all users=on your computer.

---

### Post by perspectoff on 2010-09-05
That happens to me all the time with Network Manager.

Although Network Manager has improved with every release, I still find it buggy.

I have always ended up removing it and replacing it with Wicd, which has always been rock stable for me on every computer with wireless.

 sudo apt-get remove network-manager network-manager-gnome
 sudo reboot
 sudo apt-get autoremove

 sudo apt-get install wicd
 sudo reboot

Be happy!

---

