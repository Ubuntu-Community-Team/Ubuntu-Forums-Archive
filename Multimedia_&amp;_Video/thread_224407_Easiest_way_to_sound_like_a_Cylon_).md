---
title: "Easiest way to sound like a Cylon? :)"
date: 2006-07-27
forum: Multimedia &amp; Video
---

### Post by christian.convey on 2006-07-27
OK, so I was watching the old Battlestar Galactica show tonight, and I said to myself, I'd sure like to sound like a Cylon robot, despite having no clue about Linux audio.

So it sounds like Ubuntu Studio's setup, with jack, will do the trick.  Except I have no idea how to pull this off.  I *think* the Cylon sound comes from running my voice through a harmonizer effect.

Can anyone tell me what the simplest steps for a newbie are to achieve this effect:   microphone --> harmonizer effect --> speakers?

Thanks very much,
Christian

---

### Post by christian.convey on 2006-08-05
OK, I haven't done a side-by-side comparison, but I've got a recipe that sounds pretty darn close.

Here are the tools:
- a microphone (or a recorded voice, but I'm using mic) feeding into your soundcard.
- qjackctl
- jack-rack
- zynaddsubfx
- a properly-installed, properly-patched vocoder plugin for jack-rack.  Specifically, follow the instructions mentioned on this page: [http://linuxrockstar.blogspot.com/](http://linuxrockstar.blogspot.com/)  Scroll down to the section labelled "EFFECT: LADSPA VOCODER (HOWTO)" and follow those diretions.

Here's the setup:
Step 1) Launch jack-rack, and add the "vocoder" effect.  Enable it.  Give it the following settings:
Number of bands: 16
Band level 1: 1.0
Band level 2: 1.0
Band level 3: 1.0
Band level 4: 1.0
Band level 5: 0.394
Band level 6: 0.262
Band level 7: 0.75
Band level 8: 0.75
Band level 9: 0.75
Band level 10: 0.75
Band level 11: 0.75
Band level 12: 0.75
Band level 13: 0.75
Band level 14: 0.75
Band level 15: 0.75
Band level 16: 0.75

2) Launch zynaddsubfx, and select the patch "Analog Pad 1" (I think it's in the "Pads" bank).

Using qjackctl, set up the following audio routing:
(1) zynaddsubfx's output (both ports) --> jackrack's "in_2" port.
(2) the alsa_pcm (e.g. your mic) sound source (the alsa_pcm entry in the "Readable Clients / Output Ports" column) --> jackrack's "in_1" port.
(3) jackrack's output ports --> the alsa_pcm input ports (the alsa_pcm entry in the "Writable Clients / Input Ports" column).

Now you just need to create the two input sounds, and you should hear a Cylon.  For me, I press the A below middle-C on zynaddsubfx's keyboard, and while holding the note I speak into the mic.  Voila.

I've also found that the Cylon voice can go from cool/authentic, to boring, to incomprehensible, depending on the pitch of my voice and the particular note I'm playing on synaddsubfx.  I suspect that it sounds best when my voice and synthesizer have the same fundamental frequency, but I could be wrong.

Hope you have fun with this.
- Christian

---

### Post by edev on 2006-08-13
Oh yeah !

Thanx a lot Christian ! That's really cool.
Another amazing tool into my dapper box.

Ciao,

Eric,

---

