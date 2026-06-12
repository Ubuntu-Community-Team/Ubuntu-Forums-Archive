---
title: "t vtime and Pulseaudio"
date: 2008-04-19
forum: Multimedia &amp; Video
---

### Post by apoclypse on 2008-04-19
Does anyon know how to  get my tvcard  ouput which uses my line-in input on my primary card to forward sound to another device? I've tried getting Pulseaudio to forward all sound to both devices but I still don't here anything from my tvcard coming through my external USB card.

---

### Post by davidlm on 2008-05-04
I wanted the sound of tvtime, out by pulseaudio sink....
I did this:
* Start tvtime
* Mute the sound
* Write in the console: 
```
parec -d nvin | pacat
```
Where nvin is the name of the source (in my case of the primary soundcard).
 
* With the application pavucontrol i move the stream "pcat" to other sink (device)

---

