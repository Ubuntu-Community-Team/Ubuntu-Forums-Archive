---
title: "Wubi - no internet"
date: 2009-03-21
forum: Networking &amp; Wireless
---

### Post by matthewlowery on 2009-03-21
I'm having a similar problem. I have installed WUBI. It all works fine except for the internet. Why can't it just detect the settings like all my other computers? I have typed in all the codes I can find from the actual wireless router, but still no luck. Any help?

---

### Post by matthewlowery on 2009-03-21
can somebody help?

---

### Post by matthewlowery on 2009-03-21
[FONT="Trebuchet MS"]I have a BT Broadband V1.5 Hub.
All my laptops and computers have connected wirelessly fine.
I have installed WUBI, and booted up in it. For some reason it can't connect to the internet. I have all the codes on it.
SSID, Key, Wep 64bit Hexadecimal, the pin, and the MAC Address.
How can I get it to connect? If it helps, the laptop is an Acer Aspire 5751z.[/FONT]

---

### Post by matthewlowery on 2009-03-21
jeez why can't I get a bloody answer? Everybody else on this forum does!

---

### Post by matthewlowery on 2009-03-21
if you don't know, just tell me! Why does everybody except me get answers?

---

### Post by prythin on 2009-03-21
> **Death_DealerV69 said:**
> i keep seeing everywhere to go to system-admin-network but i dont have that option.
i have network tools.
i can't connect to the internet using wireless.
btw i just installed it yesterday and am completely new to this.
i got all the updates that i could through the update manager.

Sounds like you are using Wubi in which case it is at System - Preferences - Network Configuration.

I'm having this exact same problem too, posted elsewhere about it but this seems to be the relevant thread. Also using Wubi 8.10.

---

### Post by drstove on 2009-03-21
I have the same connection problems. I have an  Acer Aspire One which comes loaded with XP. Because I am running UBUNTU 8.10 on two desktop computers and a Toshiba laptop, I would like to remain 100% Linux. The Acer One finds and uses the wireless connection when running XP but when I run Ubuntu it only shows wired. How do I get it to look for a wireless connection?

---

### Post by ugm6hr on 2009-03-21
New thread started for new poster and new problem.

---

### Post by matthewlowery on 2009-03-21
are you honestly telling me *nobody* knows a solution? come on people!

---

### Post by ugm6hr on 2009-03-21
More detail would be helpful.

See the wifi help link below.

---

### Post by matthewlowery on 2009-03-22
so there isn't a single person on this entire OFFICIAL UBUNTU FORUM that knows how to solve a simple wireless problem?

---

### Post by matthewlowery on 2009-03-22
same problem as him, but how do i paste it here if i have no internet?

---

### Post by ugm6hr on 2009-03-22
You can save the output as a file.

For example (the same can be done for all that commands):

```
lspci >> lspci.txt
```

This will create a file lspci.txt in your Home Folder, which you can save to a USB (or even your own HD), and upload from Windows.

---

### Post by matthewlowery on 2009-03-22
ok when i type lspci -nn i get this;
matthew@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
05:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
06:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)

---

### Post by matthewlowery on 2009-03-22
just lspci gives me this if it's any different:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

---

### Post by ugm6hr on 2009-03-22
> **matthewlowery said:**
> 06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

This is your wifi controller.

More detail please...

32 or 64-bit?

Which version of Ubuntu?

If you don't know:
```
uname -a
```

---

### Post by matthewlowery on 2009-03-22
Linux ubuntu 2.6.27-7-generic #1 SMP Fri Oct 24 06:40:41 UTC 2008 x86_64 GNU/Linux

---

### Post by ugm6hr on 2009-03-22
64-bit Intrepid 8.10

[http://ubuntuforums.org/showpost.php?p=6861397&postcount=2](http://ubuntuforums.org/showpost.php?p=6861397&postcount=2)

---

### Post by matthewlowery on 2009-03-22
so I just download those files and reboot?

---

### Post by matthewlowery on 2009-03-22
OH MY GOD IT WORKS! THANK YOU SO MUCH SORRY I SPAMMED A BIT!!!
I'm gonna stick around here, I was gonna just stay for the solution, but now I kinda got used to this place. THANK YOU AGAIN!!! As I may  have said, this will be my laptop for my birthday in May, my first laptop, and I really wanted to be able to run Ubuntu and bring it into school with me. NOW I CAN THANKEEEEEE

---

### Post by ugm6hr on 2009-03-22
Congrats, and welcome to the community :)

I understand the zeal felt with a new laptop.... Enjoy it.

---

