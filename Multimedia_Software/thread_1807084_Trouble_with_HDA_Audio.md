---
title: "Trouble with HDA Audio"
date: 2011-07-18
forum: Multimedia Software
---

### Post by sulgorae on 2011-07-18
Hi Guys

I'm having problems with audio on Ubuntu 11.04 using an Asus M4A87TD/USB3 motherboard I bought last week.  The sound chipset is a VIA VT1818S.  So, my problems are:
[LIST][*]5.1 sound using the 3 stereo jacks won't work[*]Front microphone input won't work

[/LIST]
In the sound preferences it shows my speakers as 5.1, but when I test the speakers only left and right work.
The front mic port doesn't work at all no matter what i select in sound preferences.

To try and fix this I've checked all the settings in alsamixer, nothing is muted.  
I've added another line to my alsa-base.conf(options snd_hda_intel model=auto)
I've tried using the latest builds of pulse audio snapshots from the dev ppa
I've also tried using the really old versions of alsa that some people had success with on ubuntu 10.04, didn't help me either.

I've been using ubuntu for the past 3 years as my main OS, but i'm really starting to think about using win7 permanently.  Please help me.

---

### Post by Help Computer on 2011-09-14
> **sulgorae said:**
> Hi Guys

I'm having problems with audio on Ubuntu 11.04 using an Asus M4A87TD/USB3 motherboard I bought last week.  The sound chipset is a VIA VT1818S.  So, my problems are:
[LIST]
[*]5.1 sound using the 3 stereo jacks won't work
[*]Front microphone input won't work
[/LIST]
In the sound preferences it shows my speakers as 5.1, but when I test the speakers only left and right work.
The front mic port doesn't work at all no matter what i select in sound preferences.

To try and fix this I've checked all the settings in alsamixer, nothing is muted.  
I've added another line to my alsa-base.conf(options snd_hda_intel model=auto)
I've tried using the latest builds of pulse audio snapshots from the dev ppa
I've also tried using the really old versions of alsa that some people had success with on ubuntu 10.04, didn't help me either.

I've been using ubuntu for the past 3 years as my main OS, but i'm really starting to think about using win7 permanently.  Please help me.

I have the exact same motherboard and had similar problems (only L/R speakers, no input) with Ubuntu 11.04. To enable 5.1  I selected the device "Internal Audio", below that I selected "Analogue Surround 5.1 Output + Analogue Stereo Input" for the selected device in "Sound Preferences". Then testing the speakers they all worked.

To get input working (or in your case mic), I had to install Gnome Alsa Mixer from the software centre, then un-mute "Input". For some reason this didn't work using alsamixer from the terminal.

The only problem I had after installing Gnome Alsa Mixer (possibly related to the "smart 5.1" option) was reduced subwoofer volume. I now need to have my subwoofer nob to max to get the same level I was getting before. In Windows the program that comes with the motherboard CD (something like HD Via Audio) resolves this with the various boosting options.

---

