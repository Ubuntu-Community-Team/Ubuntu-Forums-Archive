---
title: "NO SOUND: ubuntu 10.10 + Alsa 1.0.25 + integrated Realtek ALC883 (SPDIF)"
date: 2012-03-31
forum: Multimedia Software
---

### Post by eraygao on 2012-03-31
Hi All,

Need help to get digital SPDIF working. Fairly new to ubuntu/linux. Installed Ubuntu 10.10,  sound card not shown in 'Sound Settings' from the speaker icon (pulseaudio?). Devices shown are:

HD48x0 audio Digital Stereo (HDMI)
Interal Audio Analogue Stere

Motherboard:

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: Gigabyte Technology Co., Ltd.
    Product Name: 965P-S3
    Version: 
    Serial Number: 
    UUID: 00000000-0000-0000-0000-0016E685A81A
    Wake-up Type: Power Switch
    SKU Number: 
    Family:

Tried to install lasted Realtek drivers for linux

[ftp://WebUser:r3iZ6vJI@207.232.93.28/pc/audio/LinuxPkg_5.17rc1.tar.bz2](ftp://WebUser:r3iZ6vJI@207.232.93.28/pc/audio/LinuxPkg_5.17rc1.tar.bz2)

and installed latest Alsa 1.0.25. Now devices showing properly for device list and aplay, however, still not shown in sound settings:

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Intel
    HDA Intel, ALC883 Analog
    Default Audio Device
sysdefault:CARD=Intel
    HDA Intel, ALC883 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
[B][COLOR=Red]iec958:CARD=Intel,DEV=0
    HDA Intel, ALC883 Digital
    IEC958 (S/PDIF) Digital Audio Output[/COLOR][/B]
hdmi:CARD=HDMI,DEV=0
    HDA ATI HDMI, HDMI 0
    HDMI Audio Output


Notice iec958:CARD=Intel,DEV=0 is the one I am trying to use.....

Have tried to modify /etc/modprobe.d/alsa-base.conf by adding:

options snd-hda-intel model=auto

in the end (tried other models from the list ([http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt))


Have tried to uninstall pulseaudio according to:

[http://ubuntuforums.org/showthread.php?t=1733323&page=2](http://ubuntuforums.org/showthread.php?t=1733323&page=2)

[I][SIZE=1]1. I used Linux Mint 10.10 (GNOME) Live DVD-- Guess it is Maverick makeover

2. I removed pulse audio (apt-get remove pulseaudio)

3. From terminal type gconf-editor

4. Go to System --->gstreamer---->0.10--->default

5. Change audiosink value to "alsasink"

6.change musicaudiosink to "alsasink"

(Terminal as Root)

7. lsof /dev/snd/*

8.. Kill "****" (the respective PIDs)

9. rmmod snd-hda-intel <Enter>
       modprobe snd-hda-intel model=clevo-m540r 

(Luckily this model worked for my card ..Else try to substitute different models in "model=" line as suggested in ALSA matrix  [http://www.kernel.org/doc/Documentat...dio-Models.txt]("http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt") 

(  Repeat steps 7 to 11 till u get sound)

10 make sure all channels are unmuted by running "alsamixer" (press"M" to toggle and raise the volume)[/SIZE][/I]



After restart, now the speaker icon is gone, in sound in system, there is no devices any more.

Note also in alsamixer, the sound card is shown properly and everything is unmuted.


Anyone can provide some hints please?

---

### Post by eraygao on 2012-03-31
Please find the attached system information for Alsa project.

[http://www.alsa-project.org/db/?f=fd408b7de9f2c759bf8dd9c23db9dcc143eb07d3](http://www.alsa-project.org/db/?f=fd408b7de9f2c759bf8dd9c23db9dcc143eb07d3)

---

### Post by eraygao on 2012-03-31
Actually it plays sound with aplay...

Solved....................................................


$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
$ aplay -D plughw:0,1 /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono

---

### Post by eraygao on 2012-03-31
Problem solved. Please close thread.

---

