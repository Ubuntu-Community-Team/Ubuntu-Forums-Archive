---
title: "No Wifi after update 8/01/2010 Ubuntu 9.10 32bit"
date: 2010-01-08
forum: Networking &amp; Wireless
---

### Post by ludionisio on 2010-01-08
Hello,

after the automatic update this morning and restart I could no longer connect to wifi. The router is visible, along with all the others, but when it tries to connect to it, it doesn't succeed.

This is what have been instaled:

Commit Log for Fri Jan  8 10:58:42 2010


Upgraded the following packages:
firefox (3.5.6+nobinonly-0ubuntu0.9.10.1) to 3.5.7+nobinonly-0ubuntu0.9.10.1
firefox-3.5 (3.5.6+nobinonly-0ubuntu0.9.10.1) to 3.5.7+nobinonly-0ubuntu0.9.10.1
firefox-3.5-branding (3.5.6+nobinonly-0ubuntu0.9.10.1) to 3.5.7+nobinonly-0ubuntu0.9.10.1
firefox-3.5-gnome-support (3.5.6+nobinonly-0ubuntu0.9.10.1) to 3.5.7+nobinonly-0ubuntu0.9.10.1
firefox-gnome-support (3.5.6+nobinonly-0ubuntu0.9.10.1) to 3.5.7+nobinonly-0ubuntu0.9.10.1
gimp (2.6.7-1ubuntu1) to 2.6.7-1ubuntu1.1
gimp-data (2.6.7-1ubuntu1) to 2.6.7-1ubuntu1.1
libgimp2.0 (2.6.7-1ubuntu1) to 2.6.7-1ubuntu1.1
linux-generic (2.6.31.16.29) to 2.6.31.17.30
linux-headers-generic (2.6.31.16.29) to 2.6.31.17.30
linux-image-generic (2.6.31.16.29) to 2.6.31.17.30
linux-libc-dev (2.6.31-16.53) to 2.6.31-17.54
xulrunner-1.9.1 (1.9.1.6+nobinonly-0ubuntu0.9.10.1) to 1.9.1.7+nobinonly-0ubuntu0.9.10.1
xulrunner-1.9.1-gnome-support (1.9.1.6+nobinonly-0ubuntu0.9.10.1) to 1.9.1.7+nobinonly-0ubuntu0.9.10.1

Installed the following packages:
linux-headers-2.6.31-17 (2.6.31-17.54)
linux-headers-2.6.31-17-generic (2.6.31-17.54)
linux-image-2.6.31-17-generic (2.6.31-17.54)

I believe this update was the cause, but no idea what could be...

Thanks

---

### Post by tripolitan on 2010-01-08
This is an update that requires restarting. Have you had to build the driver for your wifi hardware using ndiswrapper or did it get detected automatically? I'm asking because sometimes certain wifi or video drivers may get broken after a kernel upgrade.

errr...(deleted assumption)

---

### Post by glenarvan on 2010-01-09
Hi,

I am having the same problem on a x64 box - after update I can see the wifi-network (PKI-secured), but can not access it (password is set correctly, though).

syslog is saying this:
[COLOR=DimGray]Jan  9 09:06:52 x-pc NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Jan  9 09:06:52 x-pc NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jan  9 09:06:52 x-pc  NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Jan  9 09:06:52 x-pc  NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jan  9 09:06:53 x-pc  NetworkManager: <info>  (wlan0): device state change: 6 -> 9 (reason 7)
Jan  9 09:06:53 x-pc  NetworkManager: <info>  Activation (wlan0) failed for access point (WIFI-X)
Jan  9 09:06:53 x-pc  NetworkManager: <info>  Marking connection 'WIFI-X' invalid.
Jan  9 09:06:53 x-pc NetworkManager: <info>  Activation (wlan0) failed.
Jan  9 09:06:53 x-pc  NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Jan  9 09:06:53 x-pc  NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
[/COLOR] 
Any ideas?

