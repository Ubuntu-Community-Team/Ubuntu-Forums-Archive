---
title: "Wireless Problems (Inspiron 1525 w/ n-card)"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by andddlay on 2009-04-09
Hello.  First off, please move/delete this thread if it is in the wrong spot/a repeated topic.  I am at college, and there is one room in particular which I go to pretty much every day that gives me a TON of wireless problems.  If I do connect, my whole computer freezes, then unfreezes, then freezes again within a seconds.  It is very annoying and I would very much so like to fix it.  I have also noticed this happening during a registration day, where there were a ton of people accessing the internet (I was not registering at that time).

In my dorm room, I have to use a wireless antenna to help me get wireless internet, which is kind of a burden.

Am I missing a driver or anything?  I have a wireless n card in a Dell Inspiron 1525.

Also, I can't really connect to the internet using Vista, too, in that room.  Though I barely ever go on Vista, so that doesn't matter too much.

If you need what it says in lspci to help, here it is:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

**Edit:  I also have noticed everyone in that room accessing the internet without a problem.**


On a side note (I have tried a few things but it didn't work), my splash screen only shows everything that is starting.  Could somebody guide me through that?

Thank you!!!

---

### Post by andddlay on 2009-04-10
Any help would be grealty appreaciated.

---

### Post by Toady00 on 2009-04-10
Do you know what driver you are using?
Type ```
sudo lshw -C network
``` in a terminal and at the bottom of your wireless entry it should say ```
driver=*something*
``` I believe that *something* should read *iwl4965*

---

### Post by andddlay on 2009-04-10
Thank you for the reply!

Here is every spot where it says driver in "sudo lshw -C network":

configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 (under fd autonegotiation
)

configuration: broadcast=yes driver=iwlagn (under network)

configuration: broadcast=yes driver=bridge driverversion=2.3 (under Network 0)


The closes that matches what you are thinking of is the second one...but it says iwlagn.

---

### Post by superprash2003 on 2009-04-10
[http://ubuntuforums.org/archive/index.php/t-1048176.html](http://ubuntuforums.org/archive/index.php/t-1048176.html)

---

### Post by andddlay on 2009-04-10
> **superprash2003 said:**
> [http://ubuntuforums.org/archive/index.php/t-1048176.html](http://ubuntuforums.org/archive/index.php/t-1048176.html)

That helped.  Thank you!

---

