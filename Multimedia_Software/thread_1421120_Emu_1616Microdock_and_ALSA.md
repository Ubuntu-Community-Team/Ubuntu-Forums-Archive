---
title: "Emu 1616/Microdock and ALSA"
date: 2010-03-03
forum: Multimedia Software
---

### Post by counselordave on 2010-03-03
Ok, so I got alsa working, as far as I know. I have alsa 1.0.22 on my system. I can plug in my pcmcia card into my laptop, and my computer register's it, but when I plug in my microdock, alsa still thinks it's an EMU 1010, which is just the basic one, and I have a 1616, so none of my inputs register anything at all, so I can't record audio. The only thing that seems to be working perfectly or at all, are the audio jack on the pc card, the headphone jack on the microdock, and the stereo mini out for speakers on the microdock. I think it's odd that the headphone and stereo outs work on the microdock, but I can't input any audio. Anyone know how to get the rest of my microdock to work?

---

### Post by life-on-mars on 2010-05-08
Try to switch soundcards in the input tab of your pulseaudio mixer (sound preferences) or deactivate your onboard sound card in the bios.

The EMU 1616 is a modular system consisting of a EMU 1010 and the microdock. Accordingly, the EMU 1212 is a EMU 1010 plus a EMU 0202 daughter card. It's probably not that obvious with the PCMCIA version of the card. At least the PCI version of the EMU 1010 can be used without Dock or 0202 attached, and if you buy an EMU 1212, it is possibly to change the daughter card for a Dock afterwards.

---

### Post by cpolymeris on 2010-08-29
You may need to change the values of the different routing enumerations using alsamixer, they control the signal flow. They are labeled "DSP0", "DSP1"... for inputs and "Dock DAC 1", etc for outputs.
I also started writing a graphical mixer for that card, witch does preciselly that, easier:[ http://emutrix.googlecode.com]("http://emutrix.googlecode.com/")

I appreciate feedback/bug reports or any other comment.

---

