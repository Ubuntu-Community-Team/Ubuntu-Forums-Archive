---
title: "Technisat CableStar 2 PCI not detected with MythBuntu 8.10"
date: 2008-11-22
forum: Mythbuntu
---

### Post by ak2534 on 2008-11-22
I wonder if anyone has got Technisat CableStar 2 PCI working with MythBuntu 8.10?
I'm having hard time getting the card working. lspci output shows that it's being detected as AirStar 2 card which is different card.
Any info on getting the card working would be highly appreciated.

---

### Post by ak2534 on 2008-11-23
lspci shows following info for CableStar 2 PCI:

01:08.0 Network controller: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card (rev ff)

And lspci -n | grep 01:08.0

01:08.0 0280: 13d0:2103 (rev ff)

---

### Post by ak2534 on 2008-11-24
Found following bugreport which seems to be quite indentical to my problem:

[http://webui.sourcelabs.com/kernel/issues/11384](http://webui.sourcelabs.com/kernel/issues/11384)

---

### Post by ak2534 on 2008-11-29
The card seems to get detected correctly in MythBuntu 8.04.1.
So it seems that the support for the specific card was dropped out in 8.10. The question remains, why?

---

### Post by false_apology on 2008-11-30
hey there,

Not sure if this is the right answer for you, but I have the TechinSat "Air2PC" card. I had to install a custom firmware to get it to work correctly. 

The firmware is named dvb-fe-bcm3510-01.fw ( and can be downloaded from [http://www.linuxtv.org/downloads/firmware/](http://www.linuxtv.org/downloads/firmware/)), and needs to be put in /lib/firmware/.

This article has lots of info:
[http://www.linuxtv.org/wiki/index.php/TechniSat_Air2PC-ATSC-PCI](http://www.linuxtv.org/wiki/index.php/TechniSat_Air2PC-ATSC-PCI)

It seems you might have a different card, but if it still uses the broadcom chipset it still might need this firmware. 

Thanks,

---

### Post by ak2534 on 2008-12-01
I wouldn't use that one since your card is DVB-T and mine is DVB-C.

Anyways, I opened a bugreport on the dropping of support fro my card in 8.10. Let's see if anyone picks that one up.

---

### Post by zubov on 2009-02-08
I'm having the same issue with Mythbuntu 8.10 and the same card.  Worked in mythbuntu 7.10 just fine.  I just upgraded over the weekend (I was waiting for nvidia issues to be resolved)

What bug report did you file?  Maybe I can help supply info?  Maybe it's fixed?  I couldn't find where you filed it.  Did you find any workarounds?

---

### Post by ak2534 on 2009-02-11
The bugreport I entered was this one:
[https://bugs.launchpad.net/mythbuntu/+bug/303549](https://bugs.launchpad.net/mythbuntu/+bug/303549)

It hasn't been touched by anyone since I opened it...

---

### Post by zubov on 2009-02-11
Hmm... not quite the same problem that I'm having.  Mine will load the firmware as it did in 7.10 but I can't get any picture out of it with mythtv.  My pchdtv 5500 still works great luckily...

I have the revision 02 card though, not the ff, so I'm using the nxt2002 firmware.  dvb-fe-nxt2002.fw

---

### Post by ak2534 on 2009-02-11
What do you get in dmesg when it tries to load the frontend driver?
Does it work fine?

---

### Post by zubov on 2009-02-11
Everything seems to be fine actually, but Myth isn't able to tune any channels with this card.  I tried to remove the references to my 5500, but I may have missed one or two.  If in doubt, I left it in.

dmesg output
```
[   17.113659] Linux video capture interface: v2.00
[   17.245718] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.612623] b2c2-flexcop: B2C2 FlexcopII/II(b)/III digital TV receiver chip loaded successfully
[   18.210321] flexcop-pci: will use the HW PID filter.
[   18.210326] flexcop-pci: card revision 2
[   18.225666] DVB: registering new adapter (FlexCop Digital TV device)
[   18.227635] b2c2-flexcop: MAC address = 00:d0:d7:02:53:ca
[   18.227895] b2c2-flexcop: i2c master_xfer failed
[   18.228246] b2c2-flexcop: i2c master_xfer failed
[   18.228249] CX24123: cx24123_i2c_readreg: reg=0x0 (error=-121)
[   18.228252] CX24123: wrong demod revision: 87
[   18.835053] b2c2-flexcop: i2c master_xfer failed
[   18.969667] tda9887 0-0043: attaching existing instance
[   19.037833] b2c2-flexcop: i2c master_xfer failed
[   19.058135] b2c2-flexcop: i2c master_xfer failed
[   19.058143] mt352_read_register: readreg error (reg=127, ret==-121)
[   19.100892] nxt200x: NXT2002 Detected
[   19.175516] b2c2-flexcop: found 'Nextwave NXT200X VSB/QAM frontend' .
[   19.175523] DVB: registering frontend 0 (Nextwave NXT200X VSB/QAM frontend)...
[   19.175662] b2c2-flexcop: initialization of 'Air2PC/AirStar 2 ATSC 2nd generation' at the 'PCI' bus controlled by a 'FlexCopIIb' complete
[  106.990639] nxt2002: Waiting for firmware upload (dvb-fe-nxt2002.fw)...
[  106.990649] firmware: requesting dvb-fe-nxt2002.fw
[  107.099932] nxt2002: Waiting for firmware upload(2)...
[  107.406038] nxt2002: Firmware upload complete
[  107.729616] nxt200x: Timeout waiting for nxt200x to stop. This is ok after firmware upload.

```

lspci output
```
00:09.0 Network controller: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card (rev 02)
	Subsystem: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card
	Flags: bus master, slow devsel, latency 32, IRQ 18
	Memory at ea020000 (32-bit, non-prefetchable) [size=64K]
	I/O ports at ee00 [size=32]
	Kernel driver in use: b2c2_flexcop_pci
	Kernel modules: b2c2-flexcop-pci

```

---

### Post by zubov on 2009-02-11
It seems the kernel driver is loaded and working just fine.  Myth won't find any channels on it though.  When scanning for channels, the signal meter will change.  Also while watching live TV on the 5500 and then switching cards, the air2pc will show a signal strength then too but it won't tune the channel.

---

### Post by zubov on 2009-02-12
I must admit, I feel pretty dumb...  Apparently I wasn't letting myth go long enough as all the channels that are found using this card weren't until later in the spectrum.  The test channel that I was using to test the card didn't have enough strength to pull in the signal, so that's why it wasn't working....

EBKAC -- Error Between Keboard And Chair once again :)

---

