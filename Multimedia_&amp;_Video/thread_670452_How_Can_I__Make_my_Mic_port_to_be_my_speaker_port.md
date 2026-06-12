---
title: "How Can I  Make my Mic port to be my speaker port?"
date: 2008-01-17
forum: Multimedia &amp; Video
---

### Post by coollettuce on 2008-01-17
My motherboard has 6 3.5mm ports for audio. My green one that I usually plug my headphones into is broken, the port itself. How can I make my pink mic port to be my green speaker port? Thanks. BTW alsa is the sound driver.

---

### Post by Lord Illidan on 2008-01-17
I doubt it's even possible from a software issue..

---

### Post by steeleyuk on 2008-01-17
Theres probably some hardware issue which would prevent you from doing this.

Is there no line-out port you can use? Some cards have them...

---

### Post by coollettuce on 2008-01-17
Well on windows there was a nice gui that came with my sound driver and it allowed me to pick what I wanted each port to be. It doesn't have to be the mic one, it can be one of the other ones on there. The black and the green ones are broken so I need to be able to make one of the other ones a sound out one.

---

### Post by Waappu on 2008-01-17
> **coollettuce said:**
> My motherboard has 6 3.5mm ports for audio. My green one that I usually plug my headphones into is broken, the port itself. How can I make my pink mic port to be my green speaker port? Thanks. BTW alsa is the sound driver.

It is impossible Í would say. You need modify your motherboard if you like do that. This isn't anything to do with software.

---

### Post by coollettuce on 2008-01-17
> **Waappu said:**
> It is impossible Í would say. You need modify your motherboard if you like do that. This isn't anything to do with software.

You are completely wrong, I booted into windows and easily chose to make my mic port a speaker port. If it can be done in windows with the same hardware shouldn't it be able to be done in Linux? I'd like to get back into linux asap.

---

### Post by Whiffle on 2008-01-17
What motherboard and sound card do you have?

---

### Post by coollettuce on 2008-01-17
I have a Gigabyte M59SLI-S5, with on board audio.

---

### Post by Whiffle on 2008-01-17
Looks like it might be possible, you'd have to play with the settings for the snd-hda-intel module.  

Heres some info on it:
[http://murga-linux.com/puppy/viewtopic.php?t=22383](http://murga-linux.com/puppy/viewtopic.php?t=22383)

---

### Post by coollettuce on 2008-01-17
Thanks for your help, but is the intel driver the right one, I have an AMD cpu and not an intel chipset. Also how do I change settings for a sound driver?

---

