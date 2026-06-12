---
title: "question about Hauppage WinTV-HVR 950Q"
date: 2009-08-03
forum: Multimedia Software
---

### Post by cptrohn on 2009-08-03
Hi I just got this USB tv tuner and am trying to get it to work using TV time television viewer...

I am only using the antenna that came with the tv tuner and when I open up the TV time package I just get a blue screen that says No Signal at the top middle of the screen, no video source at the top right hand corner under the current time and at the bottom of the screen I get an error message of ```
Cannot open capture device /dev/video0
```

So since I am completely new to this what exactley do I need to do to get this device opened to be able to watch TV on the PC?  I guess I could try to use wine with the software that came included if all else fails but I really want it to work through ubuntu.

---

### Post by cptrohn on 2009-08-03
Bump..

Man I actually just ordered Vista rescue discs if I can't get it running in Ubuntu, I guess I will go back to dual booting.... Wasn't wanting to do that.

---

### Post by borisz264 on 2009-10-06
I got it running by installing the firmware here:

[http://www.linuxtv.org/wiki/index.php/Xceive_XC5000/XC4000#How_to_Obtain_the_Firmware](http://www.linuxtv.org/wiki/index.php/Xceive_XC5000/XC4000#How_to_Obtain_the_Firmware)

I got sound to work by opening TVtime with this script (paste into a text file, set it to open with "sh", and just double-click):

#! /bin/sh

tvtime | arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -


you may need to install arecord and aplay if they are not installed. There IS a slight audio delay.

---

### Post by zebtonson on 2009-10-20
I used a combination of tvtime, and jackd.  I selected the 950q's audio in port and piped it to the speakers.   I was running ubuntu 9.10 beta, so it was running using v4l v2 to create a video0 automatically.  


best of luck.

---

### Post by markackerman8@gmail.com on 2010-04-09
Has anyone had any success with this card and MythTV when watching livetv from an analog cable source (NTSC)??  soooo frustrated!!!

---

### Post by WinterRain on 2010-04-09
> **markackerman8@gmail.com said:**
> Has anyone had any success with this card and MythTV when watching livetv from an analog cable source (NTSC)??  soooo frustrated!!!

During mythtv setup, are you sure you chose the right firmware from the drop down list? Did you install the firmware linked above?

---

### Post by markackerman8@gmail.com on 2010-04-09
Thanks soo much for a response ... new optimism!!!

OK I will answer y0our questions as best as i can, but please remember I am sadly ignorant of many details (struggling for 1 mo. with this card and 1 year with my hvr-1500c (gave up on it for analog).

1/ From the dropdown list I chose "Analog V4l Capture Card", dev/video1, and it shows "Probed Information" as "Hauppaugge HVR-950Q [au0828]", so I assume it is right.

2/w.r.t. the firmware I have downloaded and compiled the latest from v4l-dvb.  and here is my dmesg that may confirm it and help troubleshoot. 

Thank you very much for any help troubleshooting this! :)

19.822691] tveeprom 0-0050: Hauppauge model 72101, rev B3F0, serial# 6793570
[   19.822699] tveeprom 0-0050: MAC address is 00-0D-FE-67-A9-62
[   19.822705] tveeprom 0-0050: tuner model is Xceive XC5000 (idx 150, type 76)
[   19.822711] tveeprom 0-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   19.822717] tveeprom 0-0050: audio processor is AU8522 (idx 44)
[   19.822721] tveeprom 0-0050: decoder processor is AU8522 (idx 42)
[   19.822727] tveeprom 0-0050: has no radio, has IR receiver, has no IR transmitter
[   19.822732] hauppauge_eeprom: warning: unknown hauppauge model #72101
[   19.822736] hauppauge_eeprom: hauppauge eeprom: model=72101
[   19.840159] au8522 0-0047: creating new instance
[   19.840161] au8522_decoder creating new instance...
[   19.951461]   alloc irq_desc for 22 on node -1
[   19.951465]   alloc kstat_irqs on node -1
[   19.951474] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   19.951558] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   20.305151] tuner 0-0061: chip found @ 0xc2 (au0828)
[   20.611022] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input11
[   20.798873] xc5000: xc5000_attach(0-0061)
[   20.798877] xc5000 0-0061: creating new instance
[   20.803810] xc5000: Successfully identified at address 0x61
[   20.803814] xc5000: Firmware has not been loaded previously
[   20.804237] au8522 0-0047: attaching existing instance
[   20.811747] xc5000: xc5000_attach(0-0061)
[   20.811750] xc5000 0-0061: attaching existing instance
[   20.816420] xc5000: Successfully identified at address 0x61
[   20.816422] xc5000: Firmware has not been loaded previously
[   20.816425] DVB: registering new adapter (au0828)
[   20.816428] DVB: registering adapter 0 frontend 0 (Auvitek AU8522 QAM/8VSB Frontend)...
[   20.818900] Registered device AU0828 [Hauppauge HVR950Q]
[   20.818981] usbcore: registered new interface driver au0828
[   20.837187] xc5000: xc5000_sleep()
[   21.552816] usbcore: registered new interface driver snd-usb-audio

