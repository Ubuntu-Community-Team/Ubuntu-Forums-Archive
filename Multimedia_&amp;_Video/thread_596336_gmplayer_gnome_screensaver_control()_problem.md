---
title: "gmplayer gnome_screensaver_control() problem"
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by HeinekenPissr on 2007-10-29
I am running UBUNTU 7.10

When I run a movie in mplayer and pause/stop and then restart the video i am prompted with an error window that says "gnome_screensaver_control()".

I can get rid of this error by going into gmplayer Preferences-->Misc--> and unchecking the "Stop Xscreensaver" box.  However when unchecking this the annoying screensaver pops up  many times throughout a movie.

The Terminal output when i run gmplayer is the following:

 MPlayer 2:1.0~rc1-0ubuntu13 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.53GHz (Family: 15, Model: 2, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
[B]xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled[/B]
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.


Even though i get this error upon starting gmplayer the stop xscreensaver function still works and i don't get the annoying screensaver during a movie but i can't pause the movie without getting this error and having to restart the movie.

I would like to fix this while keeping the stop xscreensaver function enabled.

By the way are Gnome screensaver and Xscreensaver the same?

Thanks in advance

---

### Post by HeinekenPissr on 2007-10-29
Let me know if any additional information is needed.

---

### Post by amiga_os on 2007-10-30
I'm getting this same error trying to play DVDs in MPlayer.  Totem GStreamer has failed to install the right codecs for me to play DVDs, and installation of the ugly set (which it kept trying to install) hasn't worked as Totem doesn't recognise them.

Mplayer opens the DVD disc, then I get this gnome_screensaver_control() error, then I can't even begin watching the DVD!  I'm going to try some fixes - has anyone else experienced this?  If so I may file a bug in Launchpad.

---

### Post by amiga_os on 2007-10-30
Just to confirm this is a registered bug, with a patch posted, but the bugs not even triaged, and still has "new" status:

[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/108785]("https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/108785")

---

### Post by NT4usB on 2007-10-30
What happens if you kill the gnome-screensaver process? Still get popups?

---

### Post by HeinekenPissr on 2007-10-30
@NT4USB > "What happens when you kill the gnome screensaver process?"


As I said in the initial post  I can get rid of this error by going into gmplayer Preferences-->Misc--> and unchecking the "Stop Xscreensaver" box. However when unchecking this the annoying screensaver pops up many times throughout a movie.

If you meant what happens if I disable my screen saver altogether then i don't know.  I am not interested in solving one problem by creating another.

I found a TEMPORARY WORKAROUND

Go into synaptic an install the smplayer frontend
-this still uses the mplayer engine but with a different front end that is pre-configured to work perfectly out of the box.  I am still interested in the solution to this problem but i am more than happy with this workaround.

---

### Post by old_salt on 2007-11-01
I also am running 7.10 Gutsy but with KDE and receive the same dialog window about Gnome Screensaver. I disabled the KDE Screensaver and it still appears. Would love it if I didn't have to have half ofg gnome installed on top my KDE version please. 

In any case...... Same issue here with KDE.

I can confirm as per HeinekenPissr  posting that installing smplayer or kmplayer for KDE resolves the issue. I even restored the screensaver settings I had originally and no issues.

weird !!!!!!

---

### Post by rvm4000 on 2007-11-01
There's an explanation.

It seems that gmplayer pops up error/warning messages from mplayer, while smplayer (and probably kmplayer) ignore them.

But if you take a look at the mplayer log, you'll see that those warnings are still there.

---

### Post by old_salt on 2007-11-02
however.... why am I getng them while using KDE (Kubuntu) still?

---

### Post by rvm4000 on 2007-11-02
I have no idea.

Anyway [here](http://launchpadlibrarian.net/10167946/mplayer-gnome-screensaver-control-fix.patch) is a patch for mplayer which will supposedly fix the problem. Has anyone tested it?

---

### Post by old_salt on 2007-11-02
> **rvm4000 said:**
> I have no idea.

Anyway [here](http://launchpadlibrarian.net/10167946/mplayer-gnome-screensaver-control-fix.patch) is a patch for mplayer which will supposedly fix the problem. Has anyone tested it?

I don't know how to apply a diff or a patch like that but would love to learn if someone could provide some instructions or a quick gouge. Nothing like learning something new.!!!![http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

### Post by crouton on 2007-11-03
Problem with the patch is it expects the gnome_screensaver.c file, which as far as I can tell is the uncompiled version of the utility found under /usr/bin.  So I'm confused how this patch is supposed to be applied to anything.

---

### Post by Epilonsama on 2007-11-03
Thank God IM not the only one with this [problem]("http://ubuntuforums.org/showthread.php?t=601114")!, it seems that dvd playback sucks in gutsy, cuz i was trying to play it on totem and it sucked and vlc was extremely crappy, so in the mean time im staying on mint.

(Even tough gutsy did boot a lot faster, but this bug is a serious one)

---

### Post by rvm4000 on 2007-11-03
> **crouton said:**
> Problem with the patch is it expects the gnome_screensaver.c file, which as far as I can tell is the uncompiled version of the utility found under /usr/bin.  So I'm confused how this patch is supposed to be applied to anything.

The file to patch is one of the sources of mplayer.

Here is how to do it:

```

cd /tmp/
apt-get -d source mplayer
dpkg-source -x mplayer_1.0~rc1-0ubuntu9.1.dsc
cd mplayer-1.0~rc1/

```

The patch is a modification of only one line, so it's faster to do it by hand:

edit file libvo/gnome_screensaver.c, go to line 59 and change it:
```

                              cookie, G_TYPE_INVALID);

```
to
```

                              cookie, G_TYPE_INVALID, G_TYPE_INVALID);

```

Now
```

dpkg-buildpackage -rfakeroot

```

That would recompile mplayer and create a deb package, ready to install.
(I haven't done myself 'cos it asks me to install a lot of packages)

BTW, I have no idea if this patch would really fix the problem.

---

### Post by afecelis on 2007-11-20
After trying out Ubuntu and Kubuntu, I'm now using Xubuntu for its clean desktop and light resource use. In this case, Heineken's tip of unchecking the screensaver option in preferences/misc worked great! thanks! ;)

---

### Post by wzwilliam on 2007-11-22
> **afecelis said:**
> After trying out Ubuntu and Kubuntu, I'm now using Xubuntu for its clean desktop and light resource use. In this case, Heineken's tip of unchecking the screensaver option in preferences/misc worked great! thanks! ;)

same here. probably it has something to do with the mplayer's update which went out a few days ago.

---

### Post by misha1983 on 2008-01-06
> **rvm4000 said:**
> The file to patch is one of the sources of mplayer.

Here is how to do it:

... snip...

BTW, I have no idea if this patch would really fix the problem.

I followed your instructions and the problem seems to be fixed.  Thanks!

---

### Post by A$h X on 2008-01-08
I have the same problem but I don't even the file libvo/gnome_screensaver.c on my system! I also noticed it seems to kill firefox downloads in progress when it occurs. I'll try and disable the screensaver manually to see if it helps.

---

### Post by rvm4000 on 2008-01-09
I think the screensaver code in mplayer has been changed recently.

You should try to compile mplayer from svn and see if the problem has been fixed.

---

