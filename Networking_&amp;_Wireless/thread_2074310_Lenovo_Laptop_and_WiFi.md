---
title: "Lenovo Laptop and WiFi"
date: 2012-10-21
forum: Networking &amp; Wireless
---

### Post by yizrahomme on 2012-10-21
Hi there,
I just installed Ubuntu onto a friend's laptop - a Lenovo 3000-G400.  The WiFi interface wasn't coming up, so I googled a bit and came up with a driver called 'b43'.  

Downloaded the driver, did a quick change into the directory and ran sudo rmmod -f b43 and then sudo modprobe b43.  Or the other way around - can't recall.  :)

Anyway, the WiFi interface came online as if by magic, and all was right with the world.  Until the laptop was rebooted.  I redid the above, and it worked again, but could someone enlighten me as to how to get this driver loaded at each boot?

Many thanks.

---

### Post by chili555 on 2012-10-21
Please open a terminal and do:```
sudo su
echo b43 >> /etc/modules
exit
```Is it working now?

---

### Post by offgridguy on 2012-10-21
Just a thought here, did you disconnect before you shutdown??

---

### Post by yizrahomme on 2012-10-22
> **chili555 said:**
> Please open a terminal and do:```
sudo su
echo b43 >> /etc/modules
exit
```Is it working now?

Thank you for the response.

No, it didn't work.  It still hoses that module every time he reboots.  :(

---

### Post by yizrahomme on 2012-10-22
> **offgridguy said:**
> Just a thought here, did you disconnect before you shutdown??

Disconnect?  You mean logout?  No, he just hits the little gear wheel in the top right and 'shutdown'.

---

### Post by chili555 on 2012-10-22
>  It still hoses that module every time he reboots. I don't understand this. Can you please be more specific?

---

### Post by yizrahomme on 2012-10-22
> **chili555 said:**
> I don't understand this. Can you please be more specific?

Sorry.  What I mean is that I can get WiFi working using the modprobe method which I cited earlier on.  But that even after putting the line b43 into /etc/modules, a reboot still sees the machine coming up without WiFi connectivity.

---

### Post by chili555 on 2012-10-22
> **yizrahomme said:**
> Sorry.  What I mean is that I can get WiFi working using the modprobe method which I cited earlier on.  But that even after putting the line b43 into /etc/modules, a reboot still sees the machine coming up without WiFi connectivity.Let's dig deeper:```
lsmod | grep -e b43 -e ndis -e wl
ls /etc/modprobe.d
cat /etc/modprobe.d/blacklist.conf | tail -n5
dmesg | grep b43
```Thanks.

---

### Post by yizrahomme on 2012-10-23
> **chili555 said:**
> Let's dig deeper:```
lsmod | grep -e b43 -e ndis -e wl
ls /etc/modprobe.d
cat /etc/modprobe.d/blacklist.conf | tail -n5
dmesg | grep b43
```Thanks.

lsmod | grep -e b43 -e ndis -e w1
b43                   342643  0 
mac80211              436455  1 b43
cfg80211              178679  2 b43,mac80211
bcma                   25651  1 b43
ssb                    50691  1 

ls /etc/modprobe.d
alsa-base.conf          blacklist-firewire.conf     blacklist-rare-network.conf
blacklist-ath_pci.conf  blacklist-framebuffer.conf  blacklist-watchdog.conf
blacklist-bcm43.conf    blacklist-modem.conf        dkms.conf
blacklist.conf          blacklist-oss.conf          vmwgfx-fbdev.conf


cat /etc/modprobe.d/blacklist.conf | tail -n5
# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


dmesg | grep b43
[  663.375809] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[  663.672330] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[  663.844624] Registered led device: b43-phy0::tx
[  663.844690] Registered led device: b43-phy0::rx
[  663.844759] Registered led device: b43-phy0::radio
[  664.072153] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[14316.349193] b43-pci-bridge 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[14316.349224] b43-pci-bridge 0000:03:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xd4100000)
[14316.349233] b43-pci-bridge 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[14316.349243] b43-pci-bridge 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[14322.640089] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)

---

### Post by chili555 on 2012-10-23
Everything looks pretty normal except two things. May I see:```
cat /etc/modprobe.d/blacklist-bcm43.conf 
cat /etc/modprobe.d/dkms.conf
```I hope b43 and/or some of its dependencies are not simultaneously blacklisted *AND* declared in /etc/modules.

I am also a bit mystified as to why b43 doesn't appear until so late in the boot process:> [ [COLOR="Red"]663[/COLOR].375809] b43-pci-bridge 0000:03:00.0: setting latency timer to 64The plot thickens!

---

### Post by yizrahomme on 2012-10-23
> **chili555 said:**
> Everything looks pretty normal except two things. May I see:```
cat /etc/modprobe.d/blacklist-bcm43.conf 
cat /etc/modprobe.d/dkms.conf
```I hope b43 and/or some of its dependencies are not simultaneously blacklisted *AND* declared in /etc/modules.

I am also a bit mystified as to why b43 doesn't appear until so late in the boot process:The plot thickens!

Arrgh, my apologies... b43 was *not* in /etc/modules ! 

It is now, and it works.  Thank you *very* much and again, sorry for being dense!

---

### Post by chili555 on 2012-10-23
> **yizrahomme said:**
>  it works.  Thank you *very* muchGlad it's working by whatever means. I was glad to help. Have fun!!

---

