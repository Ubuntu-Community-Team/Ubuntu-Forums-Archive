---
title: "[SOLVED] Toshiba laptop has Ibex but no wireless"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by cybrsaylr on 2008-12-17
Just upgraded and installed 8.10 in my 10 month old Toshiba AMD dual core laptop that was running Hardy. Ibex upgrade installed fine, then did 190 updates to bring it up to date. The wired connection works great but can't get wireless to connect. Wireless stopped working on Hardy months ago after some updates knocked wireless out and I couldn't get it back. Was hoping this issue would be corrected by putting in 8.10 but I wasn't so lucky.

Can anyone help me get wireless to work and connect?

This laptop is dual booted with Vista and Vista connects to the router with no problems.

---

### Post by The-Kernel on 2008-12-17
Can you post lspci for us, also post iwconfig?

---

### Post by cybrsaylr on 2008-12-17
Here's the output:

tt@tt-laptop:~$  lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
0e:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
tt@tt-laptop:~$ 


tt@tt-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

---

### Post by P235 on 2008-12-17
Have you tried the procedure outlined here?

[http://ubuntuforums.org/showthread.php?t=766169](http://ubuntuforums.org/showthread.php?t=766169)

---

### Post by cybrsaylr on 2008-12-17
There are 3 pages of solutions there.
Which one works?

---

### Post by P235 on 2008-12-17
I have tried the solution of the very first post of the thread I linked to.  I imagine the madwifi solution could work as well should the first one prove unsatisfactory.

---

### Post by cybrsaylr on 2008-12-17
I get down to:

- download the .inf from the XP driver at : [http://blakecmartin.googlepages.com/...-32-0.2.tar.gz](http://blakecmartin.googlepages.com/...-32-0.2.tar.gz)

- open a terminal and type this command : sudo ndisgtk

- select the net5211.inf file and "enter"

When I open a terminal and enter sudo ndisgtk I can't find that net5211.inf file to enter.

---

### Post by P235 on 2008-12-17
The .inf file must be extracted from the tar.gz file.  Simply locate where you saved the tar.gz file, right click the file, and select extract here.  Place the .inf file in a convenient location, take note of where you placed it, and begin from the "sudo ndisgtk" step again.

---

### Post by cybrsaylr on 2008-12-17
P235, Thanks.
I now have wireless working again @ 100% signal strength. 
Just had a little problem extracting that net5211.inf file but just did it and laptop found my home wireless connection and was able to connect. 

Used the first solution in the link you provided in post #4 and it worked even though I have a 32 bit version of Ibex.

I just hope wireless stays.
On Hardy wireless worked for a few months then some updates that were made knocked it out. I tried a number of solutions and this forum for help but could never get wireless back on Hardy. 

Hope I have better luck with wireless on Ibex.:p


FWIW:
Ibex was slow again while surfing the net. Suspected it was an IPv6 issue again, it was.
Followed the directions on this [link]("http://ubuntuforums.org/showpost.php?p=4891172&postcount=2") and the lag was corrected and Ibex is flying again on the net like Hardy was.

---

