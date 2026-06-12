---
title: "Poor performance with flash"
date: 2008-07-25
forum: Multimedia Software
---

### Post by Nightmist on 2008-07-25
Hello,

I am getting pretty poor performance with flash videos. Small ones, like on YouTube play pretty good. They just stutter some times. But after a while performance decreases, and I sometimes have to restart the browser to fix the problem (severe stuttering). The full screen feature doesn't work with YouTube. The full screen just flashes then it's back to the normal, small video.

For other sites where fullscreen works, or the flash video is presented in a larger format than YouTube, the performance is generally worse, with choppyness, stuttering and tearing of the image. Normal video performance (.avi files etc.) is much better than Windows, so it's sad that flash has so bad performance.

So... is there anything I can do to improve this?

Thanks.

---

### Post by ajgreeny on 2008-07-25
You could try the flash 10 beta 2 which I have installed manually, and seems to work better than flash 9.

Go to [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) and download the tar.gz then unpack it and manually copy the libflashplayer.so file to /usr/lib/flashplayer-nonfree as root (gksudo nautilus) after first renaming the current version  as a backup (libflashplayer.so9~).  If it doesn't suit you for some reason you can restore the v9 player easily.

---

### Post by Nightmist on 2008-07-25
> **ajgreeny said:**
> You could try the flash 10 beta 2 which I have installed manually, and seems to work better than flash 9.

Go to [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) and download the tar.gz then unpack it and manually copy the libflashplayer.so file to /usr/lib/flashplayer-nonfree as root (gksudo nautilus) after first renaming the current version  as a backup (libflashplayer.so9~).  If it doesn't suit you for some reason you can restore the v9 player easily.

So my performance issues are pretty normal with flash 9?

---

### Post by Nightmist on 2008-07-26
Maybe I should add that I'm using Opera 9.5 if that helps.

---

### Post by akudewan on 2008-07-26
I always had poor flash performance with my old PC. Probably had something to do with the graphics card being toast ;)

Can you post your CPU, RAM, and graphics card specs ?

---

### Post by Nightmist on 2008-07-26
> **akudewan said:**
> I always had poor flash performance with my old PC. Probably had something to do with the graphics card being toast ;)

Can you post your CPU, RAM, and graphics card specs ?

AMD Athlon 64 3700+
2 GB RAM
GeForce 8800 GT

---

### Post by akudewan on 2008-07-26
Wow, an 8800!! :) Doesn't seem like a slow-pc problem

You could try out firefox to see if its a browser-specific problem. There seem to be some [bugs]("http://www.google.co.in/search?source=ig&hl=en&rlz=&q=flash%20slow%20in%20opera&meta=") with flash and Opera.

---

### Post by Nightmist on 2008-07-26
> **akudewan said:**
> Wow, an 8800!! :) Doesn't seem like a slow-pc problem

You could try out firefox to see if its a browser-specific problem. There seem to be some [bugs]("http://www.google.co.in/search?source=ig&hl=en&rlz=&q=flash%20slow%20in%20opera&meta=") with flash and Opera.

Full screen flash videos are still tearing and choppy on firefox, so I don't know what the problem might be :/

Is it possible to re-install it somehow, if that might work for some strange reason? :o

---

### Post by Melcar on 2008-07-26
Flash just sucks.  Slow and choppy here as well:

AMD X2 @ 3GHz
4GB RAM
HD3850

Sometimes it even freezes my desktop.  Works for the most part, mostly with small windowed movies.

---

### Post by Nightmist on 2008-07-26
> **Melcar said:**
> Flash just sucks.  Slow and choppy here as well:

AMD X2 @ 3GHz
4GB RAM
HD3850

Sometimes it even freezes my desktop.  Works for the most part, mostly with small windowed movies.

Ah, okay. So it's just not me, then. Most streaming sites use flash, though. I guess I'll stick with small windows, then.

---

### Post by dizee on 2008-07-26
i have similar problems with flash in opera in xubuntu.

firefox seems to be a bit better for some reason, though i haven't extensively tested it.

i'm hoping that when flash 10 comes out the experience will be a lot smoother.

---

### Post by pi.phage on 2008-08-01
Yeah, I have the same problems, running it in firefox, ubuntu.

---

### Post by Greenwidth on 2008-08-03
I have this problem too, I can play small window vids fine but when maximised it shears and stutters.
One thing I have noticed is that if you (can) enter the address of the swf into the address bar it plays better:
Try:
[http://www.flashcomguru.com/apps/fullscreen_player9/fullscreen.html](http://www.flashcomguru.com/apps/fullscreen_player9/fullscreen.html) (and maximise it)
then try:
[http://www.flashcomguru.com/apps/fullscreen_player9/fullscreen.swf](http://www.flashcomguru.com/apps/fullscreen_player9/fullscreen.swf)
It's not properly fullscreen but runs better (for me anyway)

---

### Post by eye208 on 2008-08-03
The reason for choppy video in Flash 9 is simply because the Flash plugin does not yet use the video acceleration features of the graphics card. This is why you get tearing even with the latest Nvidia cards. With more and more video sites using Flash video in HD formats, this has become a problem.

Flash 10 is going to fix this. There is an installer for Flash 10 in the backports repository, but be warned, it's still crash-prone, and video is displayed with some strange artifacts. In fact it crashed so frequently here that I had to roll back to Flash 9.

Thanks to Ubuntu's package manager, switching between the versions is pretty simple, so you may want to give it a try.

---

### Post by gandaran on 2008-08-03
> The reason for choppy video in Flash 9 is simply because the Flash plugin does not yet use the video acceleration features of the graphics card. 

right click the flash video window » settings, uncheck the enable hardware acceleration box.

---

### Post by eye208 on 2008-08-03
> **gandaran said:**
> right click the flash video window » settings, uncheck the enable hardware acceleration box.
I did. No change. What is it supposed to do?

---

### Post by eye208 on 2008-08-03
> **eye208 said:**
> There is an installer for Flash 10 in the backports repository
Correction: The installer in hardy-backports has been rolled back too. If you want to test Flash 10 beta, you have to install it manually. Probably the best place to put it is the ~/.mozilla/plugins folder (instead of /usr/lib/mozilla/plugins).

---

### Post by billgoldberg on 2008-08-03
Flash on linux sucks.

The flash player 10 beta 2 runs a bit better, but still not great.

---

### Post by stmiller on 2008-08-19
> **gandaran said:**
> right click the flash video window » settings, uncheck the enable hardware acceleration box.

Thanks that helped performance for me. (Asus Epc - Intel graphics)

---

### Post by xrecar on 2008-11-03
I still have very poor performance of flash on 8.10, I actually use the Totem youtube plugin instad of firefox. This sucks.

---

### Post by Allegretto on 2008-11-03
8.10 seems to have made Flash a lot slower for me. With 8.04 it worked pretty okay using Flash 10. Now that I've upgraded to 8.10, playing a Flash video lags my whole system (still using Flash 10). I'm not sure what the problem is to be honest.

---

