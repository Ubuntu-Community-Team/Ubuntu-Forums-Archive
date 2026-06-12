---
title: "smplayer full screen"
date: 2008-03-13
forum: Multimedia &amp; Video
---

### Post by Robbyx on 2008-03-13
I am using a dual monitor nvidia drive in Gutsy.

I would like some help in reducing the size of the screen when playing poor bandwith videos. It is defaulting to large screen.  Smplayer is not responding to any settings in the size drop down menu.

I can not see home/.smplayer which is where I expected to find the config files. Does anyone know where the config files are now kept?

Robin

---

### Post by rvm4000 on 2008-03-13
> **Robbyx said:**
> I am using a dual monitor nvidia drive in Gutsy.

I would like some help in reducing the size of the screen when playing poor bandwith videos. It is defaulting to large screen.  Smplayer is not responding to any settings in the size drop down menu.

The size of the video can't be changed in fullscreen mode. I don't know anyway if this is what you mean.

> **Robbyx said:**
> I can not see home/.smplayer which is where I expected to find the config files. Does anyone know where the config files are now kept?

The configuration files are in ~/.smplayer/ (unless you're using a very old version, in that case the config file is ~/.qt/smplayerrc)

---

### Post by Robbyx on 2008-03-14
I was trying to watch a very poor quality video. It needed to be very small ie not full screen. It kept launching in full screen and I found I could not make it be small.

As for the control files I can not see them. I have just completely uninstalled SMP and then reinstalled it. I can see a directory for mplayer but not smplayer. I installed SMP via synaptec.

I guess my settings are not being retained and that is why  I wanted to find the config files.

Robin

---

### Post by rvm4000 on 2008-03-14
What version of smplayer are you using?

The latest one is 0.6.0rc2. Try to update if you have an older version:

[http://smplayer.sourceforge.net/downloads.php](http://smplayer.sourceforge.net/downloads.php)

---

### Post by Robbyx on 2008-03-14
I have just installed both packages. I do not know what you have done to it, but the picture quality seems so much brighter and sharper. It is a great improvement. Thank you.

Is there a way that I could update my repositories so that Ub will automatically update with the latest?

Robin

---

