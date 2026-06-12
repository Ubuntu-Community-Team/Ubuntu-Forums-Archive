---
title: "HVR-1250 no /dev/dvb"
date: 2010-01-09
forum: Multimedia Software
---

### Post by hutchic on 2010-01-09
Recently picked up a HVR-1250 under the impression ( [http://www.mythtv.org/wiki/Hauppauge_HVR-1250](http://www.mythtv.org/wiki/Hauppauge_HVR-1250) ) that support would be easily achieved.

for whatever reason I have no /dev/dvb directory

```
2.6.27-16-generic i686 GNU/Linux

```

dmesg

```
[   14.086421] cx23885 driver version 0.0.2 loaded
[   14.286578] cx23885 0000:04:00.0: PCI INT A -> Link[LN3A] -> GSI 16 (level, low) -> IRQ 16
[   14.286644] CORE cx23885[0]: subsystem: 0070:2211, board: Hauppauge WinTV-HVR1250 [card=3,insmod option]
[   14.420140] cx23885[0]: warning: unknown hauppauge model #0
[   14.420142] cx23885[0]: hauppauge eeprom: model=0
[   14.420145] cx23885_dvb_register() allocating 1 frontend(s)
[   14.420550] cx23885[0]: cx23885 based dvb card
[   14.451320] cx23885[0]: frontend initialization failed
[   14.451326] cx23885_dvb_register() dvb_register failed err = -1
[   14.451329] cx23885_dev_setup() Failed to register dvb on VID_C
[   14.451333] cx23885_dev_checkrevision() Hardware revision = 0xd0
[   14.451341] cx23885[0]/0: found at 0000:04:00.0, rev: 4, irq: 16, latency: 0, mmio: 0xfbc00000
[   14.451349] cx23885 0000:04:00.0: setting latency timer to 64

```

lspci -v

```

04:00.0 Multimedia video controller: Conexant Systems, Inc. Device 8880 (rev 04)
	Subsystem: Hauppauge computer works Inc. Device 2211
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fbc00000 (64-bit, non-prefetchable) [size=2M]
	Capabilities: [40] Express Endpoint, MSI 00
	Capabilities: [80] Power Management version 3
	Capabilities: [90] Vital Product Data <?>
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [200] Virtual Channel <?>
	Kernel driver in use: cx23885
	Kernel modules: cx23885

```

lshw

```

 *-multimedia
	description: Multimedia video controller
	product: Conexant Systems, Inc.
        vendor: Conexant Systems, Inc.
        physical id: 0
        bus info: pci@0000:04:00.0
        version: 04
        width: 64 bits
        clock: 33MHz
        capabilities: pciexpress pm vpd msi bus_master cap_list
        configuration: driver=cx23885 latency=0 module=cx23885

```

I've tried a number of solutions that seem somewhat related to HVR-1250 or missing /dev/dvb including installing the latest V4L TV tuner drivers.

Any help would be appreciated

---

### Post by bmjenkins on 2010-02-21
hutchic:

I also recently got the HVR-1250 with the same impression. I am having motherboard problems that keep me from making it work but I did find a possible solution for your problem.

You need to note the very last line on the mythtv wiki that you linked to. looking at your lspci you have the rev 04 card that they have mentioned in the comments and probably need to upgrade your kernel and v4l-dvb source to get it working. I believe you will need at least kernel 2.6.31 to make it work 'out of the box.'

report back on what you find.

---

### Post by Inflatable Soulmate on 2010-06-25
I recently had this same problem with the same card.  This was with Mythbuntu based on 10.04 with the 2.6.32 kernel at the time.  I ended up adding the **ppa:kernel-ppa/ppa** repo and upgrading the kernel to 2.6.35-6, which didn't help.  Eventually I got on freenode and found some help:

Create a config file:
```
sudo nano -w /etc/modprobe.d/cx23885.conf
```
and type in the  following line:
```
options cx23885 card=20
```save the file and reboot.

This worked for me... thanks to kc on #ubuntu-mythtv on the freenode irc  network for helping me figure this one out.  I would imagine that if  this doesn't work for you, you could also try using the other Hauppauge  HVR-12xx card numbers and hopefully one would work.

---

### Post by drewciferpike on 2010-10-08
I am so frustrated, right now: I just received a 1250, and Mythtv backend continues to report it as "failed to open" in the capture card section.

I've tried card=3, 7, 12, 18, 19, 20 option in the new cx23885.conf file, and the card's still not recognized in Mythtv. dmesg shows me the same info from your screen captures (and from other forums, too), and lspci still reports it as a 1250 rev. 04.

I installed Mythtv just two hours ago, and because I'm new to it, I have no idea where else to look, or what else to do...  I only want to use this computer as a PVR for ATSC programs and a media/music hub.

Is there something I'm forgetting, or am I just screwed, for some reason I don't understand?

Thanks in advance (I hope!).

-Drew

---

### Post by drewciferpike on 2010-10-10
I returned the card to Amazon, and picked up another 1250 from the local Frys. This one gave different info (not 0070:2259) when thrown through dmesg and lspci, and it works like a charm, despite being another rev. 04 card.

I have no idea what the difference was between the two cards, but the new one works.

---

### Post by hutchic on 2010-10-13
Even though you resolved your issue I'll reply here for posterity sake.

[http://forums.scotsnewsletter.com/index.php?showtopic=36509](http://forums.scotsnewsletter.com/index.php?showtopic=36509) Is a pretty thorough debug of issues someone was having with HVR-1250.

To resolve the issues with my HVR-1250 I needed to install the most recent v4l2-firmware v4l2-modules v4l2-ngene-modules and specify the Hauppauge WinTV-HVR1255 (card 20).

I hope this helps anyone else in the future (or myself if I ever need to reinstall this card)

---

