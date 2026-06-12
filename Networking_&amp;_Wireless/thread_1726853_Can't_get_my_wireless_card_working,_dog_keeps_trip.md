---
title: "Can't get my wireless card working, dog keeps tripping on the CAT"
date: 2011-04-11
forum: Networking &amp; Wireless
---

### Post by EriktheAwful on 2011-04-11
I'm a Linux noob, and I just got my new computer up and running Ubuntu 10.10. I asked how to get my wireless running on the Installation forum, but I think I'm needing some deeper troubleshooting.

I have a  Zonet ZEW1642S which uses the Ralink  RT3062 chipset. In terminal, lspci -nn gives:
```
erik@erik-System-Product-Name-System-Product-Name:~$ lspci -nn
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1510]
00:01.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:9802]
00:01.1 Audio device [0403]: ATI Technologies Inc Device [1002:1314]
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] Device [1022:1512]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] [1002:4390] (rev 40)
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 42)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB700/SB800 IDE Controller [1002:439c] (rev 40)
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d] (rev 40)
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller [1002:4399]
00:15.0 PCI bridge [0604]: ATI Technologies Inc Device [1002:43a0]
00:15.1 PCI bridge [0604]: ATI Technologies Inc Device [1002:43a1]
00:15.2 PCI bridge [0604]: ATI Technologies Inc Device [1002:43a2]
00:15.3 PCI bridge [0604]: ATI Technologies Inc Device [1002:43a3]
00:16.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:16.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1700] (rev 43)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1701]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1702]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1703]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1704]
00:18.5 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1718]
00:18.6 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1716]
00:18.7 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1719]
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
05:00.0 PCI bridge [0604]: Device [1b21:1080] (rev 01)
06:00.0 Network controller [0280]: RaLink Device [1814:3062]
06:02.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev c0)
07:00.0 USB Controller [0c03]: Device [1b21:1042]
```lsmod doesn't show anything relating to the wireless card. I installed the linux firmware non-free package. "lspci | grep wifi", "dmesg | grep wifi", and "dmesg | grep firmware" all return nothing.

Where do I go from here?

---

### Post by EriktheAwful on 2011-04-12
I followed these instructions, [http://ubuntuforums.org/showthread.php?t=1608095](http://ubuntuforums.org/showthread.php?t=1608095), and got all the way to modifying /etc/modules. I can't make any changes because I'm not logged on as root. I tried logging out and discovered I **can't** log on as root. I did the normal Ubuntu install, but was I supposed to specify a root logon? I thought there would be one by default. Did I screwup somewhere in the install?

I ended up rebooting my computer and now the wireless connection shows up, but it doesn't stay connected long enough to load a web page. At least it's progress, but I'm still unsure where to go from here. Any ideas?

---

### Post by hijiz on 2011-04-12
I'm not sure but my first instinct tells me you should conect using an auto eth0 and then go to System>Administrator>Aditional Drivers and install the correct driver. Hope it Helps. If this donsnt work 
just login as root, just add **_sudo_** before the rest of the comand in terminal.

---

### Post by hijiz on 2011-04-12
Sorry what i meant to say at the second half was try adding sudo before the rest of the comand and root acounts dont exist in ubuntu by default sudo elevates your privilages in the system so you become root.

---

### Post by EriktheAwful on 2011-04-13
I booted up my computer tonight and both the wireless and wired connections were working, so I unplugged the wired connection and it's doing fine. I did go to System>Administration>Additional Drivers and it says the driver is already in use!

It looks like the problem is solved, even if I'm not sure how. Thanks!

---

