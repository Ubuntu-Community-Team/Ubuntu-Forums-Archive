---
title: "Laptop Audio Jack Retasking"
date: 2010-11-07
forum: Multimedia Software
---

### Post by VrIgHtEr on 2010-11-07
I have an MSI GX600 laptop. It has intel hda sound with 3 audio jacks for headphones/speakers, mic in, line in. On Windows the driver allows me to retask the jacks to outputs (all three of them) in order to be able to use a 5.1 sound system (My system has 3 jacks, 1 for each 2 speakers). I haven't been able to discover how to do this in Ubuntu 10.10 (and didn't really have any luck on previous versions either). Is it possible to do this or not? Most threads I found didn't have any answer at all :S

Btw sry if I didn't attach enough information. I don't know what you'd need (or how to get it either, please give me instructions if you request the output of some command).

If this is not possible I would like to at least get a reply saying so. As I said most posts I found didn't have any answer at all... which kinda left me a bit curious.

Thanks in advance :)

---

### Post by ttarvai on 2011-02-01
It's my problem also. However, on the official IRC help channel I was told that this is impossible. :(

---

### Post by VrIgHtEr on 2011-02-02
well that sucks :/

It's the only remaining problem I have with ubuntu... Just the one. Oh well... one can still hope for the future xD

---

### Post by pharaxe on 2011-10-30
I have a Dell XPS M1530 with 3 audio jacks and Ubuntu 10, and I've had luck doing something similar with JACK. It might be a good direction to look. 

Jack does [lots of things]("https://help.ubuntu.com/community/What%20is%20JACK"), but one feature is the JACK Audio Connection Kit, which can send sound from applications to different channels. I use it to retask a set of channels for a jack to my headphones and one set for the line out jack. So while I'm DJing I can preview songs to my headphones without interfering with music playing out the line out. I bet it could do what you want as well.

That being said, I've had trouble getting JACK to play nicely with all of the applications I use, so I usually use PulseAudio (the default Ubuntu sound server), and then disable it and run JACK when I dj.

In fact, you might be able to get PulseAudio to retask the jacks for you, JACK might be a little heavy handed just to set up surround sound.

That's all I know on the matter, hopefully it's helpful information!

---

### Post by VrIgHtEr on 2011-10-30
as far as i've looked online... it's just not possible... you rerouted audio between two output jacks, my problem is I need to change an *input* jack to an output one... THEN i can route audio to it :)

I know it's supported in hardware cos that's the way it worked on windows. This is the only thing that I have never gotten to work on linux (though i did uninstall windows regardless... i still love linux way too much xD)

---

### Post by VrIgHtEr on 2012-03-05
[http://voices.canonical.com/david.henningsson/2011/11/29/turn-your-mic-jack-into-a-headphone-jack/](http://voices.canonical.com/david.henningsson/2011/11/29/turn-your-mic-jack-into-a-headphone-jack/)

FINALLY found something that works :D:D:D

---

