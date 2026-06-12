---
title: "After Affects and Sound Booth alternatives"
date: 2009-06-05
forum: Multimedia Software
---

### Post by feardotcom on 2009-06-05
Does anyone know of, preferably free, alternatives to Adobe After Affects and Sound Booth? 

In my classes i would record the sessions with Sound Booth, and it records in a raw format, so you can increase the volume of the tracks with out distorting the audio.

I'm also looking for an After Affects alternative for video compositing and also adding effects. Even if its something as simple as what windows media player does but maybe on a more professional level.

Does anyone know of anything?

---

### Post by feardotcom on 2009-06-05
Does anyone know of, preferably free, alternatives to Adobe After Affects and Sound Booth? 

In my classes i would record the sessions with Sound Booth, and it records in a raw format, so you can increase the volume of the tracks with out distorting the audio.

I'm also looking for an After Affects alternative for video compositing and also adding effects. Even if its something as simple as what windows media player does but maybe on a more professional level.

Does anyone know of anything?

---

### Post by feardotcom on 2009-06-06
Bump..Bump..

Anyone? Anyone? Marco? Marco?

---

### Post by jbradley5000 on 2009-06-06
I'm not familiar with the Adobe products you mentioned but for basic audio recording and editing I use Audacity.  You might look into Ubuntu Studio which is a variation of ubuntu with audio and video software included with the OS.  They might have something you can use in there.

---

### Post by feardotcom on 2009-06-06
Yeah i was reading a some of Ubuntu Studio, it just doesn't give much detail on the software functionality. 

With Audacity can you plug like a m-audio device into it and record, or does it require something more high end like a digi design?

---

### Post by UbuntuNerd on 2009-06-06
try this link: [http://jahshaka.org/Tutorials/p2_articleid/75](http://jahshaka.org/Tutorials/p2_articleid/75)

---

### Post by feardotcom on 2009-06-06
That looks promissing! Kino does as well! 
Hmmmm, I found there is a lot more functionality to InkScape than i first thought. I cant wait till my computer parts arrive next week! I will get the chance to test all this stuff out!

---

### Post by Backharlow on 2009-06-07
Cinelerra CV (community version)
It is technically an pro editor, but does have a clean compositing engine with an effect collection. And they have their own Ubuntu repo.
[http://cinelerra.org/](http://cinelerra.org/)

Sounds weird but there is a very sophisticated node-based video compositor built into Blender 3D (that no one seems to know about since its in a 3D application) which stacks up to Apple's Shake compositor.

---

### Post by Backharlow on 2009-06-07
For sound I recommend Ardour. This is a serious multitracking environment.

---

### Post by feardotcom on 2009-06-07
Can you recommend a recording interface card? or digital mixer preferably on the entry-mid level price that works well with the recording programs?

EDIT:
I plan on recording guitar, bass guitar electronic drums, and synth, as well as voice. I will probably later down the road buy some high dollar mics to record the makeshift sound effects. lol

---

### Post by Backharlow on 2009-06-07
I would suggest avoiding any external cards. I've tried 3 m-audio cards. 1 usb, 1 firewire, and one internal pci card. The pci is definitely the right type of interface. 
The usb worked but audio over usb makes for a noisy recording. 
The firewire did not work at all, because my card was not supported by the drivers in Ubuntu whatsoever, although there is a list of supported firewire cards somewhere, and despite other firewire devices (drives, nics, etc) seem to rock well on Ubuntu.
So, go with PCI, and again I recommend the M-Audio line, which is a sort of "pro-sumer" devision of Avid, so they create mid-grade, mid-cost alternatives to the more expensive Pro Tools cards - cheap, but still hands-down superior to the crap that comes built into PC's, even if you get an old one on ebay or the like.
The M-Audio stuff also all seems to work equally well on Mac, Linux and Windows, although the mixer utilities that come with them don't have a Linux version, but there is so much good sound software in Ubuntu and UbuntuStudio, I haven't missed it.

That said, the other concern with studio recording and cards is that your card is going to have A: ENOUGH inputs for simultanious channel based recordings of all your sources. B: The RIGHT KIND of inputs for your sources. So, if its microphones, you may need to pre-amp them, and/or supply phantom power to them prior to going into the card. If not you might want a card that actually has some mic level inputs, and/or XLR connectors. Likewise, guitar is line level and another cable connector type, so you'll need either adapters, or a card that has that fat 1/4" guitar jack input. Buy the card for your situation. It's a lot easier than changing your situation to match the card.

---

### Post by feardotcom on 2009-06-07
Couldn't i just connect a basic mixer, 10-14 channels, to the pci card via the 1/4" out jacks on the mixer? OR does it not work like that?

---

