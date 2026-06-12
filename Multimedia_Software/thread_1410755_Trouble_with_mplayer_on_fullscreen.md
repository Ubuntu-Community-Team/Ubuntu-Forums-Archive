---
title: "Trouble with mplayer on fullscreen"
date: 2010-02-19
forum: Multimedia Software
---

### Post by mike.franky on 2010-02-19
Hi,

I have just installed mplayer and everything seems to work fine until i try to go fullscreen. When i do, the actuall size of the video stays the same and the rest of the screen is filled with a black border. I have seen the main problem by many people, and the solution they all found was to change the driver from x11 to xv. 

In my case however, the only driver working is x11. Anything else gives the following error

> Error opening/initializing the selected video_out (-vo) deviceThis is also quite wired since the output of mplayer -vo help says that all the drivers are available.

Any help would be very much appreciated.

---

### Post by andrew.46 on 2010-02-19
Hi mike,

> **mike.franky said:**
> I have just installed mplayer and everything seems to work fine until i try to go fullscreen. When i do, the actuall size of the video stays the same and the rest of the screen is filled with a black border. I have seen the main problem by many people, and the solution they all found was to change the driver from x11 to xv.

Try running your video from the commandline with the following options:

```
mplayer -vo x11 -zoom -fs *my_video.mp4*
```

where you will of course need to replace *my_video.mp4* with the name of your own file.

Andrew

---

### Post by mike.franky on 2010-02-22
Thanks very much. That worked perfectly. Not that it really matters but is there a way to make that work with gmplayer?

---

### Post by andrew.46 on 2010-02-22
Hi mike,

> **mike.franky said:**
> Thanks very much. That worked perfectly. Not that it really matters but is there a way to make that work with gmplayer?

I have to admit that I do not use gmplayer, however if you have a look at smplayer you should be able to alter the options quite easily and the interface is a lot better...

All the best,

Andrew

---

