---
title: "Help with Wpn111"
date: 2010-07-23
forum: Networking &amp; Wireless
---

### Post by mogey5101 on 2010-07-23
I need help with getting my netgear wpn111. Can someone walk me through step by step on how to get it setup and installed for ubuntu 10.04?

---

### Post by dca on 2010-07-23
I could've sworn that Netgear uses an old Atheros chipset, type *sudo lspci* at CLI and paste here to confirm...  If so, you should just be able to plug in, wait a couple of seconds, click on the nm-applet icon in systray and see wireless networks.  Alot of the old how-tos go back to '07 using ndiswrapper and Windows drivers...
 
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=652910](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=652910)

[http://www.linuxquestions.org/questions/linux-wireless-networking-41/getting-netgear-wireless-usb-dongle-wpn111-atheros-chipset-to-work-on-ubuntu-6-06-a-515914/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/getting-netgear-wireless-usb-dongle-wpn111-atheros-chipset-to-work-on-ubuntu-6-06-a-515914/)

---

### Post by mogey5101 on 2010-07-23
mogey@ubuntu:~$ sudo lspci
[sudo] password for mogey: 
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4850]
04:00.1 Audio device: ATI Technologies Inc HD48x0 audio
mogey@ubuntu:~$ 
 that is the result of sudo lspci

---

### Post by mogey5101 on 2010-07-23
Also there is a problem I cant get build essentials because my ubuntu machine isn't connected the the internet.

---

