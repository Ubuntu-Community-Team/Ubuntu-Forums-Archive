---
title: "Wireless not working at all on Revo R3610 with Ubuntu 10.04"
date: 2010-10-09
forum: Networking &amp; Wireless
---

### Post by manilow on 2010-10-09
Hi guys,

I just bought a new Revo R3610 with 3GB RAM and 500GB HDD, with Win 7 Home Premium.

Out of the box I installed Ubuntu 10.04 LTS from USB and connected to my LAN for software updates and graphics driver - all went ok.

My big problem is wireless isn't working at all!!!! At the top right taskbar the wireless symbol has a red exclamation mark on it for starters.

When I click it, I connect to hidden wireless network, enter the SSID and the password (WPA2) then it comes up at the top right with "Wireless network - disconnected - you are now offline".

Any ideas what is going on here? I am assuming the driver for the little USB Revo wireless dongle has been installed ok - is this only for the keyboard/mouse?

UPDATE: just ran :
lshw -C network    *-network DISABLED       
description: Wireless interface        product: RT3090 Wireless 802.11n 1T/1R PCIe
.......


and when I run "nm-tool" it says that wlan0 is disconnected!

Is there some way of turning on the wireless? Apologies of n00b questions!

Please help!!

Thanks

---

### Post by technonuub on 2010-10-09
Experiencing similar issue any help greatfully recieved

---

### Post by manilow on 2010-10-09
Just cracked it and hope I can help you!

Got answer from here:

[http://forums.ebuyer.com/showthread.php?65772-Acer-Aspire-Revo-R3610-Desktop-Atom-330-2GB-RAM-160GB-HDD-NOOPT-NVIDIA-ION-WLAN-Linux-%28Quickfind-225754%29](http://forums.ebuyer.com/showthread.php?65772-Acer-Aspire-Revo-R3610-Desktop-Atom-330-2GB-RAM-160GB-HDD-NOOPT-NVIDIA-ION-WLAN-Linux-%28Quickfind-225754%29)

and post content is here:

-------------
Found my Revo R3610 had an RT3090 card which isn't picked up by Ubuntu 10.04 but driver is here [http://tinyurl.com/yc2n8oe](http://tinyurl.com/yc2n8oe)  - look for rt3090-dkms_2.3.1.7-0ubuntu0~ppa2_all.deb in the link rt3090  - 1:2.3.1.7-0ubuntu0~ppa2 - one click download / install. 						
--------------

I have just instaled this driver and am now working!!!!!

---

