---
title: "e100 problem after moving HDD to another machine"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by voelkerc on 2006-06-04
Ok, kinda strange... What I'm trying to do is this:

I want to move my server from Mandrake to Ubuntu. So, I thought I'd use a spare HD, put it in my server machine, and install the base Ubuntu stuff. Then move the HD to another machine so I can install the rest and configure (Apache, Postgres, etc, etc) while my Mandrake box is still live. When I moved the HD over, I forgot to disable the onboard ethernet card (a Realtek RTL8139) in the other box to allow ubuntu to see the same NIC driver as in the server (an e100).

So, I'm now having problems getting the e100 driver to respond appropriately. I cannot do a ifconfig eth0 dhcp or ifconfig eth0 ip_addy. 

Everything I could think of is below. Need any other info? Let me know... Got another way to accomplish the goal as presented above? I'm all ears.

I guess I'd be happy to use the Realtek if I can get back to the e100 for the server. So, if I could get advice about how to find out which module/driver to use and how to install it, that'd be great, too.

Note, I do not have xwindows installed.

Thanks.
-Chad

#lspci | grep Eth
0000:00:0a.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 01)

#lspci -v | grep -A6 Eth
0000:00:0a.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 01)
	Flags: bus master, medium devsel, latency 32, IRQ 185
	Memory at ec100000 (32-bit, prefetchable) [size=4K]
	I/O ports at d000 [size=32]
	Memory at ec000000 (32-bit, non-prefetchable) [size=1M]
	Expansion ROM at 50000000 [disabled] [size=1M]

#lsmod | grep e100
e100                   43012  0 
mii                     7040  1 e100

<see attached for complete lsmod listing>

#sudo eepro100-diag -a
eepro100-diag.c:v2.13 2/28/2005 Donald Becker (becker@scyld.com)
 [http://www.scyld.com/diag/index.html](http://www.scyld.com/diag/index.html)
Index #1: Found a Intel i82557/8/9 EtherExpressPro100 adapter at 0xd000.
i82557 chip registers at 0xd000:
  01000000 00000000 00000000 00080002 1821782f 00000000
  No interrupt sources are pending.
   The transmit unit state is 'Idle'.
   The receive unit state is 'Idle'.
  This status is unusual for an activated interface.
 The Command register has an unprocessed command 0100(?!).

#sudo eepro100-diag -m
eepro100-diag.c:v2.13 2/28/2005 Donald Becker (becker@scyld.com)
 [http://www.scyld.com/diag/index.html](http://www.scyld.com/diag/index.html)
Index #1: Found a Intel i82557/8/9 EtherExpressPro100 adapter at 0xd000.
Primary transceiver is MII PHY #1.libmii.c:v2.11 2/28/2005  Donald Becker (becker@scyld.com)
 [http://www.scyld.com/diag/index.html](http://www.scyld.com/diag/index.html)
 MII PHY #1 transceiver registers:
   3100 782f 2000 5c00 01e1 05e1 0001 0000
   0000 0000 0000 0000 0000 0000 0000 0000
   0000 0000 0000 0000 0000 0000 0000 8440
   8000 0021 0000 1800 a3b9 0015 0705 001d.
 Basic mode control register 0x3100: Auto-negotiation enabled.
 Basic mode status register 0x782f ... 782f.
   Link status: established.
   Capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation complete.
   *** Link Jabber! ***
 Vendor ID is 08:00:17:--:--:--, model 0 rev. 0.
   No specific information is known about this transceiver type.
 I'm advertising 01e1: 100baseTx-FD 100baseTx 10baseT-FD 10baseT
   Advertising no additional info pages.
   IEEE 802.3 CSMA/CD protocol.
 Link partner capability is 05e1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Negotiation did not complete.

#dmesg | grep eth0
[42949386.200000] e100: eth0: e100_probe: addr 0xec100000, irq 185, MAC addr my_mac

#cat /etc/network/interfaces | grep eth0
auto eth0
iface eth0 inet dhcp

#sudo ifconfig eth0 dhcp
dhcp: Host name lookup failure

#sudo ifconfig eth0 192.168.1.200
SIOSCIFADDR: No such device
eth0: ERROR while getting interface flags: No such device

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
e100

---

### Post by voelkerc on 2006-06-05
Posting in case someone else finds the same issue...

The Mandrake box has eth0 and eth1 (both e100 cards), the new box has an e100 card. All that I had to do was add an entry in /etc/networking/interfaces for eth2 and all was well in the new box.

I didn't expect the OS to know that this new e100 wasn't the same as eth0 from the old (Mandrake) box. So, it treated the card in the new box as the third configured NIC.

Make sense? Works for me.
-Chad

---

### Post by ruggieror on 2006-09-09
I have been investigating this problem for a while now as I have quite an old notebook and replacing the internal PCI ethernet card is not easy (as they are hard to find), but this problem seem to come from an interruption to the NICs power supply diring a particular operation.

Example, I stupidly forced a power off of my notebook instead of shutting down windows xp and as a result it crapped over the NIC EEPROM.  This type of error seems to be common with the Intel EtherExpress Pro 10/100 (i82557/8/9 EtherExpressPro100) and this is evident when you search google.

There seems to be a great deal of belief that the problem can be fixed by software reprogramming of the EEPROM, but I simply cannot find anything to do this with, nor can I get a copy of the original EEPROM software to upload if it were possible.

Does anyone have a solution for this or even instructions for fixing this using eepro100-diag.

Cheers,

Rick

---

### Post by Stone123 on 2006-09-13
> **ruggieror said:**
> 
There seems to be a great deal of belief that the problem can be fixed by software reprogramming of the EEPROM, but I simply cannot find anything to do this with, nor can I get a copy of the original EEPROM software to upload if it were possible.

Does anyone have a solution for this or even instructions for fixing this using eepro100-diag.

Cheers,

Rick

No i don't think so . Well you need intels boot fix. I tryed but with no sucess. I can attach a bootcd (barts boot cd) with intels fix that i made since i dont have any floppy.
It didn't work for me.

---

