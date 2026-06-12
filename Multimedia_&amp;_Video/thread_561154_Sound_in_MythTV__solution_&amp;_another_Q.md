---
title: "Sound in MythTV :: solution &amp; another Q"
date: 2007-09-27
forum: Multimedia &amp; Video
---

### Post by derby007 on 2007-09-27
I finally got sound working in MythTV, solution was as follows:: 

Doing the 'dmesg | grep alsa' command (or ALSA) finds the following: 
:: saa7134 ALSA driver for DMA sound loaded
:: saa7130[0]/alsa: saa7130[0] at 0xfeafec00 irq 217 registered as card 1
ie. card 1 is being used, amixer info shows 2 cards >

derby7\> amixer info -c 0
Card hw:0 'ICH5'/'Intel ICH5 with AD1980 at 0xfeb7fa00, irq 201'
  Mixer name    : 'Analog Devices AD1980'
  Components    : 'AC97a:41445370'
  Controls      : 40
  Simple ctrls  : 29
---------------------------------------

derby7\> amixer info -c 1
Card hw:1 'SAA7134'/'saa7130[0] at 0xfeafec00 irq 217'
  Mixer name    : 'SAA7134 Mixer'
  Components    : ''
  Controls      : 6
  Simple ctrls  : 3
---------------------------------------

So I then changed to card 0, by doing: 
derby7\> amixer -c 0 
ie. use the '0' intel card

Then mute 'line-in' in playback, and set capture level.

My problem is now that sound is only in mono, ie. sound is coming out from the sat box (via sound-out R&L) and into my TVCard and then going into my PC sound card. But the TVCard only passes on mono. I wonder if I can go directly into the PC sound card, I'll try this tonite. Please leave any comments/suggestions on getting stereo!!

---

