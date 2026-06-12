---
title: "Video playback very jumpy"
date: 2007-05-23
forum: Multimedia &amp; Video
---

### Post by sebz2005 on 2007-05-23
G'day fellow ubuntu-ians... :-s

I have a problem with my video playback.
I have Totem-xine, gxine, VLC and mplayer installed and each of them have the same problem.
They all skip the 5th (?) frame of any video (whether it be a MPG, AVI, WMV or DVD)
Is there something that I've done wrong in the configuration or setup that I can change to fix this?
I really want to watch the trailer for Pirates of the Caribbean :p

---

### Post by tanelt on 2007-05-23
Well, if all the players have the exact same problem, it sounds like there's a problem with something that all of them use.


Did you apply some system-wide configurations just before the problem appeared? If yes, try to revert them.

Have you tried reinstalling/reconfiguring the graphics card drivers?

---

### Post by eye208 on 2007-05-23
> **sebz2005 said:**
> I have a problem with my video playback.
I have Totem-xine, gxine, VLC and mplayer installed and each of them have the same problem.
They all skip the 5th (?) frame of any video (whether it be a MPG, AVI, WMV or DVD)
Is there something that I've done wrong in the configuration or setup that I can change to fix this?
It seems your video driver has vsync (vertical sync) enabled.

As you probably know, there are two video standards which differ slightly in framerates: NTSC video uses 29.97fps while PAL video uses 25fps. If you watch PAL video on a display operating at 60fps, the framerates will not be in sync. This can result in either of two effects which are best visible during panning camera shots: Either the picture gets torn apart somewhere in the middle or some frames will be shown longer than others, resulting in jumpy motion. The latter will happen if your video card has vsync enabled.

The same thing will happen if you watch NTSC video on a display operating at, say, 75fps. Most TFTs typically operate at 60-75fps. So if you watch lots of PAL stuff, run the display at 75fps. If you watch mostly NTSC stuff, keep it at 60fps. TFTs don't flicker anyway, so there's usually no problem with keeping the framerate at the lower end.

---

### Post by sebz2005 on 2007-05-25
Well using Ogle it works fine. I just can't change the display settings in it.
Very odd.

---