[   40.034460] xc5000: xc5000_is_firmware_loaded() returns False id = 0x2000
[   40.039196] xc5000: xc5000_is_firmware_loaded() returns False id = 0x2000
[   40.039199] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
[   40.039204] usb 1-3: firmware: requesting dvb-fe-xc5000-1.6.114.fw
[   40.069452] xc5000: firmware read 12401 bytes.
[   40.069455] xc5000: firmware uploading...
[   40.069457] xc5000: xc5000_TunerReset()
[   43.189500] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   47.060030] xc5000: firmware upload complete...
[   47.060046] xc5000: xc_initialize()

[   51.380042] xc5000: xc5000_set_analog_params() frequency=6400 (in units of 62.5khz)
[   51.380049] xc5000: xc_SetSignalSource(1) Source = CABLE
[   53.673929] xc5000: xc_SetTVStandard(0x8020,0x0400)
[   53.673933] xc5000: xc_SetTVStandard() Standard = M/N-NTSC/PAL-BTSC

---

### Post by markackerman8@gmail.com on 2010-04-15
> **markackerman8@gmail.com said:**
> Thanks soo much for a response ... new optimism!!!
IR transmitter
[   19.822732] hauppauge_eeprom: warning: unknown hauppauge model #72101
[   19.822736] hauppauge_eeprom: hauppauge eeprom: model=72101
/PAL-BTSC

I HAVE ELIMINATED THIS ERROR by purchasing a newer HVR-950Q - model #72001.  But still no luck with analog cable and MythTV --- HELP!!!!!!!

Please!!!!!

---

### Post by nacho32 on 2010-04-15
not to go off topic but have you tried Kaffeine ?
[http://kaffeine.kde.org/?q=download](http://kaffeine.kde.org/?q=download)
I found this one to work out of the box without having to spend more time configuring it then watching it.

---

### Post by markackerman8@gmail.com on 2010-04-15
Thanks so much for responding Nacho32...getting definitely frustrated trying so hard to get over this final windows hurtle.  But I am afraid I have tried Kaffeine, and it only works for DIGITAL not analog in any way, sadly.  Plus PVR functionality is what I am looking for.  TVtime works for live viewing.  Thanks anyway though.

Anyone else have any ideas for a very tired out troubleshooter??

---

### Post by mlord on 2010-11-16
*(pardon the duplication, but I'm trying to get this info spread widely enough to help the most people)*

There's a trick (or several) to getting analog audio from the HVR-950Q in MythTV, probably required due to bugs in the latter.

The rest of this post assumes you have already figured out how to get the video part of analog recordings to work (720x480 in all profiles, 48000 audio, RTJPEG at max quality, and create a single recording group to hold both the analog and digital halves of the 950Q).

MythTV seems to only work properly with audio recording when the OSS ("Open Sound System") audio driver interface is used. It fails miserably and randomly when attempting to use the newer ALSA ("Advanced Linux Sound Architecture") driver interfaces.

So.. if your distro provides /dev/dsp1 (from OSS), then use that as the audio input device when configuring the HVR-950Q as a capture card.

If it does not provide it, then do modprobe snd-pcm-oss and check for /dev/dsp* again. If the modprobe command fails, then you will have to reconfigure/rebuild the Linux kernel to get that missing feature.

The snd-pcm-oss module is simply a glue layer, so that old-style OSS interfaces can be used (by MythTV) with the newer ALSA drivers underneath. This is the only method I've found that works for analog audio capture from the 950Q in MythTV. Other apps work fine, of course.

Cheers

---

