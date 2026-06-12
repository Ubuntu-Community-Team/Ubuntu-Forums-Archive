---
title: "Continuous Loop / Repeat Video in MPlayer"
date: 2008-01-08
forum: Multimedia &amp; Video
---

### Post by ugm6hr on 2008-01-08
I have discovered that I can loop video in mplayer (v1.0rc2) from Terminal with this:
```
mplayer -loop 0 Image01.avi
```

Unfortunately, I have a problem.  When using this, mplayer opens, plays the video file, then **closes** its window, then re-opens and plays again.

This is fine for long videos, but I need to use this for presentations of very short (i.e. around 1 second) videos that need to loop **without any breaks**.  This is how they default play in Windows Media Player with "repeat" - and I need to do the same on Ubuntu 7.10.  Gnome-Mplayer does not seem to have a *repeat* or *loop* option.  

Is there any way to get this functional - either from Terminal or GUI?

Thanks for ideas.....

PS: I have ffmpeg (avi) files that do not play at all in Totem (gstreamer) or VLC, and play in black-and-white with flaws in Kaffeine (xine) and Gxine (xine).  I can only get them to play properly in Mplayer or Gnome Mplayer.  So I need a solution in something with the mplayer engine.

---

### Post by ugm6hr on 2008-01-08
I have found a solution by trial and error myself:

```
mplayer Image01.avi -loop 0
```

I have no idea why this works better than having the option -loop before the filename...

I can also right-click to add gmplayer as a player, with a custom command:
> gmplayer %f  -loop 0

One more problem to solve:

How can you get a single frame .avi to stay displayed in Linux?

Again, Windows Media Player displays it as a continuous loop (i.e. the end result is a still image in WMP), but mplayer displays a black screen with the above fix.

Anyone got an idea?

---

### Post by ugm6hr on 2008-01-09
Sorry for just answering my own posts!  But figured that I would document my finding for anyone else who needs to display these types of media.

I can't get mplayer to "play" a single frame .avi file, but have realised that mplayer has the facility to *extract* individual frames from a video track.

```
mplayer Image01.avi -vo png z=0
```

This creates an uncompressed .png file from **all** the frames in the avi file.  Obviously, if there is only a single frame, this only creates a single png file.

It names the files:
00000001.png numerically (so the first frame is always number 1).

Having done that, I just have to rename the file to Image01.png before doing the next avi file.

Not quite as easy as in Windows, and bizarrely, the png file is larger than the original avi.  Presumably the z=value can be adjusted (0 to 9) to compress the image, but this is probably unnecessary for my uses.

Hope this helps someone.

PS: In case someone was wondering what use this might be, it is important to allow presentation of echocardiography images.

---

### Post by BlueSkyNIS on 2008-06-29
Your second post was very helpful for me. Thanks!

---

