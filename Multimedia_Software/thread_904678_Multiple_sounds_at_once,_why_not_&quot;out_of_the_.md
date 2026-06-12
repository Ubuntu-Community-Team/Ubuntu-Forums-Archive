---
title: "Multiple sounds at once, why not &quot;out of the box&quot;?"
date: 2008-08-29
forum: Multimedia Software
---

### Post by atari130xe on 2008-08-29
I have tried, many times to make it to work (multiple sounds at once in Ubuntu 8.04) but for some reason, after trying many possible solutions nothing worked for me, than just erase PulseAudio from my sys. 3 Different computers with different sound chips and always the same problem, NO multiple sounds at once available, why is that? I should not "dismantle" my OS to have just a function like this. Does anybody has any logical response to this issue?
best regards

---

### Post by markbuntu on 2008-08-29
The problem has a lot to do with the choices Ubuntu made when putting the distro together. It seems they left out many parts that are necessary to get multiple sound applications working together. 

But anyway, I have figured it out and you can use my extensive guide to get all your sound applications working together. You can just skip over the first part if your sound is already working: 


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by atari130xe on 2008-08-29
> **markbuntu said:**
> The problem has a lot to do with the choices Ubuntu made when putting the distro together. It seems they left out many parts that are necessary to get multiple sound applications working together. 

But anyway, I have figured it out and you can use my extensive guide to get all your sound applications working together. You can just skip over the first part if your sound is already working: 


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Thanks Mark but could you please tell me from "where" to "where" I should read your extensive guide ( already have sounds in my PC) :)

---

### Post by markbuntu on 2008-08-29
Well, you can start at the Introduction and end at the Pulse Audio Volume Control for just a basic playback setup. There is not a lot of things you need to do in there that would be difficult, it is mostly just checking stuff, maybe getting some packages, and opening things and clicking on them.

You can also skip all the links unless you need something specific from one of them.

---

### Post by atari130xe on 2008-08-29
Mark: I have a question, as you can see I have 2 devices: HDA VIA VT82xx & Realtek ALC662 rev1 (which one I should choose, actually I am using the first one HDA VIA VT82xx and everything seems to work ok), is that correct?

By the way, for the first time with PulseAudio and after following your guide, I HAVE MULTIPLE SOUNDS! :) BUT: Games (no matter what kind) does not play any sound and the ones who start just get freeze) any help?

---

### Post by markbuntu on 2008-08-29
You can use both of your sound cards if you want. I have three and use 2 of them all the time. I use one card for headphones and the other for speakers. I can switch streams  to either one in the Pulse Audio Volume Control by right clicking on the stream and choosing move stream.

You can also set them up to both play the same thing using the pulseaudio combine module. You can find the link to info about that further down my guide in the Pulse Audio Modules section.

You can try changing the settings in Sound to ALSA, That should not make a difference for everything else but may help with your games.

What games are you trying to play?

---

### Post by atari130xe on 2008-08-29
> **markbuntu said:**
> You can use both of your sound cards if you want. I have three and use 2 of them all the time. I use one card for headphones and the other for speakers. I can switch streams  to either one in the Pulse Audio Volume Control by right clicking on the stream and choosing move stream.

You can also set them up to both play the same thing using the pulseaudio combine module. You can find the link to info about that further down my guide in the Pulse Audio Modules section.

You can try changing the settings in Sound to ALSA, That should not make a difference for everything else but may help with your games.

What games are you trying to play?

Thanks once again, well everything seem to be ok, but games... it keep freezing: Very simple games like: circus linux, frozen bubble, Chromium, etc. they start ok (without sound) but freezes. I have no idea, I guess it has to be with pulse audio but sincerely I dont know where to change setting for games. Its important because this computer is used by a 10 years old kid.

---

