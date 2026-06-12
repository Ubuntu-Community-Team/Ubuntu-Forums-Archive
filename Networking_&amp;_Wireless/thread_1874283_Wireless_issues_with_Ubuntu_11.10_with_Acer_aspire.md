---
title: "Wireless issues with Ubuntu 11.10 with Acer aspire"
date: 2011-11-02
forum: Networking &amp; Wireless
---

### Post by siddi on 2011-11-02
Hi guys,

I recently upgraded to 11.10. I gather from other posts that there are some issues with the wifi connection in this version.

I am experiencing frequent and regular disconnections with my wifi.

Please let me know if there is any solution

regards

sid

---

### Post by lemming465 on 2011-11-04
You don't mention what model of Aspire you are having the problem on.  I had a similar issue on an Acer Aspire One 722.  My issue seems to be related to some sort of conflict between the ethernet chip and the wifi chip drivers.  Blacklisting the ethernet driver was a workaround for me.  On my system this looked something like:```
sudo -i
mount -o remount,rw /
mount -a
echo blacklist atl1c | tee -a /etc/modprobe.d/no-ether.conf
update-initramfs -u
reboot
```
Since it wouldn't stay up long enough to carry this our on a normal boot without freezing, I did this from a recovery boot to a root shell.

---

### Post by siddi on 2011-11-05
for the third command it returned no ether .conf- no such file or directory

Mine is acer aspire 5571 awxmi. 


please advice!!!

---

### Post by hantucovic on 2011-11-05
is this work with ubuntu 11.04... i have some trouble too, wireless was established but i can`t browsing anything,,, and indicator still yellow not blue... thanks a lot

---

### Post by agillator on 2011-11-05
I have an Aspire 5535-5050 that had a similar problem a year or more ago. On boot everything was fine, but within about five minutes the wireless would lose lock and not lock back on. Now, however, it works fine. I never knew for certain what the problem was. You might try updating the drivers with the newest from the controller manufacturer (probably Atheros in the Aspire). Try using Windows drivers with ndiswrapper. My eventual solution was to buy a Belkin USB wireless controller and disable the built in one until the built in one mysteriously started to work after an upgrade. I suspect that indicates drivers were updated for mine.

---

### Post by siddi on 2011-11-05
even the update manager doesn't work for me cos the wifi keeps dropping.

---

### Post by agillator on 2011-11-05
Now that you mention it, I remember that was a 'minor' problem for me, too. It is curious that this only happened after an upgrade - perhaps you should reinstall an older version of ubuntu (I assume you still have an installation cd) and play with it there, or use the driver from that version with the new version and see what that does? The only other solution I can suggest is to go the route I did and get a USB wireless adapter. I see Amazon has a number of them for less than $20. No guarantee, but it worked for me for almost a year.

---

### Post by agillator on 2011-11-05
You might try looking at this thread if you missed it, see if it gives you any ideas. 
[http://ubuntuforums.org/showthread.php?t=1868052](http://ubuntuforums.org/showthread.php?t=1868052)

---

### Post by lemming465 on 2011-11-07
If you can't keep the wifi up, can you temporarily plug the ethernet into something directly?

On my aspire one 722 what worked best for me was doing the initial install from a USB stick burned with a copy of the alternate install image (text-mode debian installer, not GUI ubiquity), and then running *apt-get upgrade; apt-get update* over ethernet, followed by blacklist the ethernet chip.

---

### Post by siddi on 2011-11-21
hey,
My wifi still keeps dropping every few seconds.... Does anyone have a solution?

---

