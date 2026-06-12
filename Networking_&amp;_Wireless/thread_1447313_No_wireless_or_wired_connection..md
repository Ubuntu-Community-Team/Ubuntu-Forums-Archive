---
title: "No wireless or wired connection."
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by Jams2602 on 2010-04-05
Hi all.
I'm all new at linux and dont really know much. but i have been sitting up the whole night trying to get internet in some way.
I'm uing a ACER Extensa 5635G laptop with win7 dualboot. 
My wireless card is: intel wifi link 5100 agn.
And my ethernet card is: atheroa AR8131 PCI-E Gigabit thernet controller.

the internet works fine in win7, but in xubuntu it keeps saying that theres no network device.
but when i run lspci i get this:

```
Jams2602@ubuntu:~$ lspci

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)

00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)

01:00.0 VGA compatible controller: nVidia Corporation G98M [GeForce G 105M] (rev a1)

07:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100

09:00.0 Ethernet controller: Attansic Technology Corp. Device 1063 (rev c0)

```

so it does find the cards, but i just cant get them to work? any help would be really good :)

-Jams2602

---

### Post by chili555 on 2010-04-05
There is a known issue with, apparently, ACPI that doesn't allow either network device to operate. A Google search of "ubuntu 5100 attansic bug" will produce many hits including: [https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/478660](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/478660)

The fix seems to be the latest kernel. You might download the latest here: [http://packages.ubuntu.com/karmic/any/linux-image-2.6.31-20-generic](http://packages.ubuntu.com/karmic/any/linux-image-2.6.31-20-generic)

Be sure to get the 32- or 64-bit version as needed. Transfer it on a USB key or otherwise and install it with:```
sudo dpkg -i linux-image-*
```Post back and let us know if this fixed your problem.

---

### Post by Jams2602 on 2010-04-05
> **chili555 said:**
> There is a known issue with, apparently, ACPI that doesn't allow either network device to operate. A Google search of "ubuntu 5100 attansic bug" will produce many hits including: [https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/478660](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/478660)

The fix seems to be the latest kernel. You might download the latest here: [http://packages.ubuntu.com/karmic/any/linux-image-2.6.31-20-generic](http://packages.ubuntu.com/karmic/any/linux-image-2.6.31-20-generic)

Be sure to get the 32- or 64-bit version as needed. Transfer it on a USB key or otherwise and install it with:```
sudo dpkg -i linux-image-*
```Post back and let us know if this fixed your problem.
okay, now i went to [http://packages.ubuntu.com/karmic/i386/linux-image-2.6.31-20-generic/download](http://packages.ubuntu.com/karmic/i386/linux-image-2.6.31-20-generic/download) and downloaded the file. 

but when i move it to xubuntu and click it the package installer starts, and in status for the package it says: "Error: Wrong architecture 'i386'"
and the install package button is not awailable. 
and i couldnt get the code u wrote to work either. then its just saying command not found.

---

### Post by chili555 on 2010-04-05
Is your system an x64 or 64-bit system? Then you need the 64-bit version, not the i386. Find out with:```
uname -a
```If you see those magic terms *x64*, then you need to go back and get the 64-bit version.

You may not have the package *dpkg* installed. The package installer should work fine.

---

### Post by Jams2602 on 2010-04-05
okay i wrote the code and it says x86_64

---

### Post by chili555 on 2010-04-05
Then you need to go here: [http://packages.ubuntu.com/karmic/amd64/linux-image-2.6.31-20-generic/download](http://packages.ubuntu.com/karmic/amd64/linux-image-2.6.31-20-generic/download)

Post back so the searchers will learn.

---

### Post by Jams2602 on 2010-04-05
well that worked just fine. im writing this message from my xubuntu installation, so the net is all good now :) thank u Chili555 :)

---

### Post by chili555 on 2010-04-05
Great! The searchers will appreciate it, too. Enjoy.

Will you please mark the thread Solved?

---

### Post by hatebreed on 2010-05-13
I had the same issue and upgrading to the newest kernel didn't do anything. Here is an easy way to fix the issue. Edit your grub.cfg, assuming you use grub, on the kernel line for Ubuntu at the end type in acpi=off and apci=off then save and reboot. Completely fixed this issue for me and also fixed an issue with another system where it wasn't detecting both cpus.

---

