---
title: "use 720p resolution in 8.04"
date: 2008-08-08
forum: Multimedia Software
---

### Post by gggerard on 2008-08-08
Hi there,

I have just done a fresh installation of ubuntu 8.04. I have an ATI 9200.

**I need:** to change my resolution of 1280x1024 to a 720p resolution, cause this is the panasonic plasma resolution that I need when I connect the DVI-pc to the HDMI-panasonic.

**Attempt1:** go to screen resolution tool. There the 720p resolution does not appears.

**Attempt2:** try something with xorg.conf, but with 8.04 that file does not provide many information.

**What I usually do:** I change to windows, there I have an ATI tool that lets me change to the 720 ress. Then unplug the monitor and plug the panasonic HDMI to the pc DVI. And I see the PC on the panasonic at the good resolution.

**What I ask:** Can I do the same in ubuntu? I know that the ATI driver is obsolete for my 9200, is the free driver providing such resolution possibilities?

Any help is obviously welcome. Thanks!

---

### Post by eye208 on 2008-08-08
Ubuntu 8.04 is designed to recognize the resolution of any connected display device automatically. This is done via the [Display Data Channel](http://en.wikipedia.org/wiki/Display_Data_Channel). DDC was introduced in the 1990s as part of the VESA standard. It works through VGA, DVI and HDMI connectors. It should be supported by any display device on the market.

Just connect the device and start up the computer.

---

### Post by gggerard on 2008-08-08
Thanks for reply,

Then what should be the procedure?

1: unplug the monitor and plug the panasonic. Since the panasonic is on another room, things are complicated.
2: then what? reconfigure xserver? Which would be the command?
3: expect that the resolutions detected include the 720p specs

Is that correct?? I would need how to autodetect the resolutions.

---

### Post by gggerard on 2008-08-08
Uoh, sorry, I didn't read the "Just connect the device and start up the computer".

Since the panasonic is in another room, to manage gnome is very unconfortable. I guess that restarting the xserver would suffice?

If you were me, what would you do? (And buying a nokia n810 to manage the computer by wifi is not a valid option:)

---

### Post by gggerard on 2008-08-08
I am thinking about ... to restart the computer is not a valid option since what I am looking for is a winning alternative to windows. And I always can restart with windows, that allows me to work with the monitor and unplug it/plug the panasonic when the VLC is paused, not since the begining.

So I need something better. Since this is linux and as far as I believe to know, the xserver is the one involved in establishing the correct resolution of the screen, so restarting the graphic server would be a solution, wouldn't it?

However, in previous ubuntues, one could write something in xorg.conf trying to include a particular resolution. My hope was that in 8.04, this could be solved graphically. Instead, I observe that the xorg.conf file possibilities have dissapeared (at least for a old-newby like me), since the file is now empty-like.

But I suspect that in 8.04 one can still configure xorg.conf. Is there any other file involved? How can I add a 720p resolution to the monitor then?

Finally, is a graphical resolution manager going to be included in ubuntu future releases? One that allows you to work with any resolution that you ATI 9200 in this case allows.

Thxs.

---

### Post by eye208 on 2008-08-08
As far as I know, DVI is not hot-pluggable (unlike USB). You may damage your monitor or graphics card in the long run if you connect them while the computer is turned on.

If you don't want to restart the computer, try restarting X.org instead by pressing Ctrl-Alt-Backspace. Maybe this will retrigger the autodetection.

---

### Post by gggerard on 2008-08-08
Jesus christ, not hot-pluggable?? Ok. Now I've changed my configuration, now the monitor is connected by VGA and the panasonic through DVI. Panasonic is detected as well as its resolution, so problem solved.

The problem is that when I maximise the movie player, in the monitor I see it well centered, but in panasonic not. I think this is not easy to be solved ...

But anyway, the main problem is almost solved. I do not need windows to see movies with my panasonic. Wonderful!!!

Thanks a lot.

---

