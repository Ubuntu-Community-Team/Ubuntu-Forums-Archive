---
title: "Compro T750F - frontend initialization failed"
date: 2009-03-10
forum: Multimedia Software
---

### Post by sandgate on 2009-03-10
Hi Everyone,

I have bought a Compro Vista T750F Dual D/A PCI capture card, after using the Compro T300 very successfully on Fedora and Ubuntu's latest versions for over 18 months.

However, the T750F will not load, nor will it register in Kaffeine.

Below is the relevant part of the dmesg;

[   13.468592] Linux video capture interface: v2.00
[   13.619066] saa7130/34: v4l2 driver version 0.2.14 loaded
[   13.619656] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   13.619662] saa7134 0000:04:08.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   13.619669] saa7133[0]: found at 0000:04:08.0, rev: 209, irq: 16, latency: 32, mmio: 0xfdbfe000
[   13.619677] saa7133[0]: subsystem: 185b:c900, board: Compro VideoMate T750 [card=139,autodetected]
[   13.619687] saa7133[0]: board init: gpio is 84bf00
[   13.619698] saa7133[0]: Oops: IR config error [card=139]
[   13.807829] saa7133[0]: i2c eeprom 00: 5b 18 00 c9 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   13.807840] saa7133[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   13.807849] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 01 03 01 08 ff 00 87 ff ff ff ff
[   13.807858] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.807866] saa7133[0]: i2c eeprom 40: ff d7 00 c4 86 1e 05 ff 02 c2 ff 01 c6 ff 05 ff
[   13.807875] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff cb
[   13.807883] saa7133[0]: i2c eeprom 60: 35 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.807892] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.807900] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.807909] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.807917] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.807925] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.807934] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.807942] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.807951] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.807959] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.965088] tuner' 2-0062: chip found @ 0xc4 (saa7133[0])
[   13.973030] tuner' 2-0063: chip found @ 0xc6 (saa7133[0])
[   13.981020] tuner' 2-0068: chip found @ 0xd0 (saa7133[0])
[   14.044778] xc2028 2-0062: creating new instance
[   14.044782] xc2028 2-0062: type set to XCeive xc2028/xc3028 tuner
[   14.044797] firmware: requesting xc3028-v27.fw
[   14.156889] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   14.354108] xc2028 2-0062: Error: firmware xc3028-v27.fw not found.
[   14.354124] firmware: requesting xc3028-v27.fw
[   14.357237] xc2028 2-0062: Error: firmware xc3028-v27.fw not found.
[   14.358680] saa7133[0]: registered device video0 [v4l2]
[   14.358720] saa7133[0]: registered device vbi0
[   14.358754] saa7133[0]: registered device radio0
[   14.364580] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   14.364587] HDA Intel 0000:00:10.1: PCI INT B -> Link[AAZA] -> GSI 23 (level, low) -> IRQ 23
[   14.364613] HDA Intel 0000:00:10.1: setting latency timer to 64
[   14.388218] saa7134 ALSA driver for DMA sound loaded
[   14.388254] saa7133[0]/alsa: saa7133[0] at 0xfdbfe000 irq 16 registered as card -2
[   14.518306] dvb_init() allocating 1 frontend
[   14.518312] saa7133[0]/dvb: Huh? unknown DVB card?
[   14.518315] saa7133[0]/dvb: frontend initialization failed

Does anyone know how to get it going?
If anyone else has this problem, and/or can help, thanks!

---

### Post by xc3RnbFO8P on 2009-03-10
In Terminal:
> sudo apt-get install mercurial linux-headers-$(uname -r) build-essential
> hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
> cd v4l-dvb
> make all
> sudo make install

---

### Post by sandgate on 2009-03-11
Thank you very much for your help Ringi. I followed your instructions, and all appeared to go OK, but still a similar result.

Anymore ideas?
Thank you



