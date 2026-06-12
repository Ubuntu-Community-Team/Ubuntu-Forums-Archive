---
title: "how to load dvb-ttpci firmware in dapper with udev??"
date: 2006-06-14
forum: Multimedia &amp; Video
---

### Post by gabster on 2006-06-14
Hi everybody,

I am installing VDR on dapper and I compiled my own 2.6.16.20 kernel with mercurial-dvb drivers in separated modules.

It seems like dapper is not using hotplug at all and I have no idea on how to load the firmware of my full-featured card...

Some people suggested to put the firmware in /lib/firmware but the firmware is not loaded by udev.

dmesg:

[4294678.300000] Linux video capture interface: v2.00
[4294678.310000] stradis 0000:07:01.0: 0: SDM2xx found
[4294678.310000] ACPI: PCI Interrupt 0000:07:01.0[A] -> GSI 22 (level, low) -> IRQ 74
[4294678.310000] videodev: "SAA7146A" has no release callback. Please fix your driver for proper sysfs support, see [http://lwn.net/Articles/36850/](http://lwn.net/Articles/36850/)
[4294678.422000] stradis0: config = 00 0e 13 c2 26 0f ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294678.570000] saa7146: register extension 'dvb'.

lspci -v:

0000:07:01.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
Subsystem: Technotrend Systemtechnik GmbH: Unknown device 000e
Flags: bus master, fast Back2Back, medium devsel, latency 32, IRQ 74
Memory at 52000000 (32-bit, non-prefetchable) [size=512]

Any idea?

Thanks,

Gab

---

### Post by gabster on 2006-06-28
The problem: My hauppauge nexus-s card (probably other SAA7146 based cards too) is broken in 2.6.16, 2.6.17

2.6.15 (working):
Linux video capture interface: v1.00
saa7146: register extension 'dvb'.
saa7146: found saa7146 @ mem f8a4c000 (revision 1, irq 74) (0x13c2,0x000e).
DVB: registering new adapter (Technotrend/Hauppauge WinTV Nexus-S rev2.3).
adapter has MAC addr = 00:d0:5c:04:e3:a7
dvb-ttpci: info @ card 0: firm f0240009, rtsl b0250018, vid 71010068, app 80f62623
dvb-ttpci: firmware @ card 0 supports CI link layer interface
dvb-ttpci: Crystal audio DAC @ card 0 detected
saa7146_vv: saa7146 (0): registered device video0 [v4l2]
DVB: registering frontend 0 (ST STV0299 DVB-S)...
input: DVB on-card IR receiver as /class/input/input2
dvb-ttpci: found av7110-0.

2.6.17 (broken):
stradis 0000:07:01.0: 0: SDM2xx found
videodev: "SAA7146A" has no release callback. Please fix your driver for proper sysfs support...
stradis0: config = 00 0e 13 c2 26 0f ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7146: register extension 'dvb'.

The why: The stupid stradis driver takes over my card (PCI IDs takeover).

The solution: echo "blacklist stradis" >> /etc/modprobe.d/blacklist

---

### Post by jeoffh on 2006-07-14
Copy your firmware file (dvb-ttpci-01.fw) into the folder /lib/firmware/YOUR.KERNEL.VERSION folder
for example, mine was
/lib/firmware/2.6.15-26-386. Well, actually I had 2 folders in that lib/firmware so I just copied the fw file into both because I am such a Linux newbie that I don't know what version of the kernel I am running :P

This worked for me, good luck!


Credit where due, I "gleaned" this from reading:
[http://www.linuxtv.org/v4lwiki/index.php/Talk:Em2880](http://www.linuxtv.org/v4lwiki/index.php/Talk:Em2880)

---

