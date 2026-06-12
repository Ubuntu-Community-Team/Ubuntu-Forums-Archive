---
title: "Network UNCLAIMED (no drivers?)"
date: 2012-12-09
forum: Networking &amp; Wireless
---

### Post by The Black Night on 2012-12-09
I built a new computer and partitioned the hard-drive for duel boot with windows 7 / 10.04.4 amd 64. The windows side works fine after using the drivers CD that came with the motherboard but the Ubuntu side wont connect to the Ethernet port it sees it but wont use it.

ran this
> sudo lshw -C network

got this

> desktop:~$ sudo lshw -C network
[sudo] password:
 
  *-network UNCLAIMED
     
       description: Ethernet controller

       product: Atheros Communications

       vendor: Atheros Communications

       physical id: 0

       bus info: pci@0000:03:00.0

       version: c0

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress vpd bus_master cap_list

       configuration: latency=0
       resources: memory:f7100000-f713ffff ioport:d000(size=128)




I looked around for the evening on this forum and others and cant find a guide to fix what I think is a simple problem.
But I don't have a lot of time to spare your help would be very much appreciated.

---

### Post by ahallubuntu on 2012-12-10
You're really going to be better off with Ubuntu 12.04 LTS with brand new hardware vs 10.04, which (desktop version) is supported only another five months anyway.  12.04 is much more likely to support everything out of the box.  I'd venture to guess the ethernet card isn't the only thing that doesn't work right once you start playing around with the OS.

If you want to use Gnome instead of the  Unity desktop, there are easy ways to do that in 12.04.

Otherwise, do an lspci and see what Ethernet card you have.  Maybe you can build module for it for 10.04 or something.

---

### Post by The Black Night on 2012-12-10
thank you for the quick reply :) I like Ubuntu, but I do NOT want Ubuntu 12.04. I unfortunately very much dislike 12.04 and would like to try to fix 10.04.4 if possible.

> desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation Device 0100 (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:14.0 USB Controller: Intel Corporation Device 1e31 (rev 04)
00:16.0 Communication controller: Intel Corporation Device 1e3a (rev 04)
00:1a.0 USB Controller: Intel Corporation Device 1e2d (rev 04)
00:1b.0 Audio device: Intel Corporation Device 1e20 (rev 04)
00:1c.0 PCI bridge: Intel Corporation Device 1e10 (rev c4)
00:1c.4 PCI bridge: Intel Corporation Device 1e18 (rev c4)
00:1d.0 USB Controller: Intel Corporation Device 1e26 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Device 1e44 (rev 04)
00:1f.2 SATA controller: Intel Corporation Device 1e02 (rev 04)
00:1f.3 SMBus: Intel Corporation Device 1e22 (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation Device 104a (rev a1)
01:00.1 Audio device: nVidia Corporation Device 0e08 (rev a1)
03:00.0 Ethernet controller: Atheros Communications Device 1083 (rev c0)


I hope/suspect that once the internet is fixed the other drivers will automatically update.
I know that I sound very formal over the internet  but I am really thankful for any help.

---