[   14.763456] Linux video capture interface: v2.00
[   14.827384] saa7130/34: v4l2 driver version 0.2.14 loaded
[   14.827963] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   14.827969] saa7134 0000:04:08.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   14.827976] saa7133[0]: found at 0000:04:08.0, rev: 209, irq: 16, latency: 32, mmio: 0xfdbfe000
[   14.827983] saa7133[0]: subsystem: 185b:c900, board: Compro VideoMate T750 [card=139,autodetected]
[   14.827994] saa7133[0]: board init: gpio is 84bf00
[   14.828006] saa7133[0]: Oops: IR config error [card=139]
[   14.980027] saa7133[0]: i2c eeprom 00: 5b 18 00 c9 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   14.980038] saa7133[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   14.980047] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 01 03 01 08 ff 00 87 ff ff ff ff
[   14.980055] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.980064] saa7133[0]: i2c eeprom 40: ff d7 00 c4 86 1e 05 ff 02 c2 ff 01 c6 ff 05 ff
[   14.980073] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff cb
[   14.980082] saa7133[0]: i2c eeprom 60: 35 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.980090] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.980099] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.980107] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.980116] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.980124] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.980133] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.980142] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.980150] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.980159] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.988026] saa7133[0]: i2c scan: found device @ 0x1e  [???]
[   15.000035] saa7133[0]: i2c scan: found device @ 0xa0  [eeprom]
[   15.008026] saa7133[0]: i2c scan: found device @ 0xc4  [???]
[   15.016024] saa7133[0]: i2c scan: found device @ 0xd0  [???]
[   15.041079] tuner 2-0062: chip found @ 0xc4 (saa7133[0])
[   15.069820] xc2028 2-0062: creating new instance
[   15.069825] xc2028 2-0062: type set to XCeive xc2028/xc3028 tuner
[   15.069835] firmware: requesting xc3028-v27.fw
[   15.094124] xc2028 2-0062: Error: firmware xc3028-v27.fw not found.
[   15.094135] firmware: requesting xc3028-v27.fw
[   15.097552] xc2028 2-0062: Error: firmware xc3028-v27.fw not found.
[   15.098885] xc2028 2-0062: Error on line 1122: -5
[   15.099000] saa7133[0]: registered device video0 [v4l2]
[   15.099036] saa7133[0]: registered device vbi0
[   15.099070] saa7133[0]: registered device radio0
[   15.120100] saa7134 ALSA driver for DMA sound loaded
[   15.120136] saa7133[0]/alsa: saa7133[0] at 0xfdbfe000 irq 16 registered as card -2
[   15.162193] dvb_init() allocating 1 frontend
[   15.162199] saa7133[0]/dvb: Huh? unknown DVB card?
[   15.162201] saa7133[0]/dvb: frontend initialization failed

---

### Post by xc3RnbFO8P on 2009-03-11
Then read this [How to Obtain the Firmware]("http://www.linuxtv.org/wiki/index.php/Xceive_XC3028/XC2028#How_to_Obtain_the_Firmware")
> Note: The extract_xc3028.pl script is located within the /usr/src/linux/Documentation/video4linux/ directory ... you can also download a copy directly from the link provided above
This would be my option: 
> cd /usr/src/**linux-headers-2.6.28-8-generic**/Documentation/video4linux
wget [http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip](http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip)
unzip -j HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip Driver85/hcw85bda.sys
./extract_xc3028.pl
cp xc3028-v27.fw /lib/firmware
Check in Terminal **(uname -r)**

---

### Post by sandgate on 2009-03-13
Thanks for your help again Ringi.

I followed your instructions and the extract_xc3028.pl script seems to work, saying 'firmwares generated' in terminal but I cannot find the created xc3028-v27.fw file.

I am thinking a clean install may be the way to go?

Regards,
Sandgate

---

### Post by sandgate on 2009-03-13
Ringi,

I have created the firmware using the extract script but still no joy.
The dmesg follows. I will do a clean install, then try your suggestions and will post how I get on.

Thanks again.

