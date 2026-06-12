---
title: "Need help setting up ISA NIC on an old machine"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by shaggy999 on 2010-05-20
Somebody gave me an old Celeron 333MHz system w/ 96 MB RAM and I thought I would set it up as a little torrent server. So I installed Ubuntu server on it, but it does not see the NIC. I know the NIC functions because the person was using it hooked up to a network until a few days ago. Unfortunately, it's an ISA-based NIC and not PCI and my understanding is that I have to pass it IRQ and DMA settings to get it to work. Unfortunately, I wiped the windows 98 partition without thinking of snagging those settings.

First of all, lspci does not show the hardware AT ALL. Here's the output I get:

```

00:00.0 Host bridge: Intel Corporation 440LX/EX - 82443LX/EX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440LX/EX - 82443LX/EX AGP bridge (rev 03)
00:04.0 USB Controller: OPTi Inc. 82C861 (rev 10)
00:14.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:14.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:14.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:14.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)

```

The machine is an old 'Compaq Presario 5050' with a really crappy BIOS that doesn't really offer any help. I read a post somewhere that trying to load the 'ne' driver should work, so I tried:

sudo modprobe ne

and it came back saying "no such device".



Any ideas?

---

### Post by linuxonbute on 2010-05-22
It might help you to look at this thread :

[http://www.linuxforums.org/forum/linux-networking/16827-ne2000-isa-drivers.html](http://www.linuxforums.org/forum/linux-networking/16827-ne2000-isa-drivers.html)

best wishes

Norm

---

### Post by tgalati4 on 2010-05-22
You probably have some isa utilities

man isaset
man isadump

You'll have to google the actual NIC to get the appropriate IO and interrupt settings.  ISA support was dropped from recent kernels, but if you pass the correct settings via modprobe the card should work for you.

You are assuming it's an "ne" card, but it could be anything.

---

### Post by shaggy999 on 2010-05-23
Ok, so I'm 99% of the way there. I finally got the card up and running. It turns out it's an Intel EtherExpress Pro/10+. I found the DOS configuration drivers for it and loaded up a FreeDOS LiveCD and snagged the values:

address=230
irq=3

I am able to load the eepro driver using the following command:

sudo modprobe eepro io=0x230 irq=3

Then I added the eth0 dhcp options to the /etc/network/interfaces file.

Initially, it didn't work, but I rebooted the computer and then re-ran the modprobe command and everything is fine.

But how do I get linux to automatically load the eepro driver along with the options for it? It's not going to be much of a network server if I have to manually log into the computer and run that command. :)

---

### Post by linuxonbute on 2010-05-23
> **shaggy999 said:**
> Ok, so I'm 99% of the way there. I finally got the card up and running. It turns out it's an Intel EtherExpress Pro/10+. I found the DOS configuration drivers for it and loaded up a FreeDOS LiveCD and snagged the values:

address=230
irq=3

I am able to load the eepro driver using the following command:

sudo modprobe eepro io=0x230 irq=3

Then I added the eth0 dhcp options to the /etc/network/interfaces file.

Initially, it didn't work, but I rebooted the computer and then re-ran the modprobe command and everything is fine.

But how do I get linux to automatically load the eepro driver along with the options for it? It's not going to be much of a network server if I have to manually log into the computer and run that command. :)
I think you should be able to put the modprobe command in /etc/rc.local
without needing the sudo bit.
Norm

---

### Post by shaggy999 on 2010-05-23
That seems to work for me. :)

Thanks.

---

### Post by tgalati4 on 2010-05-24
You can also put eepro in the /etc/modules list.  You can put the options in a file in /etc/modprobe.d directory.  I'm not sure if you can pass options in the /etc/modules file, but try that first.

---

