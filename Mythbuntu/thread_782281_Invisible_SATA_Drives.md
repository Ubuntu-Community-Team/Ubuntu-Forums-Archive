---
title: "Invisible SATA Drives"
date: 2008-05-04
forum: Mythbuntu
---

### Post by rbrown3 on 2008-05-04
Greetings:

   I have been working on an upgraded system for my Mythbuntu installation.

   This system is an Intel Dual- Core system (with a 64- bit Intel CPU). It is in a Silverstone chassis (the one with the built- in iMON), and has 2 SATA Drives.

   Problems occur when I attempt to install Mythbuntu. All seems to go well until the installer reaches the drive partitioning window.

   Apparently, the installer *does not* see the SATA drives at all!

   I did check with the system BIOS. The drives are visible there. They simply do not show up during Mythbuntu install.

   Everyone here seems to believe that there are no problems with these drives. Is there some special setup or configuration I have to do in order to make these drives visible???

   Someone please advise!

---

### Post by tamoneya on 2008-05-04
put the liveCD and type ```
sudo fdisk -l
```in the terminal.  Post the output here.

---

### Post by rbrown3 on 2008-05-04
Here is what I see:

ubuntu@ubuntu:~$ sudo fdisk -l
ubuntu@ubuntu:~$ 

There appeas to be abslutely no output whatsoever.

Is this significant?

---

### Post by tamoneya on 2008-05-04
yeah this should list all of your harddrives and show what their partitions are.  You got me there. Try ```
lspci
``` and post the result.  It will probably be pretty long so you should copy out of terminal with ctrl-shift-c

---

### Post by rbrown3 on 2008-05-05
lspci output is below:

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
00:1f.6 Signal processing controller: Intel Corporation 82801H (ICH8 Family) Thermal Reporting Device
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
02:00.0 SATA controller: JMicron Technologies, Inc. JMB361 AHCI/IDE (rev 02)
02:00.1 IDE interface: JMicron Technologies, Inc. JMB361 AHCI/IDE (rev 02)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
04:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
04:02.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
[
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
00:1f.6 Signal processing controller: Intel Corporation 82801H (ICH8 Family) Thermal Reporting Device
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
02:00.0 SATA controller: JMicron Technologies, Inc. JMB361 AHCI/IDE (rev 02)
02:00.1 IDE interface: JMicron Technologies, Inc. JMB361 AHCI/IDE (rev 02)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
04:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
04:02.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
[

---

### Post by Balachmar on 2008-05-12
I am experiencing the same problem.
The drive doesn;t show up, so I can't install.
sudo fdisk -l, list nothing
in dmesg it says something about sda to sdd, but they are the memory card readers in the front of the machine.
This really is a showbreaker.
I hope to see a workaround or a fix of somekind soon on this forum.
If you need any extra information, just ask!

---

### Post by Balachmar on 2008-05-13
For future reference:
I was able to solve this by specifying the all_generic_ide kernel option.
To do this press F6 in the menu. And type all_generic_ide
Then press enter. And hope that it will work for you too!

---

