---
title: "More tuner troubles- is mythbuntu tuner support going backwards?"
date: 2014-03-21
forum: Mythbuntu
---

### Post by itlarson2 on 2014-03-21
I have been trying to find an internal or USB tuner to use in my 0.27 mythtv setup, and am currently attempting to set up a  Hauppauge WinTV-HVR1250.  In the past this model of card just shows up in back-end setup and worked without further configuration.  Here is dmesg output:

```

$ dmesg | grep cx23885
[    7.071632] cx23885 driver version 0.0.3 loaded
[    7.071696] cx23885 0000:03:00.0: PCI INT A -> Link[LN2A] -> GSI 18 (level, low) -> IRQ 18
[    7.071701] cx23885[0]: Your board isn't known (yet) to the driver.
[    7.071702] cx23885[0]: Try to pick one of the existing card configs via
[    7.071703] cx23885[0]: card=<n> insmod option.  Updating to the latest
[    7.071705] cx23885[0]: version might help as well.
[    7.071707] cx23885[0]: Here is a list of valid choices for the card=<n> insmod option:
[    7.071709] cx23885[0]:    card=0 -> UNKNOWN/GENERIC
[    7.071711] cx23885[0]:    card=1 -> Hauppauge WinTV-HVR1800lp
[    7.071713] cx23885[0]:    card=2 -> Hauppauge WinTV-HVR1800
[    7.071715] cx23885[0]:    card=3 -> Hauppauge WinTV-HVR1250
[    7.071717] cx23885[0]:    card=4 -> DViCO FusionHDTV5 Express
[    7.071719] cx23885[0]:    card=5 -> Hauppauge WinTV-HVR1500Q
[    7.071721] cx23885[0]:    card=6 -> Hauppauge WinTV-HVR1500
[    7.071723] cx23885[0]:    card=7 -> Hauppauge WinTV-HVR1200
[    7.071725] cx23885[0]:    card=8 -> Hauppauge WinTV-HVR1700
[    7.071727] cx23885[0]:    card=9 -> Hauppauge WinTV-HVR1400
[    7.071729] cx23885[0]:    card=10 -> DViCO FusionHDTV7 Dual Express
[    7.071731] cx23885[0]:    card=11 -> DViCO FusionHDTV DVB-T Dual Express
[    7.071733] cx23885[0]:    card=12 -> Leadtek Winfast PxDVR3200 H
[    7.071735] cx23885[0]:    card=13 -> Compro VideoMate E650F
[    7.071737] cx23885[0]:    card=14 -> TurboSight TBS 6920
[    7.071739] cx23885[0]:    card=15 -> TeVii S470
[    7.071741] cx23885[0]:    card=16 -> DVBWorld DVB-S2 2005
[    7.071743] cx23885[0]:    card=17 -> NetUP Dual DVB-S2 CI
[    7.071745] cx23885[0]:    card=18 -> Hauppauge WinTV-HVR1270
[    7.071747] cx23885[0]:    card=19 -> Hauppauge WinTV-HVR1275
[    7.071749] cx23885[0]:    card=20 -> Hauppauge WinTV-HVR1255
[    7.071751] cx23885[0]:    card=21 -> Hauppauge WinTV-HVR1210
[    7.071753] cx23885[0]:    card=22 -> Mygica X8506 DMB-TH
[    7.071755] cx23885[0]:    card=23 -> Magic-Pro ProHDTV Extreme 2
[    7.071757] cx23885[0]:    card=24 -> Hauppauge WinTV-HVR1850
[    7.071759] cx23885[0]:    card=25 -> Compro VideoMate E800
[    7.071761] cx23885[0]:    card=26 -> Hauppauge WinTV-HVR1290
[    7.071763] cx23885[0]:    card=27 -> Mygica X8558 PRO DMB-TH
[    7.071764] cx23885[0]:    card=28 -> LEADTEK WinFast PxTV1200
[    7.071766] cx23885[0]:    card=29 -> GoTView X5 3D Hybrid
[    7.071768] cx23885[0]:    card=30 -> NetUP Dual DVB-T/C-CI RF
[    7.071770] cx23885[0]:    card=31 -> Leadtek Winfast PxDVR3200 H XC4000
[    7.071772] cx23885[0]:    card=32 -> MPX-885
[    7.072041] CORE cx23885[0]: subsystem: 0070:2a18, board: UNKNOWN/GENERIC [card=0,autodetected]
[    7.255466] cx23885_dev_checkrevision() Hardware revision = 0xd0
[    7.255473] cx23885[0]/0: found at 0000:03:00.0, rev: 4, irq: 18, latency: 0, mmio: 0xfe800000
[    7.255482] cx23885 0000:03:00.0: setting latency timer to 64

```

