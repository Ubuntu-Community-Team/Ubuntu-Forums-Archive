---
title: "Atheros AR9385 Wireless Network Adapter"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by SmoothFreeze on 2010-10-11
I can't enable wifi on my HP Pavilion DM3 notebook. Here is the output when i run lspci in terminal:

```
faris@faris-laptop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
02:00.0 VGA compatible controller: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series]
02:00.1 Audio device: ATI Technologies Inc RV710/730
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
09:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```
Is there anything extra I need to do to enable wifi on my netbook?? I'm on 10.10 right now. On 10.04 wifi works fine.

---

### Post by SmoothFreeze on 2010-10-12
Bump. Help?

---

### Post by SmoothFreeze on 2010-10-13
bump, help anyone?

---

### Post by hojgaard on 2010-10-14
Try installing the windows driver if you have it on a cd via ndiswrapper...

It might help..

Otherwise try installing linux backports for wireless:

```
sudo apt-get install linux-backports-modules-wireless-2.6.35-22-generic && sudo apt-get install linux-backports-modules-wireless-maverick-generic
```

---

### Post by SmoothFreeze on 2010-11-06
Still doesn't work. I think I'm giving up.

---

### Post by uncaspi on 2010-11-06
Need a little more information. What shows network-manager?
Does wlan0 shows up in sudo /sbin/iwconfig
What does sudo /sbin/ifconfig shows?
What does sudo lshw -C network
shows?

---

### Post by bigfootnmd on 2010-11-06
You might also tell us which version of Ubuntu you are using.
Ubuntu 10.10 has NATIVE Atheros drivers.  I know this because I researched it and because my Acer Aspire One A0751H has an Atheros Chipset. 

If you haven't tried 10.10 (doesn't matter if it is the NBR or desktop), download it, create a start up disk (put it on a USB)
and then boot from the USB.  If Ubuntu 10.10 finds your WIFI chip and asks you for your KEY then your problem may be solved.

---

### Post by SmoothFreeze on 2010-11-06
I got it solved. All I did was sudo rfkill unblock wifi into terminal.

---

