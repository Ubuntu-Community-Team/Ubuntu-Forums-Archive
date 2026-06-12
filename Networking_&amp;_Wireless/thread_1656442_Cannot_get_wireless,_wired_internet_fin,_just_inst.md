---
title: "Cannot get wireless, wired internet fin, just installed ubuntu, acer aspire 5252-v305"
date: 2010-12-30
forum: Networking &amp; Wireless
---

### Post by sesquipedalian on 2010-12-30
wired internet *fine* in case that confused anyone

The wireless driver is acer nplify 802.11b/g/n

In additional drivers, it says broadcom STA wireless driver is activated

--------------------------------------

jones@Jones:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

jones@Jones:~$ 



----------------------------------

Command 'lspci' from package 'pciutils' (main)
ispci: command not found
jones@Jones:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (rev 40)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
08:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)
jones@Jones:~$ 

-----------------------------------------------------

So, im wondering if I should go with nsgtk/ndiswrapper or if I should try downloading a new driver compatible to linux? Or if there is some other alternative to my problem im not seeing.

---

### Post by PatchesTheCaveman on 2010-12-30
Hi sesquipedalian!

No need to use ndiswrapper.  Just go to System > Administration > Additional Drivers on your top panel, click on the Broadcom STA wireless driver, and click Install.  

It's that easy!  Let me know if you have any trouble.

---

### Post by dineshs on 2010-12-31
You may also see post#7 [ here]("http://ubuntuforums.org/showthread.php?t=1653415") or post #4 [here]("http://ubuntuforums.org/showthread.php?t=1452464&highlight=hard+blocked")

---

### Post by PatchesTheCaveman on 2010-12-31
I'm sorry, I missed that you already had the STA driver installed.  You most likely have a bad update that breaks the STA driver and many other devices.

To check, run the following command in a terminal:
```
uname -r
```

Copy and paste the line that outputs in a reply to this thread.

---

