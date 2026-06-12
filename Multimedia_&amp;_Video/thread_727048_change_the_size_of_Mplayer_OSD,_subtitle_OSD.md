---
title: "change the size of Mplayer OSD, subtitle OSD"
date: 2008-03-17
forum: Multimedia &amp; Video
---

### Post by legolas_w on 2008-03-17
Hi
Thank you for reading my  post
I am using mplayer to watch movies  and now I need to watch a movie with a subtitile.
mplayer show very big subtitles which cover almost 1/3 of the screen, 
Is there any way to ask it to use smaller fonts for OSD?

Thanks

---

### Post by ridetheteapot on 2008-03-17
add this to your ~/.mplayer/config
subfont-text-scale=3

this works for mplayer on command line
if you use the gui you might need to do it by hand in ~/.mplayer/gui.conf
look for
font_text_scale = "5.000000"
and the related entries

---

### Post by strictlybusiness on 2008-03-17
Using Mplayer command line parameters will work. But I find it much easier just to use SMPlayer as a front-end for Mplayer. Outputs good sized subtitles and generally an easy to use interface which shows MPlayer at its best. Just install from Synaptic.

---

### Post by joellord on 2008-05-31
> add this to your ~/.mplayer/config
subfont-text-scale=3

I was having this problem on my mythbuntu machine.  The fonts of the subtitles were waaaay too big.  I modified the file as recommended by ridetheteapot and it did the trick.

Thanks !

---

