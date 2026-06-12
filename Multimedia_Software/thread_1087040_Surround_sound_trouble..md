---
title: "Surround sound trouble."
date: 2009-03-04
forum: Multimedia Software
---

### Post by BmoreFerris on 2009-03-04
I have searched and search for help with getting my 5.1 to work. everything I try ended up the same way.  Just as it started.  I only get Master, PMC, and Capture options in the pref tab.  I even edited the daemon.conf file with no luck


This is what I get when i run "lspci"
visual@visual:~/Desktop/LinuxDrivers/Audio/alsa-1.0.18rc3$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: ASUSTeK Computer Inc. Device 9602
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)

I have a M4A78 PRO running Ubuntu intrepid 64 Kernel 2.6.27-13-generic

---

### Post by kostkon on 2009-03-12
Since you are using 8.10, you need to follow [this guide]("http://ubuntuforums.org/showthread.php?t=795525") to enable 5.1.

---

### Post by BmoreFerris on 2009-03-12
I tried that.  Thanks though.

---

### Post by markbuntu on 2009-03-14
Get 

gnome-alsamixer

---

### Post by BmoreFerris on 2009-03-14
Still the same.  Just Master, Capture, and PCM

---

### Post by markbuntu on 2009-03-14
Hmm, I am on jaunty right now getting some massive update. As soon as it is finished i will switch over to my Intrepid install and get back to you. I have an a similar azalia but ona 790 ...stand by

---

### Post by markbuntu on 2009-03-14
Ok, I think I see where the problem is. Right click on the panel volume control and choose open volume control. Device: Select the ATI HDA SB. Click the preferences box. You should find the controls you want in there. Just check them to have them appear in the volume control. Then you can unmute them and turn them up.

---

### Post by BmoreFerris on 2009-03-16
that is the device I am useing.  I still only have the three options.

---

### Post by BmoreFerris on 2009-03-16
I just reinstalled the drivers and now have all the speakers but the rear two.

---