Rgrds,
glenarvan

---

### Post by tripolitan on 2010-01-11
What happens if you boot your old linux-image-2.6.31.16.29 or whatever you had before the upgrade? re-install the linux-generic-2.6.31.16.29, if all works, lock this version in Synaptic and use it until a fix is found.

---

### Post by ludionisio on 2010-01-13
Even though I haven't figured out why it happened I managed to solve it. I just deleted the saved configuration for my wifi and then created a new one, now it is working again.

Thanks for the support

---

### Post by bozzy on 2010-01-13
This latest update is dog faeces - my previously reliable Atheros wifi connection is blown into the weeds. If I revert to previous, VOILA! we have wifi again. And yes I have done all the reboot, confirmation of no fancy modprobe fixes etc. My head hurts.

The repeated problems with networking and particularly Wifi, but also with Audio and Skype especially, let the side down. This is SO ABSOLUTELY fundamental that you could not blame any newbies for heading straight back to Mr. Softy. Just my disillusionment. I do not expect my connectivity to be broken by updates. Ever! Period. Point final.

Release manager should be "retrained" or invited to dig the latrines as he/she clearly is wasting their talents in software maintenance.

---

### Post by LieToPurify3 on 2010-01-25
oops

---

### Post by Mercedes99 on 2010-02-20
It looks as though the latest upgrade to the kernel (20) has broken the wifi again.  I have rebooted back into version 19 and it is working, but it cannot find any wireless network if I boot using the latest version.

It looks like whatever fixed it last time has been "unfixed" again.

---

### Post by efflandt on 2010-02-20
If people have a problem with hardware, it would help to list at least the output of **lspci** or **lsusb** related to it (if not **sudo lspci -v** or **sudo lsusb -v**).  Otherwise people may be guessing about unrelated hardware.

When I had 64-bit Ubuntu 9.10 on an external USB drive with Broadcom STA enabled for a BCM4311, wireless automatically worked when that drive was booted on a newer Dell with BCM4312.

But when I set up same OS on another USB drive from the laptop with BCM4312, I am pretty sure that still worked when it updated to .17 kernel, but when later booted on the older Dell with BCM4311 no wireless interface or 2nd eth showed up at all (no wireless extensions), even after sudo modprobe wl (although, wl and related module were loaded).  Wireless still did not work after updating to kernel .19 using USB mobile data dongle.  So I deactivated Broadcom STA, rebooted, wireless did not work with wlan, activated Broadcom STA, rebooted, and then wireless worked automatically again.  But I was fortunate to have another network connection (mobile data), because without an install CD to reactivate Broadcom STA, I would have been stuck (at a motel) with no connection (other than WinXP).

---

### Post by Mercedes99 on 2010-02-20
Output of lspci as follows:
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:05.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)

---

### Post by northd_tech on 2010-02-20
> **Mercedes99 said:**
> Output of lspci as follows:
06:05.0 Ethernet controller: **Atheros** Communications Inc. **AR2413** [COLOR=Blue]802.11bg[/COLOR] NIC (rev 01)
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

That's an Atheros AR2413 wireless adapter- and your cabled ethernet is the Realtek 8139 stuff.  I haven't ever worked with the Atheros AR2413 WiFi, but these are the 3 most recent threads here that I found in a search:

[http://ubuntuforums.org/showthread.php?t=1305812&highlight=atheros+2413](http://ubuntuforums.org/showthread.php?t=1305812&highlight=atheros+2413)

[http://ubuntuforums.org/showthread.php?t=1345078&highlight=atheros+2413](http://ubuntuforums.org/showthread.php?t=1345078&highlight=atheros+2413)

[http://ubuntuforums.org/showthread.php?t=1120259&page=2&highlight=atheros+2413](http://ubuntuforums.org/showthread.php?t=1120259&page=2&highlight=atheros+2413)

---