I don't understand the insmod stuff, but after some googling I tried creating a file:
/etc/modprobe.d/cx23885.conf
containing the line:
options cx23885 card=3
This just caused an error message at boot time.

This is the third device I have tried.  I have tried a Hauppauge WinTV-HVR-950*Q, *which should workaccording to everything I can find on the internet, and an Avermedia USB tuner since I've had them work well before.  Neither of them worked.  Every tuner I have used in the past has worked with no fiddling.  What gives?

---

### Post by itlarson2 on 2014-03-22
Since I am out of ideas, i would like to compile the driver.  I downloaded what seems to be the right source from [HERE]("https://kernel.googlesource.com/pub/scm/linux/kernel/git/rzhang/linux/+/refs/heads/next/drivers/media/pci/cx23885/"), extracted the files, changed into the directory, and typed "make".  I get the output:

make: *** No targets.  Stop.

That's the end of my abilities.  Could someone tell me how to proceed?

---

### Post by itlarson2 on 2014-03-22
Oh- I also figured out the "card=" thing:
sudo rmmod cx23885
sudo modprobe -v cx23885 card=3
This should Identify the card correctly, but it still doesn't show up in the back-end. I also have tried card=18 through card=21 with no success.

---

### Post by chipdaz on 2014-03-22
You haven't mentioned what kernel/distro version (i.e. 12.04, 13.04, 13.10 etc) you're using. Also "dmesg | grep -i dvb" might show some useful info.

---

### Post by stevee2112 on 2014-03-22
I am also seeing the same issue.  I actually went as far as to recompile the driver and made a local modification so the firmware would know about subsystem "2a18".

Long story short that did not work.  Now admittedly all I did was grep the code for the old subsystem code and change it to the new one.

It seems to me like new versions of this card have a new subsystem id which is explains why I can not find any info besides this thread.

(using 3.8.0-34-generic / disto 12.04 LTS)

---

### Post by itlarson2 on 2014-03-24
This is on Mythbuntu 12.04 with the .27 updates repositories enabled.  Here is the kernel output:

```
$ dmesg | grep -i dvb
[    6.703631] cx23885[0]:    card=11 -> DViCO FusionHDTV DVB-T Dual Express
[    6.703641] cx23885[0]:    card=16 -> DVBWorld DVB-S2 2005
[    6.703643] cx23885[0]:    card=17 -> NetUP Dual DVB-S2 CI
[    6.703668] cx23885[0]:    card=30 -> NetUP Dual DVB-T/C-CI RF
[    6.907756] cx88/2: cx2388x dvb driver version 0.0.9 loaded
[    6.907762] cx88/2: registering cx8802 driver, type: dvb access: shared
[    6.907769] cx88[0]/2: cx2388x based DVB/ATSC card
[    7.212806] DVB: registering new adapter (cx88[0])
[    7.212810] DVB: registering adapter 0 frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...
[ 4080.925782] tveeprom 2-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[ 4080.925817] cx23885_dvb_register() allocating 1 frontend(s)
[ 4080.925827] cx23885[0]: cx23885 based dvb card
[ 4080.931333] cx23885_dvb_register() dvb_register failed err = -22
[ 4080.931338] cx23885_dev_setup() Failed to register dvb on VID_C
[ 4435.442137] tveeprom 2-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[ 4436.067342] cx23885_dvb_register() allocating 1 frontend(s)
[ 4436.067347] cx23885[0]: cx23885 based dvb card
[ 4436.070402] cx23885_dvb_register() dvb_register failed err = -22
[ 4436.070404] cx23885_dev_setup() Failed to register dvb on VID_C
[ 4531.295887] tveeprom 2-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[ 4531.295922] cx23885_dvb_register() allocating 1 frontend(s)
[ 4531.295932] cx23885[0]: cx23885 based dvb card
[ 4531.296376] cx23885_dvb_register() dvb_register failed err = -22
[ 4531.296381] cx23885_dev_setup() Failed to register dvb on VID_C
[ 4673.939009] tveeprom 2-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[ 4673.939045] cx23885_dvb_register() allocating 1 frontend(s)
[ 4673.939053] cx23885[0]: cx23885 based dvb card
[ 4673.944222] cx23885_dvb_register() dvb_register failed err = -22
[ 4673.944225] cx23885_dev_setup() Failed to register dvb on VID_C
[ 5718.777482] tveeprom 2-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[ 5718.777518] cx23885_dvb_register() allocating 1 frontend(s)
[ 5718.777527] cx23885[0]: cx23885 based dvb card
[ 5718.777965] cx23885_dvb_register() dvb_register failed err = -22
[ 5718.777970] cx23885_dev_setup() Failed to register dvb on VID_C
[ 5860.474920] tveeprom 2-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[ 5860.474954] cx23885_dvb_register() allocating 1 frontend(s)
[ 5860.475109] cx23885[0]: cx23885 based dvb card
[ 5860.475551] cx23885_dvb_register() dvb_register failed err = -22
[ 5860.475556] cx23885_dev_setup() Failed to register dvb on VID_C

```

