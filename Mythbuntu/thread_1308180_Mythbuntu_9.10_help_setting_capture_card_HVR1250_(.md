---
title: "Mythbuntu 9.10 help setting capture card HVR1250 (not auto-detected)"
date: 2009-10-31
forum: Mythbuntu
---

### Post by rcclaffe on 2009-10-31
I have a fresh Mythbuntu 9.10 and a new HVR1250 capture card (the only capture card).  I hoped it might be autodetected, and saw that for some it works "out of the box", but in my case, the syslog for the driver hints using the "insmod option", and card=3 is mine. 

lspci shows the card is recognized, so I'm close, but have not found the "right" way to set this option.  And even if I did figure it out from the command line, how/where do I set it to apply on boot?

==> /var/log/syslog <==
 cx23885 driver version 0.0.2 loaded
 cx23885 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
 cx23885[0]: Your board isn't known (yet) to the driver.
 cx23885[0]: [COLOR=Blue]Try to pick one of the existing card configs via[/COLOR]
 cx23885[0]: [COLOR=Blue]card=<n> insmod option[/COLOR].  Updating to the latest
 cx23885[0]: version might help as well.
 cx23885[0]: Here is a list of valid choices for the card=<n> insmod option:
 cx23885[0]:    card=0 -> UNKNOWN/GENERIC
 cx23885[0]:    card=1 -> Hauppauge WinTV-HVR1800lp
 cx23885[0]:    card=2 -> Hauppauge WinTV-HVR1800
 cx23885[0]:    [COLOR=Blue]card=3 -> Hauppauge WinTV-HVR1250[/COLOR]
... more card options


==> lspci <==
...
03:00.0 Multimedia video controller: Conexant Systems, Inc. Hauppauge Inc. HDPVR-1250 model 1196 (rev 04)

==> uname -a <==
Linux mythbox 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux


What I have tried: 
1. following guidance here on the insmod option,[_ http://ubuntuforums.org/archive/index.php/t-550276.html_]("http://ubuntuforums.org/archive/index.php/t-550276.html") :
$ sudo insmod /lib/modules/2.6.31-14-generic/kernel/drivers/media/video/cx23885/cx23885.ko card=3
[COLOR=Red]insmod: error inserting[/COLOR] '/lib/modules/2.6.31-14-generic/kernel/drivers/media/video/cx23885/cx23885.ko': [COLOR=Red]-1 File exists[/COLOR]

2. Another thread suggested modprobe was better, but this has no effect, no output:
$ sudo modprobe cx23885 card=3
(enter password...)
$

3. Just checking, it seems the driver seems to be loaded (but I guess syslog already confirms this):
$ modprobe -l | grep cx23885
kernel/drivers/media/video/cx23885/cx23885.ko

4. In myth-setup, Capture Card config, I have selected the "DVB" type, but then can not select a DVB number.  The field is not editable and has no values to choose from.


Forgive this newbie for his sad attempts to figure out what he's doing.  Any pointers on documentation I clearly missed would be great too.  Thanks.

---

### Post by rcclaffe on 2009-11-04
**Solution**: I created a conf file (naming after the driver I was setting the option for) and put it here:[INDENT]/etc/modprobe.d/cx23885.conf
[/INDENT]File contents:[INDENT]options cx23885 card=3 
[/INDENT]Save, reboot, and Whalla: 

[10.138143] cx23885 driver version 0.0.2 loaded
[10.138205] cx23885 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[10.138305] CORE cx23885[0]: subsystem: 0070:2259, board: Hauppauge WinTV-HVR1250 [card=3,insmod option]
[10.264930] tveeprom 0-0050: Encountered bad packet header [ff]. Corrupt or not a Hauppauge eeprom.
[10.264936] cx23885[0]: warning: unknown hauppauge model #0
[10.264938] cx23885[0]: hauppauge eeprom: model=0

I saw the tveeprom errors in other threads so am not worried about those (yet).  Enjoying this small success first.

*Thanks to superm1's post in _[COLOR=Blue][http://ubuntuforums.org/showthread.php?t=1132709](http://ubuntuforums.org/showthread.php?t=1132709)[/COLOR]_ which pointed the way for setting this type of option in Ubuntu 9.x*

---

### Post by uhappo on 2009-12-05
My tv-card is```
Conexant Systems, Inc. Hauppauge Inc. HDPVR-1250 model 1196 (rev 04)
```

I have ubuntu 9.10 64bit.

How do I make this work?

---

### Post by uhappo on 2009-12-28
I've followed your steps and this is what I get:
```

Dec 28 17:46:32 urkkimylly kernel: [   13.536690] cx23885 driver version 0.0.2 loaded
Dec 28 17:46:32 urkkimylly kernel: [   13.536880] cx23885 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Dec 28 17:46:32 urkkimylly kernel: [   13.537031] CORE cx23885[0]: subsystem: 1461:e139, board: Hauppauge WinTV-HVR1250 [card=3,insmod option]
Dec 28 17:46:32 urkkimylly modem-manager: Loaded plugin Generic
Dec 28 17:46:32 urkkimylly modem-manager: Loaded plugin Option
Dec 28 17:46:32 urkkimylly modem-manager: Loaded plugin Ericsson MBM
Dec 28 17:46:32 urkkimylly kernel: [   13.664928] tveeprom 0-0050: Encountered bad packet header [ff]. Corrupt or not a Hauppauge eeprom.
Dec 28 17:46:32 urkkimylly kernel: [   13.664930] cx23885[0]: warning: unknown hauppauge model #0
Dec 28 17:46:32 urkkimylly kernel: [   13.664931] cx23885[0]: hauppauge eeprom: model=0
Dec 28 17:46:32 urkkimylly kernel: [   13.664933] cx23885_dvb_register() allocating 1 frontend(s)
Dec 28 17:46:32 urkkimylly kernel: [   13.664935] cx23885[0]: cx23885 based dvb card
Dec 28 17:46:32 urkkimylly kernel: [   13.994645] cx23885[0]: frontend initialization failed
Dec 28 17:46:32 urkkimylly kernel: [   13.994647] cx23885_dvb_register() dvb_register failed err = -1
Dec 28 17:46:32 urkkimylly kernel: [   13.994649] cx23885_dev_setup() Failed to register dvb on VID_C
Dec 28 17:46:32 urkkimylly kernel: [   13.994654] cx23885_dev_checkrevision() New hardware revision found 0x0
Dec 28 17:46:32 urkkimylly kernel: [   13.994656] cx23885_dev_checkrevision() Hardware revision unknown 0x0
Dec 28 17:46:32 urkkimylly kernel: [   13.994661] cx23885[0]/0: found at 0000:05:00.0, rev: 4, irq: 19, latency: 0, mmio: 0xfbe00000
Dec 28 17:46:32 urkkimylly kernel: [   13.994667] cx23885 0000:05:00.0: setting latency timer to 64
Dec 28 17:46:32 urkkimylly kernel: [   13.994670] IRQ 19/cx23885[0]: IRQF_DISABLED is not guaranteed on shared IRQs

```

What does this mean? Kaffeine doesn't see the card, neither ME Tv

---

### Post by rcclaffe on 2009-12-29
uhappo, although the original issue looked to be solved (so I marked this "solved"), Unfortunately those tveeprom postings I mentioned earlier did not help, and the card still isn't working for me either.  Your errors match mine to the letter so please post any break-through if you find one.

---

### Post by uhappo on 2009-12-30
> **rcclaffe said:**
> uhappo, although the original issue looked to be solved (so I marked this "solved"), Unfortunately those tveeprom postings I mentioned earlier did not help, and the card still isn't working for me either.  Your errors match mine to the letter so please post any break-through if you find one.

Ok, good to know I'm not alone. I'll get back to this right away WHEN I get some news about this, please you do the same whenever something comes up.

---

### Post by fuzzyworbles on 2010-01-16
I have the same card running under 9.10. I got it to work by compiling the module provided here: [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb). With this module, do not add the modprobe option 'card=3.' "3" is in fact the correct card type, however when selected as such, it doesn't work. Let it auto-detect it incorrectly as a 1270. It works fine this way. The only problem I had was with myth itself. Although linux seemed to have loaded the card correctly (no dmesg errors/warings), myth saw no card. To correct this, I added "options CORE_cx23885[0]_dvb adapter_nr=0" to cx23885.conf (a method i gleaned off of how to identify the dual tuners as individual cards). 

let's get down to it though; this card sucks. i use over-the-air QAM and the reception is totally garbage. i prefer to hook the antenna up to my tv to get good quality reception than to be able to rewind garbled livetv on my box.

---

### Post by Yeno on 2010-01-16
I have the HVR 1250 Model 1196 and have a couple errors when compiling 

/v4l-dvb-b48871e88d7d/v4l/cx23888-ir.c: In function 'cx23888_ir_irq_handler':
/v4l-dvb-b48871e88d7d/v4l/cx23888-ir.c:621: error: implicit declaration of function 'kfifo_in_locked'
/v4l-dvb-b48871e88d7d/v4l/cx23888-ir.c: In function 'cx23888_ir_rx_read':
/v4l-dvb-b48871e88d7d/v4l/cx23888-ir.c:688: error: implicit declaration of function 'kfifo_out_locked'
/v4l-dvb-b48871e88d7d/v4l/cx23888-ir.c: In function 'cx23888_ir_probe':
/v4l-dvb-b48871e88d7d/v4l/cx23888-ir.c:1243: warning: passing argument 1 of 'kfifo_alloc' makes integer from pointer without a cast
/v4l-dvb-b48871e88d7d/v4l/cx23888-ir.c:1243: warning: passing argument 3 of 'kfifo_alloc' makes pointer from integer without a cast
make[3]: *** [/v4l-dvb-b48871e88d7d/v4l/cx23888-ir.o] Error 1
make[3]: *** Waiting for unfinished jobs....
make[2]: *** [_module_/v4l-dvb-b48871e88d7d/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.28-17-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/v4l-dvb-b48871e88d7d/v4l'
make: *** [all] Error 2

Does anyone have a fix for this?

dmesg|grep cx
    9.367330] cx23885 driver version 0.0.1 loaded
[    9.367376] cx23885 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.367509] CORE cx23885[0]: subsystem: 0070:2259, board: Hauppauge WinTV-HVR1250 [card=3,insmod option]
[    9.589556] cx23885[0]: warning: unknown hauppauge model #0
[    9.589558] cx23885[0]: hauppauge eeprom: model=0
[    9.589562] cx23885_dvb_register() allocating 1 frontend(s)
[    9.589566] cx23885[0]: cx23885 based dvb card
[    9.648584] cx23885[0]: frontend initialization failed
[    9.648589] cx23885_dvb_register() dvb_register failed err = -1
[    9.648591] cx23885_dev_setup() Failed to register dvb on VID_C
[    9.648595] cx23885_dev_checkrevision() New hardware revision found 0x0
[    9.648597] cx23885_dev_checkrevision() Hardware revision unknown 0x0
[    9.648606] cx23885[0]/0: found at 0000:02:00.0, rev: 4, irq: 17, latency: 0, mmio: 0xfea00000
[    9.648614] cx23885 0000:02:00.0: setting latency timer to 64



Thank you in advance.

---

### Post by mikel11 on 2010-01-16
Same here. New mythbuntu installation, HVR-1600 card, following driver install instructions from [http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600), getting same error, uname sez:

Linux my-myth 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux

---

### Post by mikel11 on 2010-01-16
Oddly enough, the card seems to be not detected anymore (nothing in dmesg) despite my not doing a make install or anything. I went from jerky video to nothing. :-(

---

### Post by Yeno on 2010-01-16
Found a patch from linuxtv.org/hg.  Not sure if thats whats needed or how to install patch.  Something called 'git' is not familiar to me.  I dont have anyting captured by this card unless booting to Vista.  My goal is to have Mythtv going.

---

### Post by BudBear on 2010-01-22
hello all, i am having a problem with my HVR-1250 as well. the funny thing is it worked fine for about 2 months then i decided to move the guts of my HTPC to another case and do a fresh install. what could possibly go wrong right? well, thats when the problems started.  from what i can tell the card is correctly detected. lspci and modprobe checkout. however in myth i  cannot scan channels and i cannot associate the card with a input. am i missing something? why would it have worked perfect and now no longer work? i tried adding the conf file as in post #2 but nothing changed. its most puzzling.

---

### Post by phaedrus351 on 2010-02-13
This never got solved, did it?  Got the same issue, guess I'm back to WMC.

---

### Post by fuzzyworbles on 2010-02-14
yeah, man. it works fine. compile the drivers in the link of my last post, let it identify the card incorrectly, and edit a .conf file for the driver in /etc/modprobe.d/

---

### Post by Failboat88 on 2010-04-01
How do I compile Drivers? I went to that site and downloaded the tar.gz and decompressed but I don't know what to do with the files.

---

### Post by fuzzyworbles on 2010-04-04
compiling is no longer necessary. the cx23885 module included with karmic and lucid now support hvr-1270, etc out of the box. just install linux-restricted-modules or whatever it's called.

---

### Post by uhappo on 2010-04-05
@fuzzyworbles:

So what you're saying doesn't affect this?:

```
05:00.0 Multimedia video controller: Conexant Systems, Inc. Hauppauge Inc. HDPVR-1250 model 1196 (rev 04)
```

I know this/my card is (still...) OEM-card, but I'm more than anxious to know if someday this will be available in ubuntu. I no longer use Win 7 so this card is really collecting dust..

I haven't tried lucid on my tv-card PC, so I don't know what the latest kernel says about that card

---

### Post by fuzzyworbles on 2010-04-11
all i can say is that my 1270, though recognized as a 1250, works out of the box with karmic and lucid. with karmic, however, i had to manually type in the device location in the backend setup. With lucid, on the other hand, it was recognized without any other configuring. i do want to mention though, that i *did* have to compile the modules when i first installed karmic (whenever that was) but found that some time later it became supported after some updates.

long story short, lucid b2 + 1250/70 = no problem

---

### Post by Failboat88 on 2010-05-11
fuzzy, how do I make my pc think my 1250 is a 1270 once I format to lucid? Also, what is an easy what to install the restricted modules? Did you pick the DVB v3 under the myth back-end? How do you manually point the back-end at your card?

Are you using lucid mythbuntu or a different distro? My lucid mythbuntu has not been reading flash drives.

---

### Post by gilson585 on 2010-05-14
Anyone that has a HVR-1250 with subsystem id of **0070:2259** should set
[B]options cx23885 card=20
[/B]in file
**/etc/modprobe.d/cx23885.conf**
not sure if building v4l drivers from source was necessary but I had previously done so before specifying this option
good luck

---

### Post by granrooster on 2010-05-14
This is great.  Definitely works. I didn't update to the latest driver but I did update to the latest mythbuntu.  I was scanning for channels in 5 minutes.  Thank you very much for figuring this out.

---

### Post by fuzzyworbles on 2010-05-16
> **gilson585 said:**
> Anyone that has a HVR-1250 with subsystem id of **0070:2259** should set
[B]options cx23885 card=20
[/B]in file
**/etc/modprobe.d/cx23885.conf**
not sure if building v4l drivers from source was necessary but I had previously done so before specifying this option
good luck

i think v4l modules are for analogue support - at least that's what i think i read on the mythtv wiki for this card. once upon a time i thought about loading and unloading the dvb and v4l modules so i can get the history channel for free (very very strange). but then final exams came up and the curiosity hasn't resurfaced.

.. just so others aren't confused, the pci id for my 1250 is 14f1:8880, which i maintain that works out of the box w/ lucid (though it be detected as a 1270).

---

### Post by fuzzyworbles on 2010-05-16
> **Failboat88 said:**
> fuzzy, how do I make my pc think my 1250 is a 1270 once I format to lucid? Also, what is an easy what to install the restricted modules? Did you pick the DVB v3 under the myth back-end? How do you manually point the back-end at your card?

Are you using lucid mythbuntu or a different distro? My lucid mythbuntu has not been reading flash drives.

if the pci id is 14f1:8880, then you don't *make* it do anything. it just works. there seem to be other 1250's with different pci ids that can be correctly identified i guess (see earlier posts). which restricted modules? nvidia? wireless stuff? yeah, your card will be found under the dvb selection of the mythbacked setup. i'm using lucid mythbuntu. what do flash drives have to do with this?

---

