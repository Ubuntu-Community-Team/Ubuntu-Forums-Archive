---
title: "Acer Aspire One video playback"
date: 2009-04-20
forum: Multimedia Software
---

### Post by yesbar on 2009-04-20
Hi :)

I am new to this place and hope to learn alot about Linux in the future. 

I have installed Ubuntu on my AA1 1gig ram 160gig hdd. I have tweak the UI to my liking and have it the way I want.. I still have one problem tho. All the menus and so on seem slow. When surfing on the internet some pages are lagging when I scroll. Its like I am needing a graphic driver. When I had XP on it I was able to playback HD quality videos but now it wont even show it even tho I have VLC installed. 

I have tried to google the issue but havent been able to find any drivers for the gfx or chipset. Hope you guys can help me what im doing wrong or not doing :)

---

### Post by inobe on 2009-04-20
welcome to the forums 

first and most important' have you updated your system since you installed ubuntu, if not' do that first, also did you install ubuntu in windows using wubi ?

lets get some information from your system, open applications> accessories> terminal.

in terminal type

```
lspci
```

then hit enter, copy and paste that output on your next post.

---

### Post by yesbar on 2009-04-20
I installed Ubuntu from scratched and updated it right away :)

here is my info:

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev ff)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
04:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
04:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
04:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
04:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller

---

