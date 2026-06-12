---
title: "Cannot hear guitar play back when recording."
date: 2007-12-09
forum: Multimedia &amp; Video
---

### Post by Soglad on 2007-12-09
**[COLOR="SeaGreen"]Hello guys. I am trying to record my guitar through my laptop into Audacity and I am having two very annoying problems. I can't hear the guitar AS I'm recording, so I'm not about to hear myself play over things, which is very hard to work with. Second, is a get a horrible "beeeeeep" noise all the way through as I record anything. I have a Compaq Presario C700 with a HDA Intel chipset.[/COLOR]**

---

### Post by Soglad on 2007-12-09
bump

---

### Post by Soglad on 2007-12-10
bump

---

### Post by Soglad on 2007-12-11
bump

---

### Post by josesanders on 2007-12-11
I've had problems with playing back while recording with Audacity, but for me, it just couldn't do it.  It gave me an error, saying that it couldn't open the sound device whenever I enabled the play back previous tracks while recording option.  I don't know if this will help you, but I solved the problem by recompiling Audacity to use ALSA.  See this page:

[http://audacityteam.org/wiki/index.php?title=Linux_Issues](http://audacityteam.org/wiki/index.php?title=Linux_Issues)

Here are the general instructions for compiling Audacity:
[http://audacityteam.org/wiki/index.php?title=CompilingAudacityForBeginners](http://audacityteam.org/wiki/index.php?title=CompilingAudacityForBeginners)

It was a while ago that I did this, and if I remember correctly, it didn't go totally smoothly, but I did get it to work, so if you run into any problems, let me know.

---

### Post by Soglad on 2007-12-11
Thanks mate, I'm busy at the moment, and will try soon!

---

### Post by josesanders on 2007-12-13
What sound card do you have?  Before you go to the trouble of recompiling Audacity, make sure that your card is full duplex, i.e. that it has the capability for simultaneous playback and recording.  Not all sound cards have this capability, and if yours doesn't then there's nothing you can do in software to get around it.

---

### Post by Soglad on 2007-12-14
> **josesanders said:**
> What sound card do you have?  Before you go to the trouble of recompiling Audacity, make sure that your card is full duplex, i.e. that it has the capability for simultaneous playback and recording.  Not all sound cards have this capability, and if yours doesn't then there's nothing you can do in software to get around it.

This laptop has a HDA Intel chipset....it's a very cheap laptop, so it might not have any functionality in that regards....I think I'll have to build myself a proper desktop.

What should I look for in a laptop for audio recording?

---

### Post by josesanders on 2007-12-14
I'm no expert in audio recording, so I can't really give you any advice as far as what equipment to buy.

As far as your sound device, can you be more specific?  I searched for the Intel HDA chipset, but I think there are several different varieties.  My guess is that it will probably work for simultaneous playback and recording, but I can't say for sure.

---

