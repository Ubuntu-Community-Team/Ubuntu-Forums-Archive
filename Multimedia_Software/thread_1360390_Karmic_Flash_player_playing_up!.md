---
title: "Karmic Flash player playing up!"
date: 2009-12-20
forum: Multimedia Software
---

### Post by Zeedok on 2009-12-20
I upgraded one of my systems to 9.10 Karmic on the weekend and among a few other wrinkles that I have been ironing out, I am having trouble with embedded flash.

My system:
9.10 (32bit)
flashplugininstaller installed (gnash defintately not installed)
The flash player version is the current one (10.0.42.34)

My problem:
YouTube plays the video without problems, but sometimes when you navigate away from that tab firefox hangs (System Monitor shows that Firefox is on a futex-wait).  On the other hand, some other video sites (eg Vimeo, and others) do not play the video properly - the playback starts for 2-3 seconds, then stops again.  If you move the cursor it will start, but then stop again after 2-3 seconds).

I have the same player version, firefox and OS version on my laptop where everything plays perfectly.

I have verified the location (and symbolic links) of the libflashplayer, and as I said the video actually plays in YouTube, so I'm not sure what else I can check.

Any suggestions would be gratefully received.

---

### Post by AkiraBergman on 2009-12-20
This is easy if you have the Ubuntu 9.10 AMD64 version. Unfortunately the installed Flash is no good. Just uninstall it with Synaptic and install the 64 bit version available on the net by copying the .so file to the relevant directory. In my case Youtube buttons did not work sometimes.

---

### Post by Zeedok on 2009-12-20
> **AkiraBergman said:**
> This is easy if you have the Ubuntu 9.10 AMD64 version. Unfortunately the installed Flash is no good. Just uninstall it with Synaptic and install the 64 bit version available on the net by copying the .so file to the relevant directory. In my case Youtube buttons did not work sometimes.

But I am running 32bit.  Will the 64bit version of the flashplayer work?  Why does the 32bit player behave properly in my laptop (same version on Karmic) and not on my other PC?

---

### Post by AkiraBergman on 2009-12-20
Then this is a different problem. Maybe you have RAM memory problems.

---

### Post by Zeedok on 2009-12-20
I have 4gb of RAM. Worked perfectly before the upgrade

---

### Post by HappyFeet on 2009-12-20
Did you "upgrade", or do a clean install of karmic?

---

### Post by Zeedok on 2009-12-21
Upgrade.

---

### Post by Zeedok on 2009-12-22
So I've had a chance to do some more digging.  It would seem to be a problem with the flash player plugin, because:

1.  Navigating away from Youtube or another video site causes the browser to hang and system monitor indicates a "futex-wait"
2.  The same thing happens in Chrome and Epiphany, so it probably isn't a problem with firefox per se, also firefox seems OK with the flash plugin uninstalled
3.  The problem has persisted despite my efforts to "apt-get remove --purge", "apt-get autoremove" firefox, flashplayer and flashplayer-installer . . . and manually deleting "libflashplayer.so" (and symbolic links to it) wherever I could find it, followed by a reinstall of the necessary packages

The weird thing is that the same software worked on my upgraded Karmic laptop, which (for unrelated reasons) I have just done a clean install on (and again everything works fine).

If it is a problem with flash player, surely I can't be the only one??

---

### Post by AkiraBergman on 2009-12-22
Have a look at this (if you haven't already);

[http://ubuntuforums.org/showthread.php?t=1358591&highlight=flash+problem](http://ubuntuforums.org/showthread.php?t=1358591&highlight=flash+problem)

---

### Post by Zeedok on 2009-12-22
I'll go through all the comments, but I'm running 32bit firefox with the standard 32bit plugin, so I'm not sure how much of it will apply.

---

### Post by AkiraBergman on 2009-12-22
Maybe you should try a clean install of 9.10.

---

### Post by Zeedok on 2009-12-22
Might have to, was hoping to avoid it though.

---

### Post by Zeedok on 2009-12-22
I installed swfdec, which is supposed to be a free open source adobe flash player alternative.  Not *all* video sites seem to work, but Firefox works well with iut and it does the main sites, so all is good.

---

### Post by Zeedok on 2009-12-28
I think I have narrowed this problem down to an issue with my sound output.  I have [posted this other thread]("http://ubuntuforums.org/showthread.php?p=8569769#post8569769") which was initially about video playback in movie player, but I have since realised that both problems are caused by my audio setup.  

I'd be grateful for any suggestions (in the other thread if you don't mind).

Thanks.

---

