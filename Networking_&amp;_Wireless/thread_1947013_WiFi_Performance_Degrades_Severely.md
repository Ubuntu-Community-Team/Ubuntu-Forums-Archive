---
title: "WiFi Performance Degrades Severely"
date: 2012-03-25
forum: Networking &amp; Wireless
---

### Post by hantechbl on 2012-03-25
Hello,

I recently Installed Wubi on my Satelite A665, with 11.10, so far I've been pleased, however I seem to have some issues with WiFi, I can't download anything with it, whereas with Windows 7 I never had this issue, for example I was downloading Chromium, and it would stop at various points, 8MB, 19MB, 17MB, etc. and I wouldn't be able to use the internet anymore until I disconnected and reconnected.  The authentication type is WPA, the router is a Linksys WRT-150N running DD-WRT.  I'm using a 1st generation i3 370M based system with Intel's Wi-Max ready wireless chipset.  Is there a way to fix this?  The current driver is iwlagn.

---

### Post by wildmanne39 on 2012-03-26
Hi, give this a try if it helps we will need to make it permanent and do not reboot after running the commands.
```
sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1
sudo ifconfig wlan0 up

```
Thanks

---

### Post by hantechbl on 2012-03-26
Worked perfectly, how do I make it permanent?

---

### Post by wildmanne39 on 2012-03-26
Hi, this will make it permanent:
```
gksudo gedit /etc/modprobe.d/iwlagn.conf
```
and adding the line:
```
options iwlagn 11n_disable=1
```
Proofread carefully, save and close gedit. Reboot.

Please use thread tools at the top of the page to mark the thread solved.
Thanks

---

