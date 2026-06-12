---
title: "How I Got Audicity to Work! (Woot!)"
date: 2006-12-11
forum: Multimedia &amp; Video
---

### Post by wilberfan on 2006-12-11
I'm too new at this, and don't really understand WHY it works now, but here's how I got Audacity to successfully record and playback on my two dual-boot boxes.  (Indulge me please; this post will help me remember these settings when I (inevitably) reload Edgy (cuz I've screwed something up!)--and might help some OTHER poor n00b who's struggling??)

One is a AMD64x2 running 32-bit Edgy, the other a Dell Pentium-4 running 32-bit Edgy...

The AMD64x2 BOX has an Audigy SE sound card (which displays as a "CA0106"--whatever that is (maybe a chipset, or...?)
[B]
VOLUME CONTROL: CA0106 (Alsa Mixer)[/B]

*Playback Tab:*
    Analog Front slider
    Capture Feedback slider [for some reason boosts the monitor volume]
[I]
Capture Tab[/I]
    Line in

*Options Tab*
    Digital Capture Source: i2s in [Whatever the %#@$ THAT is???!]
    Shared Mic/Line in:  Line in

On the DELL, it looks like this:
[B]
VOLUME CONTROL: Sound Fusion CS46xx (Alsa Mixer)[/B]

*Playback Tab*
Master Slider
Line in Slider
**ADC** Slider *[I have no idea what this is!  But it's what got it to work!]*

*Switches Tab*
Line-in Capture [x]
ADC Capture [x]

Man, it feels GOOD to finally get this working!! Now I can rip some of my vinyl (without booting into XP)!!  :mrgreen:    (Maybe one day I'll actually *understand why *it's working!   8)

---

### Post by Luke Davis on 2007-04-25
HI Wilberfan,

Fairly new to ubuntu. Currently I have feisty 2.6.20.15 and have a sound blaster audigy CA0106 PCI card. That won't capture sound. I have tried exactly your settings above and they don't work for me. If I leave it as MIc in instead of line in I can hear myself in my own spearkers but this does not make it record sounds or work on Skype. Is there something that I should do. I presume that it is something to do with the card as I can't record sound in any application.:(

---

### Post by gitti on 2007-04-29
> **Luke Davis said:**
> HI Wilberfan,

Fairly new to ubuntu. Currently I have feisty 2.6.20.15 and have a sound blaster audigy CA0106 PCI card. That won't capture sound. I have tried exactly your settings above and they don't work for me. If I leave it as MIc in instead of line in I can hear myself in my own spearkers but this does not make it record sounds or work on Skype. Is there something that I should do. I presume that it is something to do with the card as I can't record sound in any application.:(

I have the same problem.

---

### Post by gitti on 2007-04-29
> **gitti said:**
> I have the same problem.

Follow [THIS]("http://ubuntuforums.org/showthread.php?t=353053&highlight=skype+audigy+se") and RESTART skype. Now works greatly!

---

### Post by Luke Davis on 2007-04-29
hi gitti

Yeah got skype to work following a differnet thread (Sorry can't find the same link)
Thanks for the help

---

### Post by gitti on 2007-04-29
You're welcome! ;)

---

### Post by mordak13 on 2007-04-29
Thanks, I'll have to give this a try as well. I miss Audacity.

---

### Post by christhemonkey on 2007-04-29
> ADC Slider [I have no idea what this is! But it's what got it to work!]

ADC standing for Analog to Digital Converter, which is what converts incoming analog signals to digital signals for processing. (so for converting the analog signal produced by your vinyl player to a digital signal in your soundcard) ((As i understand it anyway))

Read more about it here:
[http://en.wikipedia.org/wiki/Analog-to-digital_converter](http://en.wikipedia.org/wiki/Analog-to-digital_converter)

---

