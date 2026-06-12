---
title: "setting up  SPDIF with Asus p7p55D-e"
date: 2010-10-09
forum: Multimedia Software
---

### Post by jucadizo on 2010-10-09
Hi
I just spent almost a day reading through different threads about fixing the sound in my system, and I read as reference: 

**[https://help.ubuntu.com/community/SoundTroubleshootingProcedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")**

**[https://wiki.ubuntu.com/DebuggingSoundProblems]("https://wiki.ubuntu.com/DebuggingSoundProblems")**

**[http://ubuntuforums.org/showthread.php?t=1567023&highlight=p7p55d-e]("http://ubuntuforums.org/showthread.php?t=1567023&highlight=p7p55d-e")**
 
and so many others,

And at the end of the day i thought of "adding my two cents" by bringing my solution:

Current system Specs:
Ubuntu 10.04 (Lucid Lynx)
Kernel: initrd.img-2.6.32-25-generic-pae
Alsa Version 
      Driver version:     1.0.22.1
      Library version:    1.0.23
      Utilities version:  1.0.23

Sound cards in my system: 
     [INDENT]cat /proc/asound/modules
     0 [Intel          ]: HDA-Intel - HDA Intel
                          HDA Intel at 0xf79f8000 irq 39
     1 [Generic        ]: HDA-Intel - HD-Audio Generic
                          HD-Audio Generic at 0xf7afc000 irq 40[/INDENT]

List of play back devices: 
[INDENT]**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1828S Analog [VT1828S Analog]
Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1828S Digital [VT1828S Digital]
  Subdevices: 0/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

[/INDENT]

(here, the spdif is in the card 0 device 1 )

Codec: VT1828S


My problem: 
Try to enable the SPDIF port in the card as default playback device

Solved by:
Following all the configuration steps found in my references at the top and I was able to play a sound running the following:

aplay -D plughw:0,1 /usr/share/sounds/alsa/Front_Center.wav

but then I was **stuck** for a while trying to play sounds in other applications like exaile, mplayer, etc:

the fix was to add the following:

pcm.!default {
    type plug 
    slave {
       pcm "**plug**hw:0,1" 
    } 
} 

to:

/etc/asound.config

and

~/.asoundrc


thanks

---