> [   13.317113] saa7130/34: v4l2 driver version 0.2.14 loaded
[   13.317703] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   13.317709] saa7134 0000:04:08.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   13.317716] saa7133[0]: found at 0000:04:08.0, rev: 209, irq: 16, latency: 32, mmio: 0xfdbfe000
[   13.317723] saa7133[0]: subsystem: 185b:c900, board: Compro VideoMate T750 [card=139,autodetected]
[   13.317734] saa7133[0]: board init: gpio is 84bf00
[   13.317746] saa7133[0]: Oops: IR config error [card=139]
[   13.476035] saa7133[0]: i2c eeprom 00: 5b 18 00 c9 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   13.476046] saa7133[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   13.476055] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 01 03 01 08 ff 00 87 ff ff ff ff
[   13.476064] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.476072] saa7133[0]: i2c eeprom 40: ff d7 00 c4 86 1e 05 ff 02 c2 ff 01 c6 ff 05 ff
[   13.476081] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff cb
[   13.476089] saa7133[0]: i2c eeprom 60: 35 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.476098] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.476106] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.476115] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.476123] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.476132] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.476140] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.476149] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.476157] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.476166] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.508082] tuner 2-0062: chip found @ 0xc4 (saa7133[0])
[   13.548912] xc2028 2-0062: creating new instance
[   13.548916] xc2028 2-0062: type set to XCeive xc2028/xc3028 tuner
[   13.548926] firmware: requesting xc3028-v27.fw
[   13.999716] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   14.055433] xc2028 2-0062: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
[   14.055534] xc2028 2-0062: Loading firmware for type=BASE F8MHZ MTS (7), id 0000000000000000.
[   14.055940] xc2028 2-0062: i2c output error: rc = -5 (should be 64)
[   14.055943] xc2028 2-0062: -5 returned from send
[   14.055947] xc2028 2-0062: Error -22 while loading base firmware
[   14.108032] xc2028 2-0062: Loading firmware for type=BASE F8MHZ MTS (7), id 0000000000000000.
[   14.108570] xc2028 2-0062: i2c output error: rc = -5 (should be 64)
[   14.108573] xc2028 2-0062: -5 returned from send
[   14.108576] xc2028 2-0062: Error -22 while loading base firmware
[   14.108589] xc2028 2-0062: Loading firmware for type=BASE F8MHZ MTS (7), id 0000000000000000.
[   14.109126] xc2028 2-0062: i2c output error: rc = -5 (should be 64)
[   14.109128] xc2028 2-0062: -5 returned from send
[   14.109131] xc2028 2-0062: Error -22 while loading base firmware
[   14.165021] xc2028 2-0062: Loading firmware for type=BASE F8MHZ MTS (7), id 0000000000000000.
[   14.165555] xc2028 2-0062: i2c output error: rc = -5 (should be 64)
[   14.165557] xc2028 2-0062: -5 returned from send
[   14.165560] xc2028 2-0062: Error -22 while loading base firmware
[   14.166394] xc2028 2-0062: Error on line 1124: -5
[   14.173289] saa7133[0]: registered device video0 [v4l2]
[   14.173451] saa7133[0]: registered device vbi0
[   14.173507] saa7133[0]: registered device radio0
[   14.174059] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   14.174064] HDA Intel 0000:00:10.1: PCI INT B -> Link[AAZA] -> GSI 23 (level, low) -> IRQ 23
[   14.174089] HDA Intel 0000:00:10.1: setting latency timer to 64
[   14.196322] saa7134 ALSA driver for DMA sound loaded
[   14.196353] saa7133[0]/alsa: saa7133[0] at 0xfdbfe000 irq 16 registered as card -2
[   14.337099] dvb_init() allocating 1 frontend
[   14.337105] saa7133[0]/dvb: Huh? unknown DVB card?
[   14.337108] saa7133[0]/dvb: frontend initialization failed

---

### Post by xc3RnbFO8P on 2009-03-14
If you are going to make clean install, don't compile V4L drivers, Just copy/paste the xc3028-v27.fw driver.
What is the size of your xc3028-v27.fw?

---

### Post by sandgate on 2009-03-14
Hi Ringi,

Its 64.7 KB in size. OK I will just copy/paste the xc3028-v27.fw driver.

Thanks again,
Sandgate

---

### Post by Jimbley on 2009-03-18
Hi folks,

Any progress with the T750? Did you have to do anything for the card to be correctly detected? Mine lists it as generic/unknown. I've specified options in the /etc/modprobe.d/options file but to no avail.

The lines in my /etc/modules file lists saa7134, saa7134-alsa and saa7134-dvb and modprobe confirms that they are loaded.

sudo lspci -v also lists the card correctly as a Compro Videomate T750 in case that helps but doesn't list the device as using any modules. Perhaps this is pertinent?

Sorry, I have no intention of hijacking your post and intend to start another collating links to the info I've found so far and the outputs of all the usual programs.

As always, any help will be greatly appreciated.

UPDATE:
I've upgraded to Ubuntu 8.10 and dmesg correctly identifies the card. I've applied the firmware, but get the following:
> 
[   20.057036] xc2028 2-0061: i2c output error: rc = -5 (should be 4)
[   20.057040] xc2028 2-0061: -5 returned from send
[   20.057044] xc2028 2-0061: Error -22 while loading base firmware

I'll have a root through the firmware and see if I turn anything up. One more week and then I'm getting a new card.

---

### Post by wbee on 2009-03-18
Hello,

I'm posting so this will show up on my "wbee's posts",since I also have saa7134 issues and want to follow along to try to learn something.

---------

Thanks.

---

