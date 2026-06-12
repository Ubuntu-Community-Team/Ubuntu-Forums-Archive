---
title: "Would a PCI soundcard increase the volume output?"
date: 2008-04-07
forum: Mythbuntu
---

### Post by geoken on 2008-04-07
H.264 MKV's play ridiculously quietly on my HTPC. I use xine as my player, and with Xine's volume at max, and xfce's volume at max I still need to set my TV to it's highest volume setting and even then the dialog on the movie is drowned out by anyone in the room speaking at a normal volume.

I don't know where in the chain I'm loosing all the volume. It could be in the player itself, it could be my motherboards onboard sound , or it could be the mini-jack (aka. headphone jack) to RCA splitter.

Basically my question is wether or not I would get any noticable increase in volume by going to a dedicated PCI sound card and a direct RCA link?

---

### Post by johnnybirdman on 2008-04-07
> **geoken said:**
> H.264 MKV's play ridiculously quietly on my HTPC. I use xine as my player, and with Xine's volume at max, and xfce's volume at max I still need to set my TV to it's highest volume setting and even then the dialog on the movie is drowned out by anyone in the room speaking at a normal volume.

I don't know where in the chain I'm loosing all the volume. It could be in the player itself, it could be my motherboards onboard sound , or it could be the mini-jack (aka. headphone jack) to RCA splitter.

Basically my question is wether or not I would get any noticable increase in volume by going to a dedicated PCI sound card and a direct RCA link?

Have you jacked up all the volume levels in alsa?  Get to a terminal and type:
```
sudo alsamixer
```
My dvd playback was almost impossible to hear, until I maxed all the settings in alsa, then it was too loud, i had to back them down to 75% and all is well.
J.

---

### Post by geoken on 2008-04-07
If the ALSA mixer is different from the mixer available from the settings menu then no, I haven't tried that. I'll give it a shot tonight and see what happens.

---

### Post by laga on 2008-04-07
If alsamixer doesn't fix your problem, I think you can also enable audio compression in xine which will make the loud parts less loud and the quiet parts a bit louder. If that's the problem you're having..

---

### Post by johnnybirdman on 2008-04-07
> **geoken said:**
> If the ALSA mixer is different from the mixer available from the settings menu then no, I haven't tried that. I'll give it a shot tonight and see what happens.

before you try this note that I was wrong on the command, there is no hyphen.  it is just
```
sudo alsamixer
```
change the levels and hit ESC to exit.

J.

---

### Post by geoken on 2008-04-08
alsamixer didn't help, it was already maxed. However, I did get acceptable output from VLC using the volume normalize feature which seems to be the same as xine's audio compression. 

laga, how do I enable xine's audio compression?

---

### Post by geoken on 2008-04-08
OK, I found a filter under the right click menu ( Right Click>Audio>Postproccess>Chain Reaction) then I add the volnorm filter. The only problem is that I don't know how to launch this filter from the command line (and by extension can't use the filter in Myth).

---

### Post by geoken on 2008-04-08
OK, figured it out with a bit of trial and error. 

$ xine movie.avi --post volnorm:method=2

Now xine sounds great.

---

