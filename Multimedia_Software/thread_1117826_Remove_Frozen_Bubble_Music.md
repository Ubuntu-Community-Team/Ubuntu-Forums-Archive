---
title: "Remove Frozen Bubble Music?"
date: 2009-04-06
forum: Multimedia Software
---

### Post by wbee on 2009-04-06
Hello,

Frozen Bubble is creative and perhaps addictive.

The music file is fb-music-high.

If I remove it,to listen to my own music while I play,will I break anything in the rest of fb?

If not,what is the terminal command to remove the music?

--------

Thank you

---

### Post by apmcd47 on 2009-04-06
I've just had a look - the music and sound-effects look to be a set of ogg-vorbis files in /usr/share/games/frozen-bubble/snd, so I think you could replace the frozen-mainzik-1p.ogg with your music file and see what happens. I woulds suggest making copies so if anything goes wrong you can back out. I would also suggest converting your music to ogg, if it isn't already.

Andrew

---

### Post by wbee on 2009-04-06
Andrew,

Thank you. I'll try that when I get home.

---

### Post by baldranger on 2010-06-12
Alternatively - launch frozen bubble through Alt F2
and add;
-no-music

or 

-no-sound

this switches off the sound and you can listen to your own music.

---

### Post by Jay Car on 2011-01-22
> **baldranger said:**
> Alternatively - launch frozen bubble through Alt F2
and add;
-no-music

or 

-no-sound

this switches off the sound and you can listen to your own music.

baldranger, I know this is an old thread, but thank you so much for your post. It just shows how helpful the forums can be for solving problems, even small ones like this. 

I have one general-use, Ubuntu 10.10, computer that I let other folks use. That computer has all the games installed, including Frozen Bubble. 

One of my grandaughters loves Frozen Bubble and plays it by the hour...day after day...week after week. I have turned the computer sound off, but she turns it on again, though very low. It's still right at the edge of my hearing, which almost makes it worse. 

This afternoon I was to the point where I just wanted to grab those miniature Frozen Bubble penguins and poke their beady little eyes out with a dull ice-pick... 

...which might be a little extreme. So tonight I've been madly searching for a way to completely shut the darned game music off before she comes back on Monday. I found it in your post, and tried it. It works! Awesome! :D

Now she can play the game without me wanting to rip the mouse out of her little hand...

You have saved what small amount of sanity I had left.
Thank you! :)

---

### Post by pixiestarr on 2011-12-22
hi.. im still not managing...i have ubuntu 11.04...maybe im doing it wrong? please help:confused:

---

### Post by yoramdavid on 2012-06-28
> **pixiestarr said:**
> hi.. im still not managing...i have ubuntu 11.04...maybe im doing it wrong? please help:confused:

Just in case you are still looking for a solution:
Edit de menu entry or make a new one and add ```
--no-music
```
It should look like this:
```
frozen-bubble --no-music
```
It works for me.

---