### Post by eldo on 2009-03-30
Hi Everyone,
Have the same issue. Can anybody help us? It's perfectly work under Windows but Ubuntu only find it and don't want work correctly. If needed i can check something or make some modules (i wrote on C++, but dont know anything about this device hardware,signals etc.)

P.S. Sorry for bad english (I am from Ukraine):-)

---

### Post by sandgate on 2009-04-10
[FONT="Tahoma"]Hi Ringi, Jimbley, Wbee and Eldo,

I just did a clean intall of Ubuntu 9.04 Beta.
I copied the relevant part of dmesg, and attached as a file.
The problem could be at;
BUG: unable to handle kernel paging request at fffffff4,
I am not sure.

Thanks,
Sandgate
[/FONT]

---

### Post by xc3RnbFO8P on 2009-04-11
Its a bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/316405]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/316405")

---

### Post by Jimbley on 2009-04-11
Aha, good work Ringi.

I backtracked through the v4l2 source files and found the relevant function call that presents the error. It originates from a call to one of the i2c send functions. I've had a few odd things happen too. I get a UU entry when using i2cdump after a reset. I even (stupidly) resorted to dual-booting XP and Ubuntu to see if I could do some more tracing there as my dmesg output is different from that posted on the V4l site (which really needs updating. I'll do some work there if I get a chance). There's a couple of patches floating around, but before I tried them out I thought I'd flash my BIOS to solve a HDD recognition problem. You can guess what happened (or didn't) next..............

I know it's not very politically correct to slate windows these days, but I hate it. Especially XP. I'll repost when I've got a new BIOS chip. :(

---

### Post by jalyst on 2009-09-08
As far as I can tell there's no support for dual DVB for this yet.
Only dual analogue; audio & radio isn't even tested but may work.
Another user reports AV-in works...

[http://www.linuxtv.org/pipermail/linux-dvb/2007-April/017395.html](http://www.linuxtv.org/pipermail/linux-dvb/2007-April/017395.html)
[http://www.linuxtv.org/pipermail/linux-dvb/2007-April/017433.html](http://www.linuxtv.org/pipermail/linux-dvb/2007-April/017433.html)
[http://osdir.com/ml/linux-media/2009-07/msg00010.html](http://osdir.com/ml/linux-media/2009-07/msg00010.html)

admittedly I haven't searched linux-media archives properly, this has only been found via google...

---

### Post by jalyst on 2009-09-08
hmm maybe not
[http://www.mail-archive.com/linux-media@vger.kernel.org/msg07466.html](http://www.mail-archive.com/linux-media@vger.kernel.org/msg07466.html)

try searching the archives thoroughly but, and send an email to the list. If you provide good diagnostic info they normally respond.

---

### Post by nicoloks on 2009-11-22
Hi All,

Just Wondering if the Compro T750F was a safe selection for Ubuntu 9.10 yet? The bug Ringi listed above is now marked as fixed, and I'm looking at building a budget HTPC for a mate and was looking at the Compro T750F as a dual DTV tuner solution. Any updates would be appreciated.

---

### Post by jalyst on 2009-11-22
You might be able to get a clearer picture from Linux-Media archives.

Last I searched this is what turned up...
[http://www.mail-archive.com/linux-media@vger.kernel.org/msg07466.html](http://www.mail-archive.com/linux-media@vger.kernel.org/msg07466.html)

But there could be more recent developments, [sign up]("http://vger.kernel.org/vger-lists.html#linux-media") & have a look at the [wiki]("http://www.linuxtv.org/wiki/index.php/Main_Page")

And let us know if you do find something!
I'm using a HVR-2200 which has active support, but I'm still curious to know how this ended-up.

---

### Post by nicoloks on 2009-11-23
Thanks for the link. Not sounding terribly promising though. Think I might just go the safety with the NOVAT500 as I know it works straight out of the box and is only an extra $25. Thanks again.

---

### Post by jalyst on 2009-11-23
Or the hvr-2200 if you want something little more full featured.
Assuming you're in Australasia or Europe; otherwsie the model no's slightly different (2250?) 
Not sure if the support is the same though....

[http://www.kernellabs.com/blog/](http://www.kernellabs.com/blog/)

---

### Post by jalyst on 2009-11-23
should be also supported
[http://www.kernellabs.com/blog/?page_id=17](http://www.kernellabs.com/blog/?page_id=17)

---

### Post by nicoloks on 2009-11-23
Looks good, but unfortunately I need PCI as the only PCIe is already taken by the video card.

---

### Post by jalyst on 2009-11-24
bummer.

---

