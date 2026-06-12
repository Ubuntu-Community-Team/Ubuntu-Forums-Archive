---
title: "Ubuntu 11.10 - Wireless connection not working"
date: 2011-11-12
forum: Networking &amp; Wireless
---

### Post by Waterlily on 2011-11-12
Hi, everyone!

I'm a newby here, so please bare ^___^

I had Ubuntu 11.04 for a while and had no trouble connecting to the internet. Now that I''m using Ubuntu 11.10, my wireless connection is extremely unstable, keeps dropping, and ever since yesterday, I'm not even able to access the internet through my wireless network. I' currently using an open network. As a matter of fact, my network manager is showing some unusual behavior. For example, it shows that I was connected to a wired connection yesterday, even though I don't have cable internet. Please help!!

Thank you.

---

### Post by noneofthem on 2011-11-26
I am having problems, too since I upgraded to 11.10. First my graphics card performance went down, then I lost my sound and at last I even lost my wifi connection. Apart from that programs like Transmission, Rhythmbox, LibreOffice and even Nautilus would freeze/or crash randomly. After reinstalling everything about a week later, I got my sound and wifi back. Graphics performance is still bad and I still get random crashes sometimes. Yesterday, I was just watching a YouTube video with the current Google Chrome and I got logged out! This is not what a final release should behave like. 11.10 feels like an early beta version to me.

I am afraid, we will have to wait until Canonical fixes those issues or until someone who is smarter than us comes up with a workaround.

---

### Post by Jack Cunter on 2011-11-26
Have the same problem and this is what i seen in an older (solved) post:

> **walt.smith1960 said:**
> For starters, you'll probably want to copy the result of this command:

Open a terminal windows --top left panel click Applications -> accessories -> terminal

In the resulting black box type the following 

lspci

copy & paste the resulting text

If you're using a built-in wifi, this command should come up with  several lines of text.  Somewhere in that text you'll see references  names like Atheros or Broadcomm or Realtek. That will be the  manufacturer of your wireless chip.  Then we have a place to start but  paste the entire output of lspci please.

If you were using a plug-in wifi adapter you'd use the command lsusb.  That will list all USB devices.

---

### Post by Jack Cunter on 2011-11-26
Now i did that and i get this:

thomassen@thomassen-Presario-C500-RY517EA-ABH:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
06:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by praseodym on 2011-11-26
Hi Jack Cunter,

for this Broadcom device you need the proprietary firmware packages **b43-fwcutter** and **firmware-b43-installer** via cable connection and software center.

---

