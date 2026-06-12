---
title: "Once again a Hauppauge WinTV issue"
date: 2006-09-06
forum: Multimedia &amp; Video
---

### Post by rmannon on 2006-09-06
Okay I have been all over these forums for the last 2 days trying to get this to work.  I have a hauppauge WinTV PVR card.  It is based on the bt878.  I know that much. I cannot for the life of me, get this thing to come to life.  

Here is my dmesg:

[17179591.476000] bttv: driver version 0.9.16 loaded
[17179591.476000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17179591.476000] bttv: Bt8xx card found (0).
[17179591.476000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 201
[17179591.476000] bttv0: Bt878 (rev 17) at 0000:00:0a.0, irq: 201, latency: 32, mmio: 0xec002000
[17179591.476000] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID i s 0070:13eb
[17179591.476000] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[17179591.476000] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[17179591.480000] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[17179591.568000] tveeprom 1-0050: Hauppauge model 44981, rev E1B2, serial# 9850 274
[17179591.568000] tveeprom 1-0050: tuner model is TCL M2523_5N_E (idx 112, type 4)
[17179591.568000] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
[17179591.568000] tveeprom 1-0050: audio processor is None (idx 0)
[17179591.568000] tveeprom 1-0050: decoder processor is BT878 (idx 14)
[17179591.568000] tveeprom 1-0050: has no radio, has IR remote
[17179591.568000] bttv0: using tuner=4
[17179591.568000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[17179591.572000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17179591.572000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17179591.604000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17179591.628000] tuner 1-0061: chip found @ 0xc2 (bt878 #0 [sw])
[17179591.660000] bttv0: registered device video0
[17179591.660000] bttv0: registered device vbi0
[17179591.660000] bttv0: PLL: 28636363 => 35468950 .<6>pci_hotplug: PCI Hot Plug  PCI Core version: 0.5
[17179591.676000] . ok
[17179591.692000] **tuner 1-0061: tuner type not set**

I think that last line is the problem.  How do I change the tuner type?

I've seen many posts that say this card should "just work".  Oh how I wish it would!

Thanks in advance.

---

### Post by rmannon on 2006-09-07
I guess I should read slower.  The answer was right here:

[https://wiki.ubuntu.com/HardwareSupportComponentsMultimedia](https://wiki.ubuntu.com/HardwareSupportComponentsMultimedia)

"Tuner detected incorrectly. Fix the problem by using commands "sudo rmmod bttv" and "sudo modprobe bttv tuner=51". To make settings permanent, add lines "alias video0 bttv" and "options bttv tuner=51" into file /etc/modprobe.d/bttv and run "update-modules" while being root (or use sudo)"

---

