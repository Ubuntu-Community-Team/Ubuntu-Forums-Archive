---
title: "gdm won't start -- upgrade gone bad"
date: 2006-08-06
forum: Multimedia &amp; Video
---

### Post by backdoc on 2006-08-06
In a nutshell, Dapper won't start up into X after installing an update yesterday (8/5/2006).  The kernel versions went from 2.6.15-25-386 to 2.6.15-26-386.

At this point, I can start xfce4 by running startxfce4 from the command prompt.  I get the Nvidia logo.  I ran glx-gears and it's working, too.  But, rebooting fails to start gdm.  And, I can't start it manually.  The error I'm getting is that it can't find /usr/lib/xorg/modules/xgl/libglx.so (or maybe it's libxglx.so -- my ctrl+alt+F keys aren't working now, so I can't go look at the error).  Anyway, I have both modules.  But, the libxglx.so is the only one in /usr/lib/xorg/modules/xgl. [EDIT -- see the error messages below]

Here are some of the things I've tried:

The first thing I had to fix was grub.  For some reason, the upgrade had it pointing to the wrong partitions.  That's fixed now.

Once that was going, I could only get X started if I booted into my old kernel.  But, it wasn't right.  The title bar was missing (which is something I've seen and fixed when setting up Xgl).  But, I wasn't going to be satisfied fixing the title bar problem and booting into the old kernel, so I set out to get X working with the new kernel.

I did a variety of apt-get updates, removes and installs of the usual suspects [nvidia-kernel-common, nvidia-glx (and it seems like a third package that I'm forgetting right now)].  I did dpkg-reconfigure xserver-x?? (whatever that was).  And, tried running the envy script (which cleared up the API mismatch I was getting).  

OK.  So, where do I go from here?  I haven't tried starting Gnome directly (where Xgl was working).  So, maybe I should run through the Xgl configuration.

What do you think?

[EDIT -- Here is the error I get when trying to start gdm:

[INDENT]dlopen: /usr/lib/xorg/modules/xgl/libglx.so: cannot open shared object file: No such file or directory

Fatal server error:
No GLX modules loaded
dlopen: /usr/lib/xorg/modules/xgl/libglx.so: cannot open shared object file: No such file or directory

FatalError re-entered, aborting
No GLX modules loaded[/INDENT]

Here is the error if I create a symlink in /usr/lib/xorg/modules/xgl that points to libglx.so in another directory:
[INDENT]
dlopen: /usr/lib/xorg/modules/xgl/libglx.so: undefined symbol: xf86fprintf

Fatal server error:
No GLX modules loaded
dlopen: /usr/lib/xorg/modules/xgl/libglx.so: undefined symbol: xf86fprintf

FatalError re-entered, aborting
No GLX modules loaded
[/INDENT]

---

### Post by backdoc on 2006-08-06
The situation has improved.  I can start gdm and get into Gnome.

I followed the instructions at:
[http://www.ubuntuforums.org/showthread.php?t=222034&highlight=nvidia](http://www.ubuntuforums.org/showthread.php?t=222034&highlight=nvidia)

The title bar is missing, again.  But, I'm using the new kernel.

Another weird thing is that my cursor acts like its had too much caffeine.  It's blinking unusually fast while I type this.  I'm a little nervous that I got so many packages from a domain called "beerorkid".  Hmmm.

Oh.  And, my F keys don't work.

---

### Post by backdoc on 2006-08-06
I added "gnome-wm" to the startup scripts, and that seems to have taken care of the F keys and my title bar.

I don't have any xgl eye candy and my cursor is still blinking like a wild man, but it seems to be getting there.  I think I'll try rebooting, now.

---

