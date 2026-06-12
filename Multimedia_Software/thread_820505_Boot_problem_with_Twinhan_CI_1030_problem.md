---
title: "Boot problem with Twinhan CI 1030 problem"
date: 2008-06-06
forum: Multimedia Software
---

### Post by Saiph on 2008-06-06
I like Ubuntu, but have problem with install (boot) with my sat card Twinhan CI 1030 it is rare sat card.

-Install freeze at the begining, i must get out the card from pci slot.

-When I boot, comp freeze with something like this: Found BT878  card ...

Using Ubuntu 8.04 64bit. THank you very much. I want use this card.

---

### Post by xc3RnbFO8P on 2008-06-06
[http://www.linuxtv.org/wiki/index.php/Twinhan_VP-1030]("http://www.linuxtv.org/wiki/index.php/Twinhan_VP-1030")

> CI: unsupported by current LinuxTV drivers, supported only by vendor drivers for kernel 2.4.20

---

### Post by Saiph on 2008-06-10
Thx,
I put in /etc/modules:
bttv i2c_hw=1 card=0x71
dvb-bt8xx
dst

and in /etc/modprobe.d/options

options bttv i2c_hw=1 card=0x71
options dst dst_addons=32

and booting success, but have another problem:

drivers not loaded successfully here is demsg:

[   41.668896] bttv: driver version 0.9.17 loaded
[   41.668900] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   41.668954] bttv: Bt8xx card found (0).
[   41.668979] ACPI: PCI Interrupt 0000:00:07.0[A] -> GSI 18 (level, low) -> IRQ 18
[   41.668989] bttv0: Bt878 (rev 17) at 0000:00:07.0, irq: 18, latency: 32, mmio: 0xcfdfe000
[   41.669078] bttv0: subsystem: 18c6:0001 (UNKNOWN)
[   41.669080] please mail id, board name and the correct card= insmod option to [email]video4linux-list@redhat.com[/email]
[   41.669084] bttv0: using: Twinhan DST + clones [card=113,insmod option]
[   41.669106] bttv0: gpio: en=00000000, out=00000000 in=00f548fd [init]
[   41.669139] bttv0: tuner absent
[   41.669154] bttv0: add subdevice "dvb0"
[   41.698149] bt878: AUDIO driver version 0.0.0 loaded
[   41.698192] bt878: Bt878 AUDIO function found (0).
[   41.698210] ACPI: PCI Interrupt 0000:00:07.1[A] -> GSI 18 (level, low) -> IRQ 18
[   41.698215] bt878_probe: card id=[0x118c6], Unknown card.
[   41.698216] Exiting..
[   41.698220] ACPI: PCI interrupt for device 0000:00:07.1 disabled
[   41.698227] bt878: probe of 0000:00:07.1 failed with error -22
[   41.788077] dvb_bt8xx: unable to determine DMA core of card 0,
[   41.788082] dvb_bt8xx: if you have the ALSA bt87x audio driver installed, try removing it.
[   41.788088] dvb-bt8xx: probe of dvb0 failed with error -14

Please help me using this card in ubuntu 8.04. Thank you.

lspci:
00:07.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
00:07.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

---

### Post by xc3RnbFO8P on 2008-06-10
Try to change 0x71 with 0x113.

---

### Post by Saiph on 2008-06-10
113 is hexagonaly 0x71 its the same, when I write 0x113, comp freeze booting. I try card=113 and its ok too.

How can I do this: dvb_bt8xx: if you have the ALSA bt87x audio driver installed, try removing it.

Is  dvb-s card for linux there, which one have no problem and I cant do anything like that? Only turn on computer and watch sat channel? I hope so.

---

### Post by Saiph on 2008-10-01
Problem solved rewriten last byte eeprom e7 to 22 :D

Thanks to [http://unix.opp.homeunix.net/faq/Twinhan%20VP-1020A%20-%20LinuxTVWiki.htm]("http://unix.opp.homeunix.net/faq/Twinhan%20VP-1020A%20-%20LinuxTVWiki.htm")

 or

[http://pasthis.com/random/y61bc50]("http://pasthis.com/random/y61bc50")
:guitar:

---

### Post by Saiph on 2008-11-01
Solution: It must be replaced all fourth bytes , not the last only. Now card is detect like Twinhan DVB PLus, and working fine, by the way, ubuntu then knowns the card automaticaly.

But problem with twinhan remote, buttons havent right functions. Any solutions?

---

### Post by Saiph on 2008-12-24
Another problem:
When I reboot to XP or Vista, something rewrite repeately last right (changed by me) byte in eeprom 22 to bad one.  :confused:
Help please.....

---

### Post by Saiph on 2010-04-23
Solution: restart
After some restart card is not detected.

Now I can try to use CI.
Great combination: VDR - XBMC
Where to buy supported cam modules? they are little bit old, arent they?

How to use Phoenix connect to serial port with vdr? I have got one.

---

### Post by steefjeqv on 2010-04-29
Maybe this will help :

[http://ubuntuforums.org/showthread.php?t=1126258&highlight=vdr]("http://ubuntuforums.org/showthread.php?t=1126258&highlight=vdr")

Greetings,
Steven

---

### Post by Saiph on 2010-06-15
Bad card, bought another one.

---

