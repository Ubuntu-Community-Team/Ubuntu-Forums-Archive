---
title: "Logitech Webcam built in Mic Issues"
date: 2008-08-27
forum: Multimedia Software
---

### Post by quaizar on 2008-08-27
Hello,

I am a newcomer to Ubuntu and have struggled with getting all sound devices to work.  I was able to get my x-fi working by following another post on the forums so I am hoping someone can help with this issue.  I have been trouble shooting this for at least 10 hours so I have searched for answers prior to posting.

I am new to linux so bear with me.

I ran oss test which did show a usb sound device:

*** Scanning sound adapter #1 ***
/dev/oss/usb046d09a1-1/pcmin0 (audio engine 6): USB sound device rec
- Skipping input only device

The device also shows through wine in Vent.  However it doesn't show in the sound capture list under preferences.

The camera portion works just fine and everything works in xp so I did rule out the camera/mic going dead.

I would just use a mic, but as I mentioned I have a x-fi sound card so from what I have read that is not an option.

Your help in this matter would be greatly appreciated and if I need to post more info just let me know what line to enter and I will paste the results.

Thanks

---

### Post by markbuntu on 2008-08-27
Are you using OSS4?

If so, you need to ask Temujin over on the OSS4 thread. He is usually pretty good at helping people with OSS4 problems.

---

### Post by quaizar on 2008-08-27
I sure am, and I'll include my version.  I'll see if I can get him to take a look.

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"

more info: i'd settle for the regular mic to work to heh :D

Selected mixer 0/Sound Blaster X-Fi (SB046x/067x/076x)
Known controls are:
play [<leftvol>:<rightvol>] (currently 14.4:14.4 dB)
rec [<leftvol>:<rightvol>] (currently 14.4:14.4 dB)
recsrc <mic|line|video|aux|none> (currently mic)
vmix0-enable ON|OFF (currently ON)
vmix0-rate <decimal value> (currently 96000) (Read-only)
vmix0-src <Fast|Low|Medium|High|High+|Production|OFF> (currently Fast)
vmix0-vol <monovol> (currently 25.0 dB)
vmix0-out1 [<leftVU>:<rightVU>] (currently 0:0) (Read-only)
vmix0-in [<leftVU>:<rightVU>] (currently 0:0) (Read-only)
vmix0-out.pcm2 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0-out2 [<leftVU>:<rightVU>] (currently 0:0) (Read-only)
vmix0-out.pcm3 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0-out3 [<leftVU>:<rightVU>] (currently 0:0) (Read-only)
vmix0-out.pcm4 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0-out4 [<leftVU>:<rightVU>] (currently 0:0) (Read-only)
vmix0-out.pcm5 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0-out5 [<leftVU>:<rightVU>] (currently 0:0) (Read-only)


Version info: OSS 4.1 (b rc1/200808260655) (0x00040090) 
Hg revision: changeset: 417:8466e8481f30, tag: tip, date: Thu Aug 21 23:55:37 2008 +0300, summary: Changed warning printed by vmix_attah_audiodev() to be more informative
Platform: Linux/i686 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 (portal)

Number of audio devices:	3
Number of audio engines:	7
Number of mixer devices:	2


Device objects
 0: osscore0 OSS core services
 1: oss_sbxfi0 Sound Blaster X-Fi (SB046x/067x/076x) interrupts=205218 (205218)
    PCI device 1102:0005, subdevice 1102:0021
 2: oss_usb0 USB audio core services
 3: usb046d09a1-0 USB sound device
 4: usb046d09a1-1 USB sound device


Mixer devices
 0: Sound Blaster X-Fi (SB046x/067x/ (Mixer 0 of device object 1)
 1: USB sound device (Mixer 0 of device object 3)

Audio devices
Sound Blaster X-Fi (SB046x/067x/076x) output  /dev/oss/oss_sbxfi0/pcm0  (device index 0)
Sound Blaster X-Fi (SB046x/067x/076x) input  /dev/oss/oss_sbxfi0/pcmin0  (device index 1)
USB sound device rec              /dev/oss/usb046d09a1-1/pcmin0  (device index 2)

---

### Post by quaizar on 2008-08-28
bump

---

### Post by Crafty Kisses on 2008-08-28
Post the results of > lsusb

---

### Post by quaizar on 2008-08-29
Bus 003 Device 003: ID 046d:09a1 Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 001 Device 001: ID 0000:0000

---

### Post by quaizar on 2008-08-29
I read through other posts in the forums:

aplay -l shows : no soundcards found

Not sure if that is because my creative is using oss or not. Because ossinfo -a shows 

Audio devices
Sound Blaster X-Fi (SB046x/067x/076x) output  /dev/oss/oss_sbxfi0/pcm0  (device index 0)
Sound Blaster X-Fi (SB046x/067x/076x) input  /dev/oss/oss_sbxfi0/pcmin0  (device index 1)
USB sound device rec              /dev/oss/usb046d09a1-1/pcmin0  (device index 2)


I also saw in other posts people saying they just had to change their sound capture device in sound preferences, however my SB X-fi doesn't show in the list and neither does the usb webcam mic.  Hope this gives more info to be able to help.  

Again getting either to work would be awesome :D

---

### Post by quaizar on 2008-08-30
well i managed to get sound in ventrilo from my plug in mic but it is distorted but its a step (doesn't sound like me, sounds like a chirp), still need someone to look at this.

---

### Post by KosmoZ on 2008-10-08
I have the exact same problem. I'm using OSS to make my SoundBlaster X-Fi work, and I'm trying to setup my Logitech Webcam Pro 4000. I've succeeded with the video but not with the mic, even though it appears in ossinfo and ossxmix (not muted). 

Logitec Quickcam Pro 4000 (mic) rec  /dev/oss/usb046d08b2-1/pcmin0  (device index 2)

The microphone appears nowhere in the drop down menus in Skype and Audacity.. I'm not too sure what to try here.

Bloody Dell Dimension 9150 and its unsupported hardware...

---

