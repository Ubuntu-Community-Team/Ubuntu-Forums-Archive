---
title: "Help with Winfast TV2000 XP Deluxe and LIRC"
date: 2008-07-26
forum: Multimedia Software
---

### Post by Bubtottle on 2008-07-26
I am using Ubuntu (gnome) 8.10

I have a Leadtek Winfast TV2000 XP Deluxe tv tuner card which I have physically installed into my computer. My goal is to set it up to work with Myth TV. I am having trouble installing the card on the system, however, and cannot find very many resources to help me. If I can't get the tuner working, I would at least like to be able to use the infra-red reciever that plugs into it.

What I have tried so far is...

**Plug 'n' Play** *(does not work)*
**[http://www.linlap.com/wiki/Installing+the+latest+V4L+TV+tuner+drivers+for+Ubuntu+8.04](http://www.linlap.com/wiki/Installing+the+latest+V4L+TV+tuner+drivers+for+Ubuntu+8.04)** *(from what I can tell, should enable Plug 'n' Play which does not work)*
**[http://www.linuxtv.org/v4lwiki/index.php/Leadtek_WinFast_2000](http://www.linuxtv.org/v4lwiki/index.php/Leadtek_WinFast_2000)** *(I can't figure out what one is meant to do, I tried 'lspci' in a terminal and it listed a lot, not including what this page says it should)*
**[https://help.ubuntu.com/community/InstallLirc/Hardy](https://help.ubuntu.com/community/InstallLirc/Hardy) ***('irw' and 'dmesg | grep -i lirc' and 'sudo dmesg | grep -i lirc' all immediately return a prompt)*
**[http://web.missouri.edu/~datcnc/leadtek_lirc_feisty.html](http://web.missouri.edu/~datcnc/leadtek_lirc_feisty.html)** *('sudo m-a a-i lirc' comes up with somethin saying 'Build of the package lirc-modules-source failed! How do you wish to proceed')*

Output of 'lspci'
```
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
```

If I run TVtime, there is just a blue screen with a setup menu. If I click Input Configuration, then Change Video Source, nothing happens.

If anyone can help me in any way at all, it would be much appreciated.

---

### Post by benrod on 2008-07-28
*> Have you check using "dmesg" by typing it in terminal/console?
If yo do check using "dmesg", then you can see that your tv card have registered or not. Anyway, check what type of chipset your tv card.

*> about tvtime:
open terminal & type: tvtime-scanner
You do "tvtime-scanner" only if you never have the station list before or first time installing tvtime.

---

