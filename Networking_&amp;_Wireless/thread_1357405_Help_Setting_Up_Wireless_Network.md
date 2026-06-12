---
title: "Help Setting Up Wireless Network"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by wah fun on 2009-12-17
I hope someone can help. I am just about at my wits end. I have tried just about every suggestion I can find and no joy. Anyway, hope someone can help.

Things tried so far:
Installed fresh ubuntu 9.04 without wireless network adapter plugged in.
Modprobe (as su) for rt2800usb didn't do anything.
I dl'd the linux driver (v2.2.0.0) extracted drivers and ran make and make install - no change.
I edited the config.mk file for wpa supplicant and native wpasupplicant to y.
Edited os/linux/usb_main_dev.c and added device id (from lsusb output)
lssub output shows Belkin USB.

Also, tried using ndiswrapper but got an error saying ndiswrapper interface not found. (I have verified that ndiswrapper is installed.)

My eth0 card works fine it is just the wireless that I am having trouble with. Nothing I do seems to recognize the Network Adapter. Router shows wired but not wireless connection. All works fine in Windows XP.

My box:
CPU running at 2 GHz, 3 GiB ram
Dual boot with Windows XP Pro
Belkin N150 Enhanced Wireless USB Network Adapter
Belkin N150 Enhanced Wireless Router

Anyway, that's the story. Thx in advance for your help.

---

### Post by Bucky Ball on 2009-12-20
Avoid ndiswrapper at all costs. You need madwifi for that card (from memory). Sounds like you have plugged in with an ethernet cable. Did you get your updates? Try plugging the wireless in and doing an update via the ethernet cable.

Try System->Administration->Hardware Drivers. Anything there but disabled?

---

### Post by sgosnell on 2009-12-20
See [this post](http://ubuntuforums.org/showpost.php?p=7510417&postcount=34).  You may want to read the entire thread.  You need to delete a file already there before you can get the new driver to work.

---

### Post by wah fun on 2009-12-21
Bucky Ball,

Nothing but the nVidia drivers in Hardware Drivers.

Next idea?

---

### Post by wah fun on 2009-12-21
Sgosnel,

That is the thread I followed to setup my configuration.

Next idea?

---

### Post by sgosnell on 2009-12-21
Did you remove /lib/modules/*kernelversion*/kernel/drivers/staging/rt2870sta.ko, where kernelversion is the kernel version you have installed?  If you don't remove or rename the original file, the new one won't be run.

---

### Post by wah fun on 2009-12-28
Yes. I removed the original rt2870sta.ko file before installing the new driver which was installed in /lib/modules/kernelversion/kernel/drivers/wirelesss

Next idea?

---

### Post by wah fun on 2010-01-05
No other ideas? Surely as good as ubuntu is, this problem has already been solved by someone. I have tried numerous "fixes" and installations and have yet to get the Belkin N150 USB network adapter to work. The system sees it, it just doesn't work. No light ever comes on as it does in windows. I would really like to get my wireless up and running.

thx again for all your help.

here's the output for:

lsusb
Bus 002 Device 003: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 002 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 050d:935b Belkin Components 
Bus 001 Device 002: ID 046d:09c2 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

modprobe 2870sta
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions

ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
rt2870 : driver installed
	device (050D:935B) present

---

### Post by sgosnell on 2010-01-05
Are you sure the adapter actually works?  It's possible it's broken.  Does it work on other systems?  Also, you were told about ndiswrapper problems above.  I've never used it, but some say it works and some say it doesn't.  Standard network manager works for me.

---

### Post by wah fun on 2010-01-08
Sgosnell - As I stated in the original post, the adapter works in windows just fine. But it doesn't seem to work in ubuntu and that is my problem. As for ndiswrapper, I only tried it since I couldn't get NetworkManager to recognize the adapter or see the wireless network. After ndiswrapper didn't work, I unistalled it. So that is not interfering with the setup.

If you have an idea on how to fix the problem, I would appreciate seeing it.

thx

---

### Post by ktz84 on 2010-05-02
Did you ever get his device to work as I have the same problem?

---

