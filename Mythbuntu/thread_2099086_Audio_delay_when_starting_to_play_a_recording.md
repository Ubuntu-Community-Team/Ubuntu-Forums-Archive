---
title: "Audio delay when starting to play a recording"
date: 2012-12-28
forum: Mythbuntu
---

### Post by brian_hammerhead on 2012-12-28
I just installed a fresh version of MythTV v0.26 (Mythbuntu 12.04.1 - 64bit).  The audio configuration was *much* easier to set up than my previous Mythbuntu 11.10 installation last Christmas, but it is different.

*Every time I try to play any kind of audio, there is a 1-2 second delay before the sounds starts to play**.*** :confused:

This happens with any type of audio - both inside MythTV and on the Ubuntu GNOME desktop (music, video, recordings).  This wasn't a problem with my previous installation.  I have tried both my normal receiver (Sony) and a new receiver (Onkyo) - same problem.

Here is my configuration:
NVidia GT430 video card with HDMI audio/video out
HDMI hooked to receiver which decodes into 5.1 surround sound.

In GNOME Sound Settings, I see:
HDMI/DisplayPort 4 - GF108 High Definition Audio Controller
Digital Output (S/PDIF) - Built-in Audio
Headphones - Built-in Audio
Analog Output - Built-in Audio

I can post the output of aplay -l if that helps.  I know that this card is outputting on card 1 device 9.  I tried setting a /etc/asound.conf to default to this card, but nothing is fixing the delay.  I am not an expert, so I could be missing something simple.

I have Googled for the past couple of days trying to find an answer, but nothing.

Has anyone else seen this problem?

---

### Post by brian_hammerhead on 2012-12-28
More information:

Leaving everything else the same, I tried a sound test on each of the available outputs

HDMI/DisplayPort 4 - GF108 High Definition Audio Controller = DELAY
Digital Output (S/PDIF) - Built-in Audio = no delay
Headphones - Built-in Audio = no delay
Analog Output - Built-in Audio = no delay

The delay only happens when the audio is output via the GT430.  The digital S/PDIF out on the motherboard to the receiver has no delay, which rules out receiver decoding delay issues.  There was no delay when using Ubuntu 11.10 and my GT430 card.

So, this definitely points to an issue with Ubuntu 12.04 and my GT430 card.  Hopefully this is a configuration setting somewhere.

Anyone have any ideas?

---

### Post by PhilWig on 2012-12-31
A stab in the dark.  Did you load 'recommended' Nvidia drivers?
On my setup they are under Applications >  system > mythbuntu control centre > graphics drivers

Phil

---

### Post by thaibuntu on 2013-02-05
I also have this problem. I am using on board HDMI with an AMD APU. Sound did not work at all before I installed the proprietary driver, but works okay now. I just chock it up to poor video driver (even though it's an audio issue).

---

