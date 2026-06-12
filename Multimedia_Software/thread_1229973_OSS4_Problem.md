---
title: "OSS4 Problem"
date: 2009-08-02
forum: Multimedia Software
---

### Post by plzdontkillme11 on 2009-08-02
Hi,

I recently replaced ALSA with OSS4. It has been working perfectly, until this morning. There is no more sound on my laptop. I've looked at ossmix and looked at all of my sound preferences, and all look normal. As of now, I have no idea how to fix this. I've also tried restarting, with no success.

I'm using Ubuntu 9.04. Also, I'm a newbie when it comes to Linux, so you'll have to walk me through the steps :). 

Thanks in advance!

---

### Post by plzdontkillme11 on 2009-08-02
Bump.

---

### Post by plzdontkillme11 on 2009-08-02
Bump.

---

### Post by igorzwx on 2009-08-02
you should restart OSS4 perhaps
wait a moment

or ask Martin

it might happen after update, I presume

---

### Post by igorzwx on 2009-08-02
First try solution, proposed by Martin
[http://ubuntuforums.org/showthread.php?t=1227948](http://ubuntuforums.org/showthread.php?t=1227948)

Are the drivers loaded?

**lsmod | grep oss**

**sudo service oss restart**

will restart just oss.
 		                   		  		  		 		 			 				__________________
				Think for yourself. Don't let others do the thinking for you. 
[guide to switch to ossv4]("http://martinbaselier.wordpress.com/2009/07/25/how-to-switch-from-alsa-to-ossv4/") - [same guide on this forum]("http://ubuntuforums.org/showthread.php?t=1217259") - [comprehensive multimedia guide]("http://ubuntuforums.org/showthread.php?t=766683") - [optimizing firefox]("http://ubuntuforums.org/showthread.php?t=1193567")


THEN try this:

on Terminal type:

osstest


THEN

ossmix


ossinfo -v3

---

### Post by plzdontkillme11 on 2009-08-02
Ty, I'll check that out.

---

### Post by igorzwx on 2009-08-02
no problem

read my post above

---

### Post by plzdontkillme11 on 2009-08-02
I tried restarting, and this is what I got: 

[B]Stopping Open Sound System: Cannot unload the OSS driver modules
Starting Open Sound System: OSS is already loaded.

[/B]Still no sound, unfortunately[B].
[/B]

---

### Post by igorzwx on 2009-08-02
Execute these commands and paste results here 
(osstest should produce sound)

on Terminal:

**lsmod | grep oss**


THEN:


osstest


THEN

ossmix


ossinfo -v3

---

### Post by plzdontkillme11 on 2009-08-02
vignesh@vignesh-laptop:~$ lsmod | grep oss
oss_usb               117132  2 
oss_hdaudio           143076  4 
osscore               561844  4 oss_usb,oss_hdaudio



vignesh@vignesh-laptop:~$ osstest
Sound subsystem and version: OSS 4.1 (b 1052/200903240610) (0x00040100)
Platform: Linux/i686 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009

*** Scanning sound adapter #-1 ***
/dev/oss/oss_hdaudio0/pcm0 (audio engine 0): HD Audio play speaker
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47986.00 Hz (-0.03%)> 
/dev/oss/oss_hdaudio0/pcm1 (audio engine 1): HD Audio play headphone
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47986.00 Hz (-0.03%)> 
/dev/oss/oss_hdaudio0/pcm2 (audio engine 2): HD Audio play pcm
- Performing audio playback test... 
  <left> Device returned error: Input/output error
/dev/oss/oss_hdaudio0/pcm3 (audio engine 3): HD Audio play pcm
- Performing audio playback test... 
  <left> Device returned error: Input/output error
/dev/oss/oss_hdaudio0/pcm4 (audio engine 4): HD Audio play pcm
- Performing audio playback test... 
  <left> Device returned error: Input/output error
/dev/oss/oss_hdaudio0/pcm5 (audio engine 5): HD Audio play pcm
- Performing audio playback test... 
  <left> Device returned error: Input/output error
/dev/oss/oss_hdaudio0/pcm6 (audio engine 6): HD Audio play pcm
- Performing audio playback test... 
  <left> Device returned error: Input/output error
/dev/oss/oss_hdaudio0/pcm7 (audio engine 7): HD Audio play pcm
- Performing audio playback test... 
  <left> Device returned error: Input/output error
/dev/oss/oss_hdaudio0/pcmin0 (audio engine 8): HD Audio rec select
- Skipping input only device
/dev/oss/oss_hdaudio0/pcmin1 (audio engine 9): HD Audio rec select
- Skipping input only device

*** Some errors were detected during the tests ***


vignesh@vignesh-laptop:~$ ossmix
Selected mixer 0/High Definition Audio ALC268
Known controls are:
jack.int-speaker.mode <mix|input> (currently mix)
jack.int-speaker.mute ON|OFF (currently ON)
jack.int-speaker.speaker [<leftvol>:<rightvol>] (currently 63.9:63.9 dB)
jack.int-speaker.speaker-mute ON|OFF (currently OFF)
jack.fp-black.mode1 <mix|input> (currently mix)
jack.fp-black.mute1 ON|OFF (currently OFF)
jack.fp-black.headphone [<leftvol>:<rightvol>] (currently 63.9:63.9 dB)
jack.fp-black.mute.headphone ON|OFF (currently ON)
jack.fp-black.mute.speaker ON|OFF (currently OFF)
jack.fp-black.mode2 <speaker|input> (currently speaker)
jack.fp-black [<leftvol>:<rightvol>] (currently 39.9:39.9 dB)
jack.fp-black.mute2 ON|OFF (currently OFF)
jack.int-mic [<leftvol>:<rightvol>] (currently 39.9:39.9 dB)
record.select.select1 [<leftvol>:<rightvol>] (currently 46.4:46.4 dB)
record.select.select2 <speaker|int-mic> (currently speaker)
record.select.select3 [<leftvol>:<rightvol>] (currently 46.4:46.4 dB)
record.select.select4 <speaker|int-mic> (currently speaker)
vmix0-enable ON|OFF (currently ON)
vmix0-rate <decimal value> (currently 48000) (Read-only)
vmix0-channels <Stereo|Multich> (currently Multich)
vmix0-src <Fast|Low|Medium|High|High+|Production|OFF> (currently High+)
vmix0-outvol <monovol> (currently 25.0 dB)
vmix0-invol <monovol> (currently 25.0 dB)
vmix0.pcm10 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm11 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm12 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm13 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)

