---
title: "M-AUDIO DELTA 1010LT Ubuntu 10.04 HELP!"
date: 2010-05-02
forum: Multimedia Software
---

### Post by scottstoked on 2010-05-02
Hi ... I'm pretty much an Ubuntu noob and I'm about to give up. I've spent hours reading tips and tricks to get this sound card working but I usually end up making things worse. This will be my last attempt and I hope someone can help.

- onboard sound is disabled in BIOS
- Delta 1010LT is recognized 
- fresh Ubuntu 10.04 32bit  install . . . everything is default.
- I know how to access the terminal and for argument's sake, let's say that's it. I need step by step.

I tried to remove all instances of pulse audio in the past and it  removed the desktop as well. Talk about frustrating.

Ok, so here I am. Fresh install, no sound and I haven't touched a thing. Someone please tell me what next .. thank you so much!

Scott

---

### Post by cchhrriiss121212 on 2010-05-02
You can control your card using a nice program called envy24control, which you can search for in synaptic. Or you can just use the slightly less functional alsamixer (open a terminal and type in "alsamixer").
The output channels will be labeled DAC0, DAC1 etc and are muted by default, so simply raise the volume up.

---

### Post by scottstoked on 2010-05-02
Thanks .. . but still no luck . . .I turned up all the sliders just to make sure and still nothing. :confused:

---

### Post by tgalati4 on 2010-05-03
You need to set patches from inputs to outputs using envy24control.

---

### Post by cchhrriiss121212 on 2010-05-03
Just tried out 10.04 today and you have two options: remove pulse, or try [this]("http://ubuntuforums.org/showthread.php?t=1469648").

---

### Post by scottstoked on 2010-05-03
Thanks guys .. . when I remove all instances I can find regarding pulse via package manager and then reboot, I have no desktop. Just a terminal window in the upper left. :confused:

---

### Post by scottstoked on 2010-05-04
Well, I guess I'm done with Ubuntu until they can get their audio issues sorted.

---

### Post by cchhrriiss121212 on 2010-05-05
Here's how I removed pulse while retaining a desktop:
Open synaptic
Mark pulse and compiz for removal
Mark xfce for installation
Reboot

You should remember that 10.04 is less than a week old, and as such will have numerous bugs just like any other new operating system. I still use 9.10 and pulse does not remove the desktop with it, so try that out if you want stability.

---

### Post by cathalcummins on 2010-05-05
I think you removed ubuntu-desktop when you removed "All pulseaudio" related entries in Synaptic.

I'm still having problems - I'm hopeful though. In envy24control the levels weren't moving at all until I removed pulseaudio and rebooted. They are moving to system sounds and youtube videos and when I 

```
aplay /usr/share/sounds/speech-dispatcher/*test.wav
Playing WAVE '/usr/share/sounds/speech-dispatcher/test.wav' : Signed 16 bit Little Endian, Rate 16000 Hz, Mono
```

All four channels light up but I still can't hear anything - I'm positive that this is something minor. 

I removed pulse entirely from /etc but still no go. I did a search for all things pulse via the file search, and it seems to have its finger in a lot of pies. Some of which are probably not important, some essential but some, potentially, are stopping the sound from happening. Can anybody name an obscure pulse file that is known to cause problems (apart from the ones that are removed by sudo apt-get remove pulseaudio)?

---

### Post by antipanda on 2010-05-05
from 
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442)


The reason pulseaudio right now doesn't work with this card is that it  expects a front device that has only 2 channels.
A possible fix for this is changing it's definition to:
ICE1712.pcm.front.0 {
        @args [ CARD ]
        @args.CARD {
                type string
        }
        type route
        ttable.0.0 1
        ttable.1.1 1
        slave.pcm {
                type hw
                card $CARD
        }
        slave.format S32_LE
        slave.channels 10
}
in /usr/share/alsa/cards/ICE1712.conf
This is taken from RedHat's and pulseaudio's bugtracker and the alsa  list, I can't find the relevant thread/bugs right now though...

---

### Post by BbUiDgZ on 2010-05-11
> **scottstoked said:**
> Well, I guess I'm done with Ubuntu until they can get their audio issues sorted.
This is a shame, another windows user willing to come a little out of his comfort zone scared back to windows and by the looks of this "low priority" bug that wont get fixed any time soon even although this card (maudio 2496) and others with the same chipset has been sold in their hunderds of thousands to spare room music makers all over the world.

I have the 2496 and i run ubuntu studio, my advice to music makers all over the world with this same problem.
If you don't want to hack and slash at your OS and you'd rather spend time making music rather than setting up your system so you can make music use 8.04 - its rock solid

---

### Post by Dalekk on 2010-11-09
My Delta 1010LT is working now in 10.04 by following the instructions given by antipanda. I didn't even need to remove pulseaudio, just had to select ICE1712 in the output tab under sound preferences and use the "Analog Stereo Output" in the hardware settings tab.

---

### Post by Evil-Ernie on 2010-12-09
Are you getting all channels working on the 1010LT? I say this because I am thinking of getting a multichannel soundcard for use in Ubuntu and its one of the options Im considering.

---

