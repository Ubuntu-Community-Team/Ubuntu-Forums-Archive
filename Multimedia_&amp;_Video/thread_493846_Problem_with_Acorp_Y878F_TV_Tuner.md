---
title: "Problem with Acorp Y878F TV Tuner"
date: 2007-07-06
forum: Multimedia &amp; Video
---

### Post by danny_b85 on 2007-07-06
Hi, I've got a problem with my Acorp Y878F TV Tuner, it uses an Conexant BT878 chip on it, but I haven't been able to make the damn thing work. I'm currently using Kubuntu 7.04 with the 2.6.20-16 kernel version.

I've already searched the forums for similar problems, but haven't found one related to this model, so I tried modifying /etc/modprobe.d/options with the correct card number I got from $ dmesg, but here's the output I've got on it.

[   41.132323] Linux agpgart interface v0.102 (c) Dave Jones
[   41.152365] Linux video capture interface: v2.00
[   41.196519] bttv: driver version 0.9.16 loaded
[   41.196526] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   41.196590] bttv: Bt8xx card found (0).
[   41.196619] ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 17 (level, low) -> IRQ 19
[   41.196631] bttv0: Bt878 (rev 17) at 0000:00:0d.0, irq: 19, latency: 32, mmio: 0xf2000000
[   41.196642] bttv0: subsystem: 9510:1540 (UNKNOWN)
[   41.196644] please mail id, board name and the correct card= insmod option to [email]video4linux-list@redhat.com[/email]
[   41.196648] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   41.196693] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   41.226805] bttv0: using tuner=-1
[   41.226810] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   41.335407] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   41.336112] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   41.336817] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   41.337620] bttv0: registered device video0
[   41.337676] bttv0: registered device vbi0
[   41.681653] bt878: AUDIO driver version 0.0.0 loaded
[   41.681701] bt878: Bt878 AUDIO function found (0).
[   41.681722] ACPI: PCI Interrupt 0000:00:0d.1[A] -> GSI 17 (level, low) -> IRQ 19
[   41.681729] bt878_probe: card id=[0x15409510], Unknown card.
[   41.681731] Exiting..

Now in case you were wondering the tuner works just fine on Windows XP.
Right now I'm faced with two options:
1. fix the tuner, make it work somehow
2. buy another tuner (Leadtek TV2000 XP Global with Conexant CX2388x chipset).

From what I've seen on the forums and other websites, if I get the right code for this tuner as well as the country code, than I could make it work. I found a website resembling wikipedia with all of the codes for all the tuners supported in Kubuntu 7.04, as well as the country codes, unfortunatelly, I didn't bookmark the address, and google wasn't kind enough to help me find it again.

---

### Post by lilbudda on 2007-07-09
[http://linuxtv.org/](http://linuxtv.org/) this is a good place to start. I have a Encore Eview TV tuner. I can get picture but no sound if I specify options bttv tuner=65 radio=1 in /etc/modprobe.d/bttv

---

