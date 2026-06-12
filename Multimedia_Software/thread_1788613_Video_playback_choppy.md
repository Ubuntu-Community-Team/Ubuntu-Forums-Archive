---
title: "Video playback choppy"
date: 2011-06-22
forum: Multimedia Software
---

### Post by rau on 2011-06-22
This has been an on-going problem I've had when trying to watch video in linux. I'm going to go ahead and state a list of important points to possibly rule out a lot of things that it's not. For the record, by "choppy" I mean noticeably low frame rate, as in 30FPS videos looking as if they are discarding more than half of the frames. 

*This happens in lots of distributions, not just Ubuntu.
*I have a AMD HD5850 and am using the latest proprietary drivers, problem exists with older drivers too.
*I have a desktop computer with a 4GHz processor, without any type of speed stepping enabled. 
*I can play 60FPS 1080p video in Windows without any issues, but in Linux even 360p is choppy.
*Problem happens both when using Compiz and when using Metacity with or without compositing enabled.
*Problem happens with ALL video player applications EXCEPT for flash videos played inside a web browser.
*Problem goes away if I move my mouse around on top of the video player, come back when I stop.
*Problem happens with ALL video formats and from ALL types of sources (internal HDD, external HDD, internet streams, etc)

I would really like a working solution to this problem as video playback in Linux has been near impossible up to this point with my current computer. :mad:

---

### Post by Nick29 on 2011-06-23
rau

I have the same problem in Ububtu 11.04. DVD playback is jerky.

I had no problem with dvd play in Ubuntu 10.10 (though it took me 3 weeks and a number of re-installs to get to play dvds at all in 10.10 compared to 1 hour in 11.04). I do not know what codecs I have installed in 11.04 or where to find them to remove and re-install fresh ones.

Nick29

---

### Post by handy on 2011-06-23
This may be of assistance to you:

[http://ubuntu4beginners.blogspot.com/2011/04/unity-choppy-with-ati-graphics-card-and.html](http://ubuntu4beginners.blogspot.com/2011/04/unity-choppy-with-ati-graphics-card-and.html)

---

### Post by rau on 2011-06-23
> **handy said:**
> This may be of assistance to you:

[http://ubuntu4beginners.blogspot.com/2011/04/unity-choppy-with-ati-graphics-card-and.html](http://ubuntu4beginners.blogspot.com/2011/04/unity-choppy-with-ati-graphics-card-and.html)

As I pointed out in my list of points, this happens in ALL window managers, so anything regarding Compiz settings is not the solution. Plus they are referring to a choppy UI, and my UI is just dandy, it's only video playback.

---

### Post by handy on 2011-06-24
> **rau said:**
> As I pointed out in my list of points, this happens in ALL window managers, so anything regarding Compiz settings is not the solution. Plus they are referring to a choppy UI, and my UI is just dandy, it's only video playback.

I said *"may"*.

---

### Post by rtv_73 on 2011-06-25
Same problem here with Radeon HD 5450 1GB. Very annoying and headache giver :(

Please let us know if you have found a solution.

---

### Post by Nick29 on 2011-06-26
handy

I have ATI onboard graphics (4290) so tried your link. It worked, and the video playback improved greatly. But is it just me or is the video payback just not quite as good as 10.10?

Nick29

---

### Post by rtv_73 on 2011-06-26
Handy,

I followed the link and my video playing is not choppy anymore. It is more viewable now, but now show lots horizontal lines like unsync pieces of video.

Looks like it is an ATI issue in Ubuntu. Hopefully a new driver will correct all the problems.

Thanks!

---

### Post by handy on 2011-06-27
You could try the later driver stack as provided via the xorg-edgers ppa.

There is a how-to down in the Ubuntu Stuff: section of the first post here:

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

---

