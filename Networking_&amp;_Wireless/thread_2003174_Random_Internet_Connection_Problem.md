---
title: "Random Internet Connection Problem"
date: 2012-06-13
forum: Networking &amp; Wireless
---

### Post by Precipitous on 2012-06-13
Ever since upgrading to Ubuntu 12.04 anytime I reboot my computer I have to do a hard reset of my cable modem/computer reboot at least 8 - 10 times before I can connect to the Internet. Once connected everything is fine until I reboot again...  I just replaced the cable modem and I have removed my router, so I am sure it is not a hardware issue. I need to be able to reboot because I switch back and forth between using the regular Unity environment for day to day computer tasks, and the XFCE UbuntuStudio environment for music production. 

I have no idea as to where to  troubleshoot from here...

Any help anyone can give would be GREATLY appreciated!

---

### Post by biodojo on 2012-06-13
I have been troubleshooting wireless issues and some terminal commands that have helped me get information are: 

lspci (lists your wireless card at the end so you can see if there are other folks who have issues with the same hardware/drivers)

dmesg | grep wlan
dmesg | grep iee
tail -f  /var/sys/syslog

These commands tell you more about what your system is doing "under the hood" as it connects to wireless. So try those and post your wireless card and any info you can glean from those other commands.

---

### Post by fuzzyworbles on 2012-06-13
do you have some script or something running on boot that changes your ethernet mac address? supposing that the modem is good and the line is clean, that's only time the cable modem would need to be reset -- when a different mac address is introduced to the modem.

as an aside, you don't need to reboot your computer to switch between window managers. just log out and switch the window manager in lightdm. if you have them installed on separate partitions, just use the xbmc studio install and install the other window manager along with it. then you'll be able to switch between them without restarting.

---

### Post by Precipitous on 2012-06-13
@biodojo - I am not running a wireless card and took my router out of my setup too. All I am running is the cable modem connected directly to the network card  (Intel on-board). lspci command lists it as: Intel Corporation 82566DC Gigabit Network Connection (rev 02)

@fuzzyworbles - Thank you for your advise...  I do not have anything running that would change the MAC address, and have monitored it to verify that it is stable...  Unfortunately, I have to reboot when switching between desktop environments as that I run the low latency and realtime kernels for music production. I suppose I could just use the low latency one for everything if need be, then log out and back in when switching environments.  I didn't realize one could do that. Thanks again for letting me know...

---

### Post by Precipitous on 2012-06-19
This was resolved by wiping my hard drive and re-installing Ubuntu 12.04 from scratch...

---

