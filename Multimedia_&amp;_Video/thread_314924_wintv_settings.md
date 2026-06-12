---
title: "wintv settings"
date: 2006-12-08
forum: Multimedia &amp; Video
---

### Post by gistenjunge on 2006-12-08
im not happy with opening another wintv thread, but i the stuff ive read on several forums didnt do the trick.

im using ubuntu 5.10 and have an old hauppauge wintv card. it worked once, but stopped working. the only thing i changed is setting up my old soundblaster live (used the sound-on-board before).

i put the sounblaster in the pci slot where the tv card has been, and put the tv card one slot below (3rd) due to space.

dmesg | grep bttv had no result at first, than i started to modprobe bttv after reading howtos on some threads.

theres a thread on the ubuntu forums which tells to set the tuner to 51, but somehow i only get 3 channels in very bad condition. im using pal and live in germany.

and i just changed my xorg.conf. i used twinview with a CRT and LCD, the CRT died and i changed it to work with the LCD only.
this made the last line in my 'dmesg | grep bttv' appear...

```
root@giste:~# dmesg | grep bttv
[4294694.535000] bttv: driver version 0.9.15 loaded
[4294694.535000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[4294694.540000] bttv: Bt8xx card found (0).
[4294694.540000] bttv0: Bt878 (rev 2) at 0000:00:0b.0, irq: 19, latency: 32, mmio: 0xdddfe000
[4294694.540000] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[4294694.540000] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[4294694.541000] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[4294694.543000] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[4294694.656000] bttv0: using tuner=51
[4294694.656000] bttv0: i2c: checking for MSP34xx @ 0x80... found
[4294694.744000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[4294694.746000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[4294694.795000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[4294694.893000] bttv0: registered device video0
[4294694.894000] bttv0: registered device vbi0
[4294694.895000] bttv0: registered device radio0
[4294694.906000] bttv0: PLL: 28636363 => 35468950 .. ok
[4295986.252000] bttv0: SCERR @ 37ffd014,bits: HSYNC OFLOW FBUS SCERR*

```

dont know if its important, but the device radio0 section is listed, though ive got an wintv w/o radio.
any ideas are appreciated

---

