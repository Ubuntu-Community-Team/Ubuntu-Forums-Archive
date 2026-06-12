---
title: "Broadcom 4322"
date: 2013-09-03
forum: Networking &amp; Wireless
---

### Post by Nikolay_Andronov on 2013-09-03
Hi all,

I've got DELL Latitude E6400 with a Broadcom 4322 wifi adapter. Since I started using Ubuntu on this laptop, I have nothing but trouble with this adapter.
Moved into a new place, changed the ISP and noticed - my laptop can't use all the 50MBps my ISP provides me, although the wifi router is 1 meter away.
In the beggining I thought it is my ISP's fault, had few conversations with them, but nothing changed, then I used my gf's laptop for the speed test and guess what - 50Mbps. HP machine. 
So basically when I'm using the cable I have all the 50Mbps, but when I'm using the wireless, all I've got is 30Mbps max.
I have the latest drivers, but obviously they are not working properly.

Any ideas?

---

### Post by chili555 on 2013-09-03
Let's find out more details. Please open a terminal and run and post:```
lspci -nn -d 14e4:
lsmod | grep -e b43 -e wl -e brcm
```Thanks.

---

### Post by Nikolay_Andronov on 2013-09-03
Thanks for your quick reply.
Here's the info:

>  lspci -nn -d 14e4:
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)


> lsmod | grep -e b43 -e wl -e brcm
wl                   2906597  0 
cfg80211              178877  1 wl
lib80211               14040  2 lib80211_crypt_tkip,wl


---

### Post by chili555 on 2013-09-03
Unfortunately, you can Google up many different solutions for this device: the STA driver, b43 and firmware, black magic, voodoo, shop for a new card at Ebay, et al. Let's try a few things one at a time. Hopefully, we'll hit on one that fixes it.

Try resetting the router to B and G speeds only and not N. Disconnect the wireless at the Network Manager icon and reconnect. Is it improved? 

Let's turn off power management:```
sudo iwconfig eth1 power off
```

Try switching the driver:```
sudo apt-get install linux-firmware-nonfree
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -r wl
sudo modprobe b43
```Is it improved? ```
iwconfig
```It may take a reboot.

---

### Post by Nikolay_Andronov on 2013-09-04
So testing the router in b/g only resulted even lower speed - 3Mbps. It's now on "n" only and the speed is as it was before - 30Mbps.

Changing the driver failed, i don't know why, but "wl" driver was not found: > FATAL: Module wl not found.

There was no errors at all on the previous steps.

Now my wireless adapter changed from eth2 to wlan0 and I'm using the cable connection because the wifi isn't working.

EDIT: STA driver reinstalled, wifi working again, max speed: 30-32 Mbps.

---

### Post by chili555 on 2013-09-04
> It's now on **"n" only **and the speed is as it was before - 30Mbps.Is it improved or degraded if you select automatic B, G or N?

---

### Post by Nikolay_Andronov on 2013-09-04
Degraded. Combined b/g resulted 3Mbps (10 times less than b/g/n or n only).

---

### Post by chili555 on 2013-09-05
I regret that I have no further suggestions. Sorry.

---

