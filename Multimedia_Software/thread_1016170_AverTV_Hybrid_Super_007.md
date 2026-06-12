---
title: "AverTV Hybrid Super 007"
date: 2008-12-19
forum: Multimedia Software
---

### Post by Zofteis on 2008-12-19
Hey everybody,
I´m quiet new with Linux, but I´m planning to delete my old Windows XP and set up my PC again with Ubuntu as the only OS.
At the moment i´m just testing it, but Windows ist still installed.
Nearly everything i need is working well, but there is still one problem. I´m not able to get my tv tuner working under linux and so i still have to switch to Windows to watch TV....
My Tv Tuner is called: "AverTV Hybrid Super 007" [http://www.avermedia.com/avertv/product/ProductDetail.aspx?Id=16](http://www.avermedia.com/avertv/product/ProductDetail.aspx?Id=16)

Is it possible to get this tuner work under Linux???
The most important thing for me is to receive analogue singnal, because Digital TV isn´t such a big thing in our region ;)
I´ve searched a long time, but i didn´t find a solution...
Is it possible to get it work?
Thanks for your help,
Zofteis

---

### Post by xc3RnbFO8P on 2008-12-19
Read this:
[http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTV_DVB-T_Super_007]("http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTV_DVB-T_Super_007")

---

### Post by Zofteis on 2008-12-19
" Notes
Super Hybrid 007 is not currently supported. "

Oh thats sad... So i have to to watch TV with windows...
Do you thing there is a chance that support will be added in a little while?

kind regards

---

### Post by xc3RnbFO8P on 2008-12-19
> It is currently not supported under Linux. However, experimental support exists (see below for details). 
You can try that.
Do dmesg in Terminal before and after, show the output,
it could be useful information.

---

### Post by Zofteis on 2008-12-19
Well I tried it a few days ago so i can't post what dmesg showed before...
The firmware link is down, but i've found it on a russian side...
After you posted the link again, i was not quiet sure if only the analogue version (AverTV Super 007) and the DVB-T version has experimentel support...
Mine is called AverTV Hybrid Super 007 and might receive both, but as said above DVB-T isn't important at all...
Well here ist the dmesg output! I don't know much about the stuff in there...

[   55.104990] usbcore: registered new interface driver usblp
[   55.138916] saa7130/34: v4l2 driver version 0.2.14 loaded
[   55.139265] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 19
[   55.139275] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [LNKA] -> GSI 19 (level, low) -> IRQ 20
[   55.139282] saa7133[0]: found at 0000:01:08.0, rev: 209, irq: 20, latency: 32, mmio: 0xdfeff800
[   55.139288] saa7133[0]: subsystem: 1461:f01d, board: Avermedia Super 007 [card=117,autodetected]
[   55.139295] saa7133[0]: board init: gpio is 40000
[   55.296034] saa7133[0]: i2c eeprom 00: 61 14 1d f0 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   55.296044] saa7133[0]: i2c eeprom 10: ff ff ff ff ff 20 ff ff ff ff ff ff ff ff ff ff
[   55.296049] saa7133[0]: i2c eeprom 20: 01 40 01 32 32 01 01 43 88 ff 00 55 ff ff ff ff
[   55.296055] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   55.296060] saa7133[0]: i2c eeprom 40: ff 21 00 c0 96 10 05 32 15 76 8b 0c ff ff ff ff
[   55.296065] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   55.296070] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   55.296076] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   55.296081] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   55.296086] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   55.296092] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   55.296097] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   55.296102] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   55.296108] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   55.296113] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   55.296118] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   55.403959] tuner' 2-004b: chip found @ 0x96 (saa7133[0])
[   55.495825] tda829x 2-004b: setting tuner address to 60
[   55.583731] tda829x 2-004b: type set to tda8290+75a
[   59.416154] saa7133[0]: registered device video0 [v4l2]
[   59.416173] saa7133[0]: registered device vbi0
[   59.479997] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   59.480000] ACPI: PCI Interrupt 0000:00:05.0[B] -> Link [LAZA] -> GSI 22 (level, low) -> IRQ 17
[   59.480027] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   59.514420] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   59.563021] dvb_init() allocating 1 frontend
[   59.608682] DVB: registering new adapter (saa7133[0])
[   59.608689] DVB: registering adapter 0 frontend 0 (Philips TDA10046H DVB-T)...
[   59.679589] tda1004x: setting up plls for 48MHz sampling clock
[   59.964304] tda1004x: found firmware revision 29 -- ok
[   60.035529] lp0: using parport0 (interrupt-driven).
[   60.081426] Adding 4000176k swap on /dev/sda3.  Priority:-1 extents:1 across:4000176k

I hope this is the right part, cause i didn't wont to post the whole report ;)

Kind regrads

---

### Post by xc3RnbFO8P on 2008-12-19
> I hope this is the right part, cause i didn't wont to post the whole report
yes

