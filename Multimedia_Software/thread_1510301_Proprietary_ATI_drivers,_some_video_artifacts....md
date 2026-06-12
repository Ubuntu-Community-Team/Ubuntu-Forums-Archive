---
title: "Proprietary ATI drivers, some video artifacts..."
date: 2010-06-15
forum: Multimedia Software
---

### Post by zlapidus on 2010-06-15
Hello all,

New user of Ubuntu, running 10.04, using a computer with a Radeon HD 4850. I installed the Proprietary ATI drivers with the Hardware Drivers tool under the System>Administration menu. I've found that when viewing video (full screen and otherwise) there are sometimes weird artifacts in both mplayer and vlc; at moments with fast motion, like fast camera pans, etc, there is sometimes a "tearing" or weird line artifacts that sort of "roll" up and down in a small area. This doesn't really persist, it's mostly during scenes with fast motion, and seems to persist on all the video output modules in mplayer I tried. I could take a screenshot, but what it seems like what is happening is that there is somewhat of an unevenness of successive lines of pixels, that cause a weird, minor, but noticable glitch.

It's not terrible; pretty minor, and I'm still watching video, but it is annoying to me, as I watch a lot of movies on my computer, and would feel better if this issue was absent. When I was using the open-source drivers, this issue wasn't happening -- video was completely smooth in fact, but 3d, like in glest, for instance was very slow and bad.

In ubuntu, do you basically need to choose between 2d or 3d performance if you have an ati card? I also noticed that there is a newer version of the ati drivers (8.32 and I have 8.23) than is installed automatically by ubuntu's tool, but I read the release notes, and there is no mention of improved 2d performance between the two drivers, so I've held off.

For the time being, 2d is more important to me than 3d (and compiz runs great with the open source drivers as well) so I've rolled back to the open source drivers and removed the proprietary ati drivers. Any advice on where to go from here? I was also wondering if the open source drivers would cause the card to run hotter? I'm also just worried about making sure the card stays in good shape.

Thanks very much!

---

### Post by xzero1 on 2010-06-15
Unfortunately, I think there is the video vs 3d tradeoff to make. I have not found anything that works better than the open source drivers for video. For tearing, you could try the open gl driver and enable sync to vertical refresh or XvBA, but there are other artifacts and only h.264 is accelerated. I don't think you need to worry about burning out your card but it might run a bit hotter when idle.

For XvBA:

[http://ubuntuforums.org/showthread.php?t=1385896]("http://ubuntuforums.org/showthread.php?t=1385896")

---

### Post by cbrunhaver on 2010-06-15
Many times, compizitng causes tearing as well.  YOu can try to install CompizConfig Settings Manager and them make sure that Vsynch is enabled.  Typically, you want to set the compiz framerate at twice of your refresh rate (e.g. 120 hz).  

Alternately, you can disable the desktop effects (under appearance) and see if that helps.

---

### Post by zlapidus on 2010-06-15
> **xzero1 said:**
> Unfortunately, I think there is the video vs 3d tradeoff to make. I have not found anything that works better than the open source drivers for video. For tearing, you could try the open gl driver and enable sync to vertical refresh or XvBA, but there are other artifacts and only h.264 is accelerated. I don't think you need to worry about burning out your card but it might run a bit hotter when idle.

For XvBA:

[http://ubuntuforums.org/showthread.php?t=1385896](http://ubuntuforums.org/showthread.php?t=1385896)

 Thanks a lot for the input. By the opengl driver do you mean the opengl video output setting in the video player? I tried enabling sync to vertical refresh but I don't know that it made a huge difference. I think I'm just going to opt for better video performance and use the open source drivers. By the way, is there any way to check temperature once fglrx is deleted, if I'm just using the open source drivers?

---

### Post by zlapidus on 2010-06-15
> **cbrunhaver said:**
> Many times, compizitng causes tearing as well.  YOu can try to install CompizConfig Settings Manager and them make sure that Vsynch is enabled.  Typically, you want to set the compiz framerate at twice of your refresh rate (e.g. 120 hz).  

Alternately, you can disable the desktop effects (under appearance) and see if that helps.

 Thanks for the reply. I switched desktop effects to none and watched the video run perfectly, with no tearing! I then switched it back to test, to see how obnoxious it would be to disable compiz when I wanted to watch movies, and found that I couldn't reproduce the results, even when I switched back and forth to no desktop effects. Weird behavior, huh?

---

### Post by xzero1 on 2010-06-15
> **zlapidus said:**
> Thanks a lot for the input. By the opengl driver do you mean the opengl video output setting in the video player? I tried enabling sync to vertical refresh but I don't know that it made a huge difference. I think I'm just going to opt for better video performance and use the open source drivers. By the way, is there any way to check temperature once fglrx is deleted, if I'm just using the open source drivers?

Enable "vsync always on" in fglrx control panel then try something like "mplayer -vo gl ...".

I could not get vsync to work in fglrx without the open gl driver. Never tried it with Lucid, since I now use the open source driver exclusively.

---

