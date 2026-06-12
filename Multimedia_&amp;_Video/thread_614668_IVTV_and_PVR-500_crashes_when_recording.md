---
title: "IVTV and PVR-500 crashes when recording"
date: 2007-11-16
forum: Multimedia &amp; Video
---

### Post by dwarrenku on 2007-11-16
I just got a new system put together, and can't get my PVR-500 card to capture anything.  The card will scan through the channels with mythtv, so I'm assuming the ivtv-tune workes well, but when i go to test capture using:
```
cat /dev/video0 > /tmp/test_capture.mpg
```
it crashes.  When I open mythtv and attempt to "watch tv", it crashes.  When I open VLC and try to capture from there, it crashes.

When I say it crashes, it doesn't reboot, the screen just freezes.  No mouse movement, no keyboard strokes work, nothing.

I have been through [this troubleshooting guide]("https://help.ubuntu.com/community/Install_IVTV_Troubleshooting") and can see that the drivers are loading properly, and showing the "two" cards (since this is a dual tuner).  Other than that, there are no warnings in the places that it suggests there should be.

Does anyone have some advice.  I can't seem to find info on this problem anywhere.

This is my setup:

AMD64 3000+
GeForce 6800GTOC
PVR-500
KV8-Pro mobo
Gutsy Gibbon 7.10 64-bit

Anything would be much appreciated!

---

### Post by rsambuca on 2007-11-16
When you run the cat command, what crashes exactly - does your whole system freeze?

---

