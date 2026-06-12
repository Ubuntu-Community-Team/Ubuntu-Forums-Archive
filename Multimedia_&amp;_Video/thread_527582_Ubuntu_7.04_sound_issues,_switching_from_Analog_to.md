---
title: "Ubuntu 7.04 sound issues, switching from Analog to Digital Output ENS1371"
date: 2007-08-16
forum: Multimedia &amp; Video
---

### Post by demonicdude on 2007-08-16
Hello all. I am having an issue with sound being played through my digital speakers. Basically, there is no sound =P. However, through my analog (Crappy) speakers, sound comes perfectly. So i beleive the issue i'm having is how to change the output of the sound from analog to digital. 

I made another thread in this forum ([URL=http://ubuntuforums.org/showthread.php?p=3202368&posted=1#post3202368[/URL], but the people that were helping me there said to create a new thread with a *catchier* title =D. So here i am again, just in desperate need of an answer. 

As arthur said: "tell them that you can't for the life of you figure out how or what to change in feisty to switch."

this is what i get when i type aplay -l and -L in the terminal:

-l:
**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

-L:
front:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC2/ADC
    Front speakers
surround40:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC2/ADC
    4.0 Surround output to Front and Rear speakers
iec958:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC2/ADC
    IEC958 (S/PDIF) Digital Audio Output


Also, another random peice of maybe helpful information. I had ubuntu Dapper installed some time back, and my digital speakers worked fine without me having to do a thing =). 

Also, in alsamixer, there is no iec958 option or any real option to switch from digital to analog, (i've tried all of them)
So basically the problem is: Digital speakers= No, Analog speakers= Yes, how to switch.

Thanks in advance for all the help you can offer =P. 
(thank you Arthur and moore in my other thread =D)

---

### Post by demonicdude on 2007-08-17
*bump~~~*

---

### Post by demonicdude on 2007-08-17
bump....

---

### Post by sada_lives on 2007-08-18
(Copied verbatim from my last post in your original thread, don't know if you saw it)

For the record, I use Boston BA735 digital speakers, and the solution was entering Volume Control (via double clicking the speaker icon in the taskbar), navigating to "switches", and making sure "SB Live Analog/Digital Output Jack" is checked. I have Headphone LFE checked as well, but I am not sure if that is relevant.

Obviously yours will not say "SB Live", but I hope some similar switch is there to help you.

---

### Post by demonicdude on 2007-08-19
yup, i dont have that. Probably the sblive was the sound card i'm guessing? So thats why that would be different. I have Creative AudioPCI, which does work with digital because it works on Windows.

---

### Post by demonicdude on 2007-08-22
bump

---

### Post by demonicdude on 2007-09-03
bump

---

