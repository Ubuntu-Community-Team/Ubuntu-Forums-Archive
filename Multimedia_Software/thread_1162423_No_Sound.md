---
title: "No Sound"
date: 2009-05-17
forum: Multimedia Software
---

### Post by X.Cyclop on 2009-05-17
Hi.

I've just installed Ubuntu 9.04 and the sound isn't working.
I can play music and watch videos, but i can't hear any sound.

**Kernel** 2.6.28-11

**Sound card** Intel ICH6


:sad:

---

### Post by X.Cyclop on 2009-05-18
[B]**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/B]

anybody??:icon_frown:

---

### Post by motsteve on 2009-05-18
I'm a Mac guy and have done quite a few installations of various Linux ppc distro's and I don't know if I can help, but one of the biggest problems that I have getting a new installation to work is sound.  If you are familiar with the terminal, try going there and enter the command "alsamixer".  A funky looking panel display should appear in the X window with vertical bars across the screen with little boxes under each bar.  Using your right arrow on the keyboard, go over to the bar labelled "Audo Mut". If it shows "00" in the square box, change it to off by pressing the "m" key. Move left with the arrows and if you have speakers, turn off the "PC Speak" item.  Then scroll over to the "Headphone"box and light them up. To get out of alsamixer hit the esc key.  If you can't get "alsamixer" to work and it gives you an error message or a single bar in the X window, then you may have to do some messing around with installed drivers. Use the Synaptic Package Manager for that. Also read the man pages for alsa, which you can get by entering "man -k alsa".

I hope this gets you started at least, if not, just ignore me.;)

---

### Post by X.Cyclop on 2009-05-18
Yeah!!:D

I just unselected the 'external amplifier' and it worked!

the question is why does it make trouble?

thanx! ;)

---

### Post by motsteve on 2009-05-18
I learn by doing and trying to read, but sometimes I just have to do something and have faith in the results.  I like to know the whys, but if I can "fix" something and find out later the "why", I just pretend that the search is part of the "fun" of the computer hobby. Reality stinks, but what's the alternative?;)

Your answer sounded positive so I'm hoping that you fixed your problem.  I forgot to tell you also, that I test my sound by entering in the command "tput bel" in the terminal.  This rings the system error bel and the sound tells me that all is well.

---

### Post by frcsyk on 2009-05-18
I have the exact same sound card in my system as you X.cyclops but even with the external sound amplifier on mute I still get no sound.  I've been fighting this for about a week now and even went back to 8.04 then back to 9.04 with no luck.  

I've tried everything! Does anyone have any other ideas?  My system is a Thinkpad X41.  Any help would be greatly appreciated.

---

