---
title: "Mythbuntu 8.04.1 and pcHDTV HD-5500"
date: 2008-07-30
forum: Mythbuntu
---

### Post by Quentusrex on 2008-07-30
Ubuntu doesn't detect the card... And I can't find any documentation about how to install and configure the card. Everything seems to point to DVB and click 'enable on demand'; I did that, but the card isn't recognized.

Here is lspci:

cxs@cxs-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G35 Express DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82G35 Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 82G35 Express Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
02:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller


It's not there....

---

### Post by andrewc6l on 2008-07-30
I've got a machine with a pcHDTV HD-5500 in it, and it works. (I started with Mythbuntu 8.04 and upgraded with a package manager to 8.04.1). You might want to try re-seating the card / switching it to another slot.

---

### Post by jerunamuck on 2009-02-09
FYI:
This is what I see with lspci for my PCHD-5500

03:06.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
03:06.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
03:06.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
03:06.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)

---

### Post by dad311 on 2009-02-09
A buddy of might just installed this card with Mythbuntu 8.10.  No issues or special steps.  If your having problems with 8.04 you might try a fresh install of 8.10.

---

### Post by newlinux on 2009-02-09
this looks like a hardware issue - the card isn't even being seen on the bus. I recommend reseating it, putting it in a different slot, maybe even seeing if it recognized in a different computer. I used to use this card  back in dapper and edgy and I know people used in Feisty and Hardy. I doubt it's a software issue.

---