vignesh@vignesh-laptop:~$ ossinfo -v3 
Version info: OSS 4.1 (b 1052/200903240610) (0x00040100) 
Platform: Linux/i686 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 (vignesh-laptop)

Number of audio devices:    10
Number of audio engines:    14
Number of mixer devices:    1


Device objects
 0: osscore0 OSS core services
 1: oss_hdaudio0 Intel HD Audio interrupts=517552 (517561)
    HD Audio controller Intel HD Audio
    Vendor ID    0x8086293e
    Subvendor ID 0x1179ff66
     Codec  0: ALC268 (0x10ec0268/0x1179ff66)
     Codec  1: Unknown (0x11c11040)
 2: oss_usb0 USB audio core services


Mixer devices
 0: High Definition Audio ALC268 (Mixer 0 of device object 1)
    Device file /dev/oss/oss_hdaudio0/mix0, Legacy device /dev/mixer0
    Priority: 10
    Caps: 
    Device handle: PCIff661179-0000:00:1b.0-mx01
    Device priority: 10


Audio devices
HD Audio play speaker             /dev/oss/oss_hdaudio0/pcm0  (device index 0)
    Legacy device /dev/dsp0
    Caps: DUPLEX TRIGGER MMAP 
    Modes: IN/OUT 
      Out engine  1: 0/HD Audio play speaker
                     Available for use 
      Engine      2: 10/HD Audio play speaker (vmix)
                     Available for use 
      Engine      3: 11/HD Audio play speaker (vmix)
                     Available for use 
      Engine      4: 12/HD Audio play speaker (vmix)
                     Available for use 
      Engine      5: 13/HD Audio play speaker (vmix)
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_S32_LE    - 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_S32_LE    - 32 bit signed little endian
    Device handle: PCIff661179-0000:00:1b.0-au01
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 8
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play headphone           /dev/oss/oss_hdaudio0/pcm1  (device index 1)
    Legacy device /dev/dsp1
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 1/HD Audio play headphone
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_S32_LE    - 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_S32_LE    - 32 bit signed little endian
    Device handle: PCIff661179-0000:00:1b.0-au02
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play pcm                 /dev/oss/oss_hdaudio0/pcm2  (device index 2)
    Legacy device /dev/dsp2
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 2/HD Audio play pcm
                     Available for use 
    Input formats (0x00000000):
    Output formats (0x00000000):
    Device handle: PCIff661179-0000:00:1b.0-au03
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 500000 - 0
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play pcm                 /dev/oss/oss_hdaudio0/pcm3  (device index 3)
    Legacy device /dev/dsp3
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 3/HD Audio play pcm
                     Available for use 
    Input formats (0x00000000):
    Output formats (0x00000000):
    Device handle: PCIff661179-0000:00:1b.0-au04
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 500000 - 0
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play pcm                 /dev/oss/oss_hdaudio0/pcm4  (device index 4)
    Legacy device /dev/dsp4
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 4/HD Audio play pcm
                     Available for use 
    Input formats (0x00000000):
    Output formats (0x00000000):
    Device handle: PCIff661179-0000:00:1b.0-au05
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 500000 - 0
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play pcm                 /dev/oss/oss_hdaudio0/pcm5  (device index 5)
    Legacy device /dev/dsp5
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 5/HD Audio play pcm
                     Available for use 
    Input formats (0x00000000):
    Output formats (0x00000000):
    Device handle: PCIff661179-0000:00:1b.0-au06
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 500000 - 0
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play pcm                 /dev/oss/oss_hdaudio0/pcm6  (device index 6)
    Legacy device /dev/dsp6
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 6/HD Audio play pcm
                     Available for use 
    Input formats (0x00000000):
    Output formats (0x00000000):
    Device handle: PCIff661179-0000:00:1b.0-au07
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 500000 - 0
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play pcm                 /dev/oss/oss_hdaudio0/pcm7  (device index 7)
    Legacy device /dev/dsp7
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 7/HD Audio play pcm
                     Available for use 
    Input formats (0x00000000):
    Output formats (0x00000000):
    Device handle: PCIff661179-0000:00:1b.0-au08
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 500000 - 0
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio rec select               /dev/oss/oss_hdaudio0/pcmin0  (device index 8)
    Legacy device /dev/dsp8
    Caps: DUPLEX TRIGGER MMAP 
    Modes: IN/OUT 
      In engine   1: 8/HD Audio rec select
                     Available for use 
      Engine      2: 10/HD Audio play speaker (vmix)
                     Available for use 
      Engine      3: 11/HD Audio play speaker (vmix)
                     Available for use 
      Engine      4: 12/HD Audio play speaker (vmix)
                     Available for use 
      Engine      5: 13/HD Audio play speaker (vmix)
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_S32_LE    - 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_S32_LE    - 32 bit signed little endian
    Device handle: PCIff661179-0000:00:1b.0-au09
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 96000 (44100,48000,96000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio rec select               /dev/oss/oss_hdaudio0/pcmin1  (device index 9)
    Legacy device /dev/dsp9
    Caps: TRIGGER MMAP 
    Modes: INPUT  
      In engine   1: 9/HD Audio rec select
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_S32_LE    - 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_S32_LE    - 32 bit signed little endian
    Device handle: PCIff661179-0000:00:1b.0-au10
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 96000 (44100,48000,96000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

vignesh@vignesh-laptop:~$

---

### Post by plzdontkillme11 on 2009-08-02
Sorry about the random smileys >.>

---

### Post by igorzwx on 2009-08-02
Did you hear sound?

It is 03:27 here

I sent the message to Martin
Let us continue tomorrow

---

### Post by plzdontkillme11 on 2009-08-02
Nope, no sound. :\

Ok, that's no problem. It's 8:30 PM here... will you be able to help me around 7 PM (your time)?

Thanks for the help so far!

---

### Post by igorzwx on 2009-08-02
Try reboot too.

I have not here HDA
Martin has.

I think some 7 hours later,
he may tell you something

read this too:
[7.1 Troubleshooting HDAudio devices]("http://wiki.archlinux.org/index.php/OSS#Troubleshooting_HDAudio_devices")
[http://wiki.archlinux.org/index.php/OSS](http://wiki.archlinux.org/index.php/OSS)

Do not worry!

Bis Morgen!

---

### Post by plzdontkillme11 on 2009-08-02
Oh, ok. Thanks for the links, too!

---

### Post by igorzwx on 2009-08-02
Type on Terminal:

[B]lsmod | grep snd


[/B]snd means ALSA modules[B].
If they are loaded, you are in trouble.

It might be after kerner update, I presume.

The extreme solution, might be a new installation.

First remove OSS4:

sudo dpkg –purge oss-linux

Then new installation.
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

But let us wait for Martin's advice
[/B]

---

### Post by igorzwx on 2009-08-02
correction  (2 -) before purge (--purge)

**sudo dpkg --purge oss-linux**

But let us wait for Martin

---

### Post by plzdontkillme11 on 2009-08-02
Ok, when I typed the command, nothing happened so I'm assuming that there are no ALSA drivers loaded. Since I don't think a reinstallation is necessary then, I guess I'll wait on Martin's help.

---

### Post by igorzwx on 2009-08-02
It is OK!

Let us wait for Martin

---

### Post by igorzwx on 2009-08-03
You have PCM problem,
read these stories:
[http://www.google.com/search?q=HD%20Audio%20play%20pcm%0A-%20Performing%20audio%20playback%20test...%0A%3Cleft%3E%20Device%20returned%20error%3A%20Input%2Foutput%20error&ie=UTF-8&oe=UTF-8](http://www.google.com/search?q=HD%20Audio%20play%20pcm%0A-%20Performing%20audio%20playback%20test...%0A%3Cleft%3E%20Device%20returned%20error%3A%20Input%2Foutput%20error&ie=UTF-8&oe=UTF-8)

---

### Post by martinbaselier on 2009-08-03
**dmesg | grep oss**
will show if there are any errors on the device.

Your ossmix shows:
jack.int-speaker.mute ON|OFF (currently ON)
This might be the cause.

Have you tried **ossxmix**
This is a mixer with a graphical interface. It might be easier. It also shows volume indicators when sound is playing.

I wonder which kernel you are using. **uname -r** will show you.

---

### Post by plzdontkillme11 on 2009-08-03
Martin, here's what I got for dmesg grep oss:

vignesh@vignesh-laptop:~$ dmesg | grep oss
[   29.277314] Adding 8675060k swap on /dev/sda5.  Priority:-1 extents:1 across:8675060k
[   32.787055] oss_hdaudio 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   32.802210] oss_hdaudio: Unknown HDA codec 0x11c11040
[   32.803214] oss_hdaudio: Unknown HDA codec 0x11c11040
[   32.806708] oss_hdaudio: Too many output endpoints for codec 1 (12)
[   32.859203] usbcore: registered new interface driver oss_usb
[  196.993110] oss_hdaudio: No suitable rate found!
[  196.997891] oss_hdaudio: No suitable rate found!
[  197.002133] oss_hdaudio: No suitable rate found!
[  197.006906] oss_hdaudio: No suitable rate found!
[  197.011254] oss_hdaudio: No suitable rate found!
[  197.016006] oss_hdaudio: No suitable rate found!

My kernel: 2.6.28-14-generic

I have ossmix, but everything seems normal. Nothing's muted, and everythings on highest setting.
 
I ran ossmix again through terminal (not the graphical interface) and it still says that the jack int. speaker is muted... is there a way to edit this through the terminal (the graphical interface shows nothing muted)?

---

### Post by igorzwx on 2009-08-03
Sorry to intervene, but here:

[http://bbs.archlinux.org/viewtopic.php?id=73438](http://bbs.archlinux.org/viewtopic.php?id=73438)

You can get exact the error with

**Code:**

dmesg |grep HDA

---

### Post by plzdontkillme11 on 2009-08-03
Thanks; I got this when I typed it in: 

vignesh@vignesh-laptop:~$ dmesg |grep HDA
[   32.802210] oss_hdaudio: Unknown HDA codec 0x11c11040
[   32.803214] oss_hdaudio: Unknown HDA codec 0x11c11040

The person in your link seems to have a problem similar to mine.

---

### Post by igorzwx on 2009-08-03
that story was successfull after compilation.

When I made experiments with Ubuntu 8.04,
I first tried to install deb, it was a failure.

then I made this:

[B]sudo dpkg --purge oss-linux

Then compiiled OSS4 from Mercurial, following this howto:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

It was a success.
[/B]

---

### Post by plzdontkillme11 on 2009-08-03
You're right, it was a success! :) 

One little problem: I can't hear the sound from "Sound Capture" in sound preferences when I press the test button. But other than that, everything's working perfectly!

Thanks a bunch!

---

