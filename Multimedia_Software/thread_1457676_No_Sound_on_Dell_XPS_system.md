---
title: "No Sound on Dell XPS system"
date: 2010-04-18
forum: Multimedia Software
---

### Post by kingjungle on 2010-04-18
Hello,
I recently installed Ubuntu on my computer.  Everything is working well but there is no sound. Can someone please help. Here is some information regarding the system:

[B]Installed Ubuntu 9.10
[/B]
[B]Upgraded to Alsa 1.0.22.1

[/B]made sure volumes are all the way up using[B] alsamixer

$ cat /proc/asound/card0/codec#* | grep Codec[/B]
Codec: SigmaTel STAC9227

[B]$ cat /proc/asound/cards
[/B] 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdffdc000 irq 29
 1 [camera         ]: USB-Audio - USB camera
                      USB camera at usb-0000:00:1d.1-2, full speed

**$ aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

**$ aplay -L**
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Intel
    HDA Intel, STAC92xx Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Digital
    IEC958 (S/PDIF) Digital Audio Output

Thanks 
Kris

---

### Post by lidex on 2010-04-18
First did you run through this page:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats") Make sure to install the alsa-backports.

Second - which of these matches your configuration:
```
STAC9227/9228/9229/927x
=======================
  ref		Reference board
  ref-no-jd	Reference board without HP/Mic jack detection
  3stack	D965 3stack
  5stack	D965 5stack + SPDIF
  5stack-no-fp	D965 5stack without front panel
  dell-3stack	Dell Dimension E520
  dell-bios	Fixes with Dell BIOS setup
  volknob	Fixes with volume-knob widget 0x24
  auto		BIOS setup (default)

```
Third - Have you checked the Dell forum:
[http://ubuntuforums.org/forumdisplay.php?f=342]("http://ubuntuforums.org/forumdisplay.php?f=342")

---

### Post by kingjungle on 2010-04-20
I ran through this page:
[https://wiki.ubuntu.com/DebuggingSou.../KarmicCaveats](https://wiki.ubuntu.com/DebuggingSou.../KarmicCaveats) and made sure i installed the alsa-backports. Everything seems to be fine.
**$ uname -r**
2.6.31-20-generic

My sound Card:
cat /proc/asound/card0/codec#* | grep Codec
Codec: SigmaTel STAC9227

I ran **gstreamer-properties **and changed Plugin default to  ALSA -Advanced Linux Sound Architecture 
and device as STAC922XX Digital
When I tried to test the settings, it said:** "**Could not open audio device for playback. Device is being used by another application"

---

### Post by Yellow Pasque on 2010-04-20
> **kingjungle said:**
> I ran **gstreamer-properties **and changed Plugin default to  ALSA -Advanced Linux Sound Architecture 
and device as STAC922XX Digital. When I tried to test the settings, it said:** "**Could not open audio device for playback. Device is being used by another application"

You should set gstreamer to pulseaudio (unless you've removed pulseaudio). Otherwise, you'll get messages similar to the one you got while your ALSA application and Pulseaudio grapple for the ALSA hardware device.

---

### Post by lidex on 2010-04-20
Try this. Open this file for editing:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Add this line at the bottom:
```
options snd-hda-intel model=dell-bios
```
Save. Close. Reboot. Check alsamixer.

---

### Post by kingjungle on 2010-04-21
> **lidex said:**
> Try this. Open this file for editing:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```Add this line at the bottom:
```
options snd-hda-intel model=dell-bios
```Save. Close. Reboot. Check alsamixer.


I am able to get audio through my headphones but not through the sound system that is connected to the computer through an optical cable.

---

### Post by kingjungle on 2010-04-21
here is the output I get when I run speaker test
$ speaker-test -Dplug:surround51 -c6 -l1 -twav

speaker-test 1.0.22

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 5440
Period size range from 32 to 2720
Using max buffer size 5440
Periods = 4
was set period_size = 1088
was set buffer_size = 5440
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE
Time per period = 8.522899

I do not get any sound from my 5.1 surround sound.  I get sound only from the headphone jack.

---

### Post by kingjungle on 2010-04-21
Partially solved
I now get sound from Front Left and Right channels only.  I do not get 5.1 surround sound.

This what I did
$ aplay -l
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ sudo nano /etc/modules
added snd-STAC92xx to the end of the file

---

### Post by Yellow Pasque on 2010-04-21
Pulseaudio is using the ALSA hardware device. Either temporarily stop/suspend pulseaudio or route ALSA apps through it: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

EDIT: snd-STAC92xx is not an alsa kernel module. The driver for your card is snd-hda-intel, which looks to already load automatically.

---

### Post by kingjungle on 2010-04-22
> **Temüjin said:**
> Pulseaudio is using the ALSA hardware device. Either temporarily stop/suspend pulseaudio or route ALSA apps through it: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

EDIT: snd-STAC92xx is not an alsa kernel module. The driver for your card is snd-hda-intel, which looks to already load automatically.

I went through the site and made recommended changes.  I still get stereo sound and not 5.1 surround sound.  

Any ideas ?

---

### Post by lidex on 2010-04-22
Have a look here:
[http://ubuntuforums.org/showthread.php?t=877811]("http://ubuntuforums.org/showthread.php?t=877811")

---