Install Mediubuntu codec [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")
and then **Kaffeine** from Add/Remove.
Open Kaffeine and scan channels.

---

### Post by Zofteis on 2008-12-19
Well... somehow it does not work!
When i start Kaffeine a message appears:"Can't bind info socket!!!"
Then i can only choose between Digital TV and DVB Client!
When searching for channels, no channel can be found...
I guess thats because he ist only searching for dvb-t channels...
Cause if i control the DVB Settings, my tuner is recognized as Phillips TDA10046H DVB-T type Terrestrial...
So analogue TV doesn't seem to work somehow...
Maybe the message :"Can't bind info socket!!!" is the problem?

Kind regards

---

### Post by xc3RnbFO8P on 2008-12-19
> I guess thats because he ist only searching for dvb-t channels...
Cause if i control the DVB Settings, my tuner is recognized as Phillips TDA10046H DVB-T type Terrestrial...
Dont you have a digital antenna?

---

### Post by Zofteis on 2008-12-19
Well as i said, above...
The most important thing for me is the analogue TV, because the DVB-T signal is very weak in here....
At the moment i am not quiet sure what you mean with "digital antenna"...
I think you mean an antenna to receive Terrestrial TV? 
Actually the problem is that in the area where i live here in Germany, there are only two channels i guess which you can receive with the help of an antenna... So i never bought one...

Kind regards

---

### Post by xc3RnbFO8P on 2008-12-19
> I think you mean an antenna to receive Terrestrial TV?
Yes

If you have a TV cable connected to TV card and a 15 cm wire on the other end,
place it it in the window pointed up 90°, have a digital antenna :)

---

### Post by Zofteis on 2008-12-19
> **Ringi said:**
> Yes

If you have a TV cable connected to TV card and a 15 cm wire on the other end,
place it it in the window pointed up 90°, have a digital antenna :)

:D Okay i will give it a try tomorrow, cause now i need some sleep!
So there won't be a opportunity to get analogue TV to get work?

Thanks for your help!!!!

---

### Post by xc3RnbFO8P on 2008-12-20
> When i start Kaffeine a message appears:"Can't bind info socket!!!
I Kaffeine Setting>DVB Client and un-checked "enable DVB client

Install TVtime from Add/Remove (all available application)
and try to scan channels.

---

### Post by Zofteis on 2008-12-20
Well i did what you've said, but if i want to start TvTime a black window opens which closes after a second, and then nothing happens...
Then i took a short look at the tvtime webside and found this:

1. tvtime not starting when using the Radeon FireGL drivers

With the Radeon FireGL drivers, the user has the option of having OpenGL use an overlay surface, giving 3D graphics without tearing, or video overlay surfaces for multimedia players. This can be set in the Device section for the fglrx of your /etc/X11/XF86Config-4 using:

    Option  "VideoOverlay"       

or

    Option  "OpenGLOverlay"      

To use tvtime, you MUST select VideoOverlay instead of OpenGLOverlay. The tvtime bug report on this is bug 787142.


Maybe this causes my bug because I'm using an ATI card...
I went to /etc/X11/ , but there isn't a XF86Config-4...
I only find xorg.conf! Is this the same one????
Inside it i changed:
Option 		"OpenGLOverlay"		"on"
to
Option 		"OpenGLOverlay"		"off"

and i've added the line:
Option          "VideoOverlay"          "on"   

but the problem starting TVtime remains....
Do i have to do anything to before the new settings start working?

Kind regards

Edit:
If i try to start TVTime with console it says:
Starte tvtime 1.0.2.
Lese Konfiguration aus /etc/tvtime/tvtime.xml
Lese Konfiguration aus /home/markus/.tvtime/tvtime.xml
markus@markus-desktop:~$ xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

---

### Post by xc3RnbFO8P on 2008-12-20
Do you have Compiz enabled?

---

### Post by Zofteis on 2008-12-20
Do you mean this?
[http://ubuntuforums.org/showthread.php?t=766683&highlight=Compiz](http://ubuntuforums.org/showthread.php?t=766683&highlight=Compiz)

Yeah i enabled it now, and i reinstalled my ATI driver with the help of this guide....
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

but somehow the problem remains.....

Kind regards

---

### Post by xc3RnbFO8P on 2008-12-20
Sorry no, disable it.
In >System> Preferences> appearance> Visual Effects> None

---

### Post by Zofteis on 2008-12-20
Okay i disabled it, but it didn't change something...
Still the same error while starting tvtime...
But i don't know why i don't have "hardware YUY2 overlay support" because my ati driver seems to work fine...

Kind regards

---

### Post by xc3RnbFO8P on 2008-12-21
Try to install **Gatos** in Synaptic Package Manager.

---

### Post by Zofteis on 2008-12-21
Well finally Tv Time was able to start without Gatos...
But i haven't got a signal....
And i can't change the signal source...
In tvtime the signal ist named televsion and i cannot choose another one...
Tvtime only hangs für a short time and the source remains the same one...

Kind regards

---

### Post by xc3RnbFO8P on 2008-12-21
Can you **reset all channels as active** and scan again?

---

### Post by Zofteis on 2008-12-21
Yeah i did so, but it didn't work...
Is this programm for anlague TV or for DVB-T ?

---

### Post by xc3RnbFO8P on 2008-12-21
> Is this programm for anlague TV or for DVB-T ?
Analog.

---

### Post by Zofteis on 2008-12-21
strange...
Somehow he does not give me the possibility to change the source...
Well i´ll look at this problem, but i don´t think that i´ll be possible to fix it...

Kind regards

---

### Post by Zofteis on 2008-12-22
Well i have another idea...
dmesg always shows me:
[   53.344889] saa7133[0]: subsystem: 1461:f01d, board: Avermedia Super 007 [card=117,autodetected]

But this is the DVB-t card...
The card i need is number 149...
Isn't there a way to force the kernel to load card 149??

Kind regards

---

### Post by xc3RnbFO8P on 2008-12-22
It should work with card=117
**sudo modprobe saa7134 card=117**
then start TVtime
or
**sudo modprobe saa7134 card=149**

---

### Post by Zofteis on 2008-12-22
Well i tried both options a few times now and they didn't work...
I guess the problem is that only the AverTv Super 007 (analog only) and the AverTv Super 007 (DvB-t pnly) only is supported! The Hybrid version does not seem to work...
Maybe v4l will make it work in the future...
But thanks for your help!!!!!

Kind regards

---

