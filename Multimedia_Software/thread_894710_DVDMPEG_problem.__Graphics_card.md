---
title: "DVD/MPEG problem.  Graphics card?"
date: 2008-08-19
forum: Multimedia Software
---

### Post by bravo sierra echo on 2008-08-19
Just set up a new frankenbox with Ubuntu and am very happy apart from a couple of odd video problems.

DVDs and certain video files (it seems to be restricted to mpegs, but I haven't tested enough to say for sure) play with a green stripe along the bottom and in black-and-white, except for moving diagonal lines of colour.

I notice that I'm also restricted to no visual effects (I get a very unhelpful "Desktop effects could not be enabled" error) so I'm starting to wonder if I have a graphics card or driver issue.

Can anyone help?  What more info do you need, and how do I get it for you?

---

### Post by bravo sierra echo on 2008-08-19
Just in case this helps:
```
lspci -n | grep 0300
01:00.0 0300: 1106:3108 (rev 01)

lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)
```

---

### Post by shirilover on 2008-08-19
Have you tried any other players to see if this alleviates the problem?

I generally recommend MPlayer+SMplayer for video playback.

---

### Post by bravo sierra echo on 2008-08-19
Thanks for the suggestion, but it's a no-go.  Mplayer can only play the audio on the "odd" files - it fails to display the video at all with an error "Error opening/initialising the selected video_out (-vo) device"

---

### Post by rvm4000 on 2008-08-19
> **bravo sierra echo said:**
> it fails to display the video at all with an error "Error opening/initialising the selected video_out (-vo) device"

You can select a different video output:

mplayer -vo x11 dvd://
mplayer -vo xv dvd://
mplayer -vo gl dvd://
...

look at the manpage for more info.

---

### Post by bravo sierra echo on 2008-08-20
A bit of a forum search has turned up a few more issues that people have had with Linux and VIA graphics cards.  I think I'm going to give up on this box and use the other one that I have lying about - a shame, as it's a little slower and in an uglier casing, but the video tests out much better.

Thanks for the replies anyway!

---