### Post by dwarrenku on 2007-11-16
Yeah, the whole system freezes, like it did in the bad old days with windows 98.  No mouse movement, no keyboard strokes work (the num lock light doesn't go off).  I can't press ctrl+c to stop it.  Nothing works...

---

### Post by rsambuca on 2007-11-16
Have you checked your dmesg for errors?

---

### Post by dwarrenku on 2007-11-16
No errors found there.  I'm not at the computer right now, but when I run:
```
dmesg | tac | sed -n '/=\ \ END INIT IVTV\ \ =/,/= START INIT IVTV =/p;/= START INIT IVTV =/q' | tac
```
I don't get any errors when loading the drivers.  I will post what I see when I get home later.

---

### Post by dannyboy79 on 2007-11-16
Do any log files show anything? Syslog, what about if you open top within a terminal next to the one terminal your trying the cat /dev/video0 command in and see what's occuring. Is there room in your /tmp folder?
you're certain that the pvr-500's tuner's are actually /dev/video0 and /dev/video1? They are on my machine but just curious. trying to brainstorm here.

I am running Xubuntu, then Mythbuntu Control Center on Gutsy, I have a PVR-500 and all is well. Are you using Mythtv to record stuff? I don't know if that matters I suppose. I have never done a scan for channels within mythtv, I pay for schedulesdirect so I already know which ones I get and which ones I don't. Not sure if I was much help, sorry.

---

### Post by bnuytten on 2007-11-17
Make sure you install the correct version of the ivtv drivers for your kernel. I've had similar problems with Feisty and it was solely caused by a mismatch between kernel and ivtv version.

Have a look at this page to match your kernel with ivtv version: [http://ivtvdriver.org/index.php/Download]("http://ivtvdriver.org/index.php/Download")

I have reinstalled Gutsy now which automagically installs the ivtv driver. Just for the record, my current situation:```
uname -a
Linux jupiter 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

md5sum /lib/modules/2.6.22-14-generic/kernel/drivers/media/video/ivtv/ivtv.ko
571cac19c012de3e8aa07f35e9666c3c  /lib/modules/2.6.22-14-generic/kernel/drivers/media/video/ivtv/ivtv.ko
```

---

### Post by dwarrenku on 2007-11-17
So I did a fresh install of ubuntu Gutsy 32 bit to make sure that it wasn't something stupid that I did.  I attempted to capture with the command line, and the same thing happened.

Here is the result of: dmesg | tac | sed -n '/=\ \ END INIT IVTV\ \ =/,/= START INIT IVTV =/p;/= START INIT IVTV =/q' | tac

> ivtv:  ==================== START INIT IVTV ====================
ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload 586 ) loading
wifi0: Atheros 5212: mem=0xe3000000, irq=19
ivtv0: Autodetected Hauppauge card (cx23416 based)
ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 17
ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
usbcore: registered new interface driver hiddev
input: Microsoft Microsoft IntelliMouse&#65533; Explorer as /class/input/input3
input: USB HID v1.00 Mouse [Microsoft Microsoft IntelliMouse&#65533; Explorer] on usb-0000:00:10.1-1
usbcore: registered new interface driver usbhid
/build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
ivtv0: loaded v4l-cx2341x-enc.fw firmware (4144895808 bytes)
ivtv0: Encoder revision: 0x02050032
ivtv0: Recommended firmware version is 0x02060039.
tveeprom 1-0050: Hauppauge model 23552, rev D492, serial# 7967779
tveeprom 1-0050: tuner model is Philips FQ1236A MK4 (idx 92, type 57)
tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
tveeprom 1-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
tveeprom 1-0050: audio processor is CX25843 (idx 37)
tveeprom 1-0050: decoder processor is CX25843 (idx 30)
tveeprom 1-0050: has radio, has no IR receiver, has no IR transmitter
ivtv0: Autodetected WinTV PVR 500 (unit #1)
tuner 1-0043: chip found @ 0x86 (ivtv i2c driver #0)
tda9887 1-0043: tda988[5/6/7] found @ 0x43 (tuner)
tuner 1-0060: TEA5767 detected.
tuner 1-0060: chip found @ 0xc0 (ivtv i2c driver #0)
tuner 1-0060: type set to 62 (Philips TEA5767HN FM Radio)
tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
tuner 1-0061: type set to 57 (Philips FQ1236A MK4)
ivtv0: Registered device video0 for encoder MPEG (4 MB)
ivtv0: Registered device video32 for encoder YUV (2 MB)
ivtv0: Registered device vbi0 for encoder VBI (1 MB)
ivtv0: Registered device video24 for encoder PCM audio (1 MB)
ivtv0: Registered device radio0 for encoder radio
ivtv0: Initialized WinTV PVR 500 (unit #1), card #0
ivtv:  ======================  NEXT CARD  ======================
ivtv1: Autodetected Hauppauge card (cx23416 based)
ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 21 (level, low) -> IRQ 18
ivtv1: Unreasonably low latency timer, setting to 64 (was 32)
ivtv1: loaded v4l-cx2341x-enc.fw firmware (4144896848 bytes)
ivtv1: Encoder revision: 0x02050032
ivtv1: Recommended firmware version is 0x02060039.
tuner 2-0043: chip found @ 0x86 (ivtv i2c driver #1)
tda9887 2-0043: tda988[5/6/7] found @ 0x43 (tuner)
tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #1)
cx25840 2-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #1)
cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #1)
tveeprom 2-0050: Hauppauge model 23552, rev D492, serial# 7967779
tveeprom 2-0050: tuner model is Philips FQ1236A MK4 (idx 92, type 57)
tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
tveeprom 2-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
tveeprom 2-0050: audio processor is CX25843 (idx 37)
tveeprom 2-0050: decoder processor is CX25843 (idx 30)
tveeprom 2-0050: has radio, has no IR receiver, has no IR transmitter
ivtv1: Correcting tveeprom data: no radio present on second unit
ivtv1: Autodetected WinTV PVR 500 (unit #2)
tuner 2-0061: type set to 57 (Philips FQ1236A MK4)
ivtv1: Registered device video1 for encoder MPEG (4 MB)
ivtv1: Registered device video33 for encoder YUV (2 MB)
ivtv1: Registered device vbi1 for encoder VBI (1 MB)
ivtv1: Registered device video25 for encoder PCM audio (1 MB)
ivtv1: Initialized WinTV PVR 500 (unit #2), card #1
ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 16
PCI: Setting latency timer of device 0000:00:11.5 to 64
ivtv:  ====================  END INIT IVTV  ====================


I checked the version of the kernel and it outputed this:

> uname -a
Linux ubuntu 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux


I still don't know what is going on.  I read something about a PSCI problem causing crashes with IVTV, but I'm not sure what that is.

Also, here are some more specs about my system:

KV8-pro mobo
2 gigs ram
250 gigs hdd
AMD 3000+ 64
PVR-500
Nvidia GeForce 6800GTOC

Thanks for the responses so far, I appreciate the help!

---

### Post by bnuytten on 2007-11-18
For what it's worth, I compared your dmesg output to mine. Note that I am using a Europen (PAL) version of the card. Below are the differences, in short:

```
[   13.720000] ivtv0: Autodetected Hauppauge card (cx23416 based)
**[   14.368000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (4159269224 bytes)**
[   14.640000] tveeprom 2-0050: Hauppauge model 23559, rev E491, serial# 9578267
[   14.640000] tveeprom 2-0050: tuner model is Philips FQ1216AME MK4 (idx 91, type 56)
[   14.640000] tveeprom 2-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) (eeprom 0x74)
[   14.640000] tveeprom 2-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[   14.640000] tveeprom 2-0050: audio processor is CX25843 (idx 37)
[   14.640000] tveeprom 2-0050: decoder processor is CX25843 (idx 30)
[   14.640000] tveeprom 2-0050: has radio, has no IR receiver, has no IR transmitter
```

So the chipset version is not exactly the same, even the revision of the card is different. I have no idea if this is relevant or not. You are definitely loading a different firmware version. Which can be normal because of the difference in chipset/card revision.

One final tought is try adding acpi=off to your kernel boot options. If you are using grub, enter the grub menu on boot, press e and just add acpi=off at the end of the kernel line. Maybe it helps.

---

### Post by dwarrenku on 2007-11-19
Everyone, thanks for the help.  I didn't get it working after trying all of these things, and I hate to say it, but I gave up.  I installed windows and am using beyondTV.  I'll give MythTV another try when Hardy Heron comes out.

Thanks

---

### Post by dannyboy79 on 2007-11-20
did you try a different pci slot? did you try irqpoll in the boot options? I have no idea what's going on with your setup. What type of feed are you providing it, straight coax which is your analog cable? are you trying svideo-in? also, do you have 2 many pci cards? what type of power supply you have? do you have tons of hard drives? many many things can cause issues.

---

### Post by db260179 on 2007-12-04
Hello,

First problem is this - ' ivtv1: Recommended firmware version is 0x02060039.'

You have 'Encoder revision: 0x02050032'

Check you have the latest firmware - [http://www.mythtv.org/wiki/index.php/Hauppauge_PVR-500](http://www.mythtv.org/wiki/index.php/Hauppauge_PVR-500)
For helpful tips!

Also my box suffers PCI Latency issues - so i followed this tip [http://www.mythtv.org/wiki/index.php/PCI_Latency](http://www.mythtv.org/wiki/index.php/PCI_Latency)

Try this page for more tips [http://www.mythtv.org/docs/mythtv-HOWTO.html](http://www.mythtv.org/docs/mythtv-HOWTO.html)

Also a few other things, Enabling 'Enable realtime priority threads' causes problems, so disable it! ([http://www.mythtv.org/wiki/index.php/User_Manual:Detailed_configuration_Frontend#Playback](http://www.mythtv.org/wiki/index.php/User_Manual:Detailed_configuration_Frontend#Playback))

Make sure your card is setup correctly in Mythtv Backend ([http://www.mythtv.org/wiki/index.php/Video_capture_card](http://www.mythtv.org/wiki/index.php/Video_capture_card))

Last thing, disable the Powernowd (cpu dynamic module in /etc/init.d/powernow) - Just lately this has been causing loads of issues.

Hope this all helps?
:)

---

### Post by michaelboord on 2008-01-02
Hi, 

I have a Pentiuum C2D with a PVR 500...

And I am having exactly the same pc lockup problems when accessing the PVR card. 

Some info:

root@mc:~# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy

root@mc:~# uname -a
Linux mc 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux


root@mc:~# dmesg | tac | sed -n '/=\ \ END INIT IVTV\ \ =/,/= START INIT IVTV =/p;/= START INIT IVTV =/q' | tac | grep tuner                
[   29.224080] tveeprom 1-0050: tuner model is Samsung TCPG 6121P30A (idx 96, type 73)
[   29.224084] tveeprom 1-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[   29.277972] tuner 1-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   29.277996] tda9887 1-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   29.281942] tuner 1-0060: TEA5767 detected.
[   29.281944] tuner 1-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   29.281954] tuner 1-0060: type set to 62 (Philips TEA5767HN FM Radio)
[   29.282192] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   33.005155] tuner 1-0061: type set to 73 (Samsung TCPG 6121P30A)
[   34.205160] tuner 2-0043: chip found @ 0x86 (ivtv i2c driver #1)
[   34.205170] tda9887 2-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   34.208349] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   37.816806] tveeprom 2-0050: tuner model is Samsung TCPG 6121P30A (idx 96, type 73)
[   37.816811] tveeprom 2-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[   37.867961] tuner 2-0061: type set to 73 (Samsung TCPG 6121P30A)


I have  a Set top box, so no tuning or anything on the PVR 500,
just hooked up to the S-video plug.

acpi=off doesn't help :( 

Anyone any ideas ?  


:( :(

---

### Post by dannyboy79 on 2008-01-02
it appears that you have the PVR-500 with the Samsung tuner built in it. My PVR-500 shows this in my dmesg

Samsung TCPN 2121P30A
and I don't have any problems.
I am using mythbuntu gutsy. 
uname -a shows: Linux gutsy 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux

my lsb_release -a shows the same as yours.


There's some info for the pvr-500 stating the samsung tuner although theres is a TCPN NOT a TCPG? [http://www.gossamer-threads.com/lists/ivtv/users/32325](http://www.gossamer-threads.com/lists/ivtv/users/32325)

Also here: [http://www.mythtv.org/wiki/index.php/Hauppauge_PVR-500](http://www.mythtv.org/wiki/index.php/Hauppauge_PVR-500)

---

### Post by michaelboord on 2008-01-02
[http://www.gossamer-threads.com](http://www.gossamer-threads.com)

is mostly about bad image quality and finetuning  the tuner ..

My entire system locks up when i do cat /dev/video0 > /tmp/test_capture.mpg


Only the reset buttons responds :(

---

### Post by michaelboord on 2008-01-03
**Update: **


Downloade mythbunty 7.10. 

And even on the Live CD the entire machine hangs when trying to get 
video from the PVR 500



**Update: **

Been changing bunch of Bios setting....

Memory speed , PCI latency ACPI etc..

And suddenly, I get video :) 

Just don't remember what change fixed is... 

Still get a system hang when chaning channels :(

---

### Post by michaelboord on 2008-01-20
Somehow got some image after tinkering with bios options. 


Still random crashes... 

Even with mythtv disabled and nothing using the PVR card..

Thought maybe a problem with the card, so replaced it with a PVR 150 which 
my brother owns. 

And still... PC hangs when the card is just in the PC (nothing using it) 

:( :( 

Must be some problem with the IVTV drivers I reckon or a incompatiblity with the motherboard...

---