Stevee2112- What was the procedure to compile the module?[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1199880")

---

### Post by tgm4883 on 2014-03-24
> **itlarson2 said:**
> This is on Mythbuntu 12.04 with the .27 updates repositories enabled.  Here is the kernel output:

```
$ dmesg | grep -i dvb
[    6.703631] cx23885[0]:    card=11 -> DViCO FusionHDTV DVB-T Dual Express
[    6.703641] cx23885[0]:    card=16 -> DVBWorld DVB-S2 2005
[    6.703643] cx23885[0]:    card=17 -> NetUP Dual DVB-S2 CI
[    6.703668] cx23885[0]:    card=30 -> NetUP Dual DVB-T/C-CI RF
[    6.907756] cx88/2: cx2388x dvb driver version 0.0.9 loaded
[    6.907762] cx88/2: registering cx8802 driver, type: dvb access: shared
[    6.907769] cx88[0]/2: cx2388x based DVB/ATSC card
[    7.212806] DVB: registering new adapter (cx88[0])
[    7.212810] DVB: registering adapter 0 frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...
[ 4080.925782] tveeprom 2-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[ 4080.925817] cx23885_dvb_register() allocating 1 frontend(s)
[ 4080.925827] cx23885[0]: cx23885 based dvb card
[ 4080.931333] cx23885_dvb_register() dvb_register failed err = -22
[ 4080.931338] cx23885_dev_setup() Failed to register dvb on VID_C
[ 4435.442137] tveeprom 2-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[ 4436.067342] cx23885_dvb_register() allocating 1 frontend(s)
[ 4436.067347] cx23885[0]: cx23885 based dvb card
[ 4436.070402] cx23885_dvb_register() dvb_register failed err = -22
[ 4436.070404] cx23885_dev_setup() Failed to register dvb on VID_C
[ 4531.295887] tveeprom 2-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[ 4531.295922] cx23885_dvb_register() allocating 1 frontend(s)
[ 4531.295932] cx23885[0]: cx23885 based dvb card
[ 4531.296376] cx23885_dvb_register() dvb_register failed err = -22
[ 4531.296381] cx23885_dev_setup() Failed to register dvb on VID_C
[ 4673.939009] tveeprom 2-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[ 4673.939045] cx23885_dvb_register() allocating 1 frontend(s)
[ 4673.939053] cx23885[0]: cx23885 based dvb card
[ 4673.944222] cx23885_dvb_register() dvb_register failed err = -22
[ 4673.944225] cx23885_dev_setup() Failed to register dvb on VID_C
[ 5718.777482] tveeprom 2-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[ 5718.777518] cx23885_dvb_register() allocating 1 frontend(s)
[ 5718.777527] cx23885[0]: cx23885 based dvb card
[ 5718.777965] cx23885_dvb_register() dvb_register failed err = -22
[ 5718.777970] cx23885_dev_setup() Failed to register dvb on VID_C
[ 5860.474920] tveeprom 2-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[ 5860.474954] cx23885_dvb_register() allocating 1 frontend(s)
[ 5860.475109] cx23885[0]: cx23885 based dvb card
[ 5860.475551] cx23885_dvb_register() dvb_register failed err = -22
[ 5860.475556] cx23885_dev_setup() Failed to register dvb on VID_C

```

Stevee2112- What was the procedure to compile the module?[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1199880")

12.04 doesn't tell us a whole lot, as it's LTS and has the hardware enablement stack (meaning it gets new kernel versions). What kernel version are you running?

---

### Post by stevee2112 on 2014-03-24
@tgm4883 

$ uname -a
Linux xbmc 3.8.0-34-generic #49~precise1-Ubuntu SMP Wed Nov 13 18:08:04 UTC 2013 i686 i686 i386 GNU/Linux


@[COLOR=#000000]itlarson2[/COLOR]
I followed this guide:

[http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

---

### Post by itlarson2 on 2014-03-25
Here's the kernel information:

 3.2.0-60-generic #91-Ubuntu SMP Wed Feb 19 03:54:44 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

I will probably need to wait for the weekend to look at the driver compile stuff.

---

### Post by stevee2112 on 2014-03-26
sooooooo, I decided to take a deeper look at the actually card.

[http://imgur.com/aZhWmCs](http://imgur.com/aZhWmCs)

1265!!!!!!!!!

That is not a 1250.

Which is odd because I bought this new and the box is a 1250.

Anyways, I cant find anything related to support for this version, which may be the root of the issue.

---

### Post by itlarson2 on 2014-03-27
Mine says 1265 on the card too!  The box says 1250.  I wonder if I can return this to amazon?

---

### Post by stevee2112 on 2014-03-28
That is my plan too.  I did order another one from a 3rd party seller so perhaps that will actually be a 1250.

I would imagine that at some point someone will look into adding support for the 1265 but I am not willing to wait for that.

---

### Post by Theodore_Vaida on 2014-05-11
I too have been bitten. Wrote an answer to the Linux question on the product page and wrote a review to warn others. This is not a simple tweak, the front end IF tuner device has changed from the TDA8295 to an LG Electronics part (I don't have a strong enough magnifying glass to read the labels.. nor the time to write a driver patch). If you are suckered into buying this card, send it back because they owe you what the packaging says. Form/Fit/Function must remain the same for a labeled part, or the part number must change. Shame on Hauppague for being too lazy to change the part number on the outer packaging.

This is what you will see in the logs if you attempt to use the cx23885 driver with debugging enabled (options cx23885 debug=5)

```
tveeprom 15-0050: Hauppauge model 161111, rev A1I6, serial# 8684867
tveeprom 15-0050: MAC address is 00:0d:fe:84:85:43
tveeprom 15-0050: tuner model is unknown (idx 186, type 4)
tveeprom 15-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
tveeprom 15-0050: audio processor is CX23888 (idx 40)
tveeprom 15-0050: decoder processor is CX23888 (idx 34)
tveeprom 15-0050: has no radio, has IR receiver, has no IR transmitter
cx23885[0]: warning: unknown hauppauge model #161111
cx23885[0]: hauppauge eeprom: model=161111
cx25840 17-0044: cx23888 A/V decoder found @ 0x88 (cx23885[0])
cx25840 17-0044: loaded v4l-cx23885-avcore-01.fw firmware (16382 bytes)
cx23885[0]: registered device video1 [v4l2]
cx23885[0]: registered device vbi1
cx23885[0]: registered ALSA audio device
cx23885_dvb_register() allocating 1 frontend(s)
cx23885[0]: cx23885 based dvb card
cx23885[0]: frontend initialization failed
cx23885_dvb_register() dvb_register failed err = -22
cx23885_dev_setup() Failed to register dvb on VID_C
cx23885_dev_checkrevision() Hardware revision = 0xd0
cx23885[0]/0: found at 0000:03:00.0, rev: 4, irq: 51, latency: 0, mmio: 0xfe200000
```

---

### Post by bigwolf227 on 2014-08-03
I, too have this same card, but since I'm on a limited income, I don't have the luxury of returning my hauppauge card and praying that I actually get an HVR-1250 instead of the HVR-1265. With that being said, does anyone know if there are any plans of including the drivers for the HVR-1265 in an upcoming version of the Linux kernel? Or, is there some programmer willing to tackle this issue with the HVR-1265?

Thanks,
Bigwolf227

---

