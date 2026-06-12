---
title: "Unable to initialize SDL: No available video device"
date: 2008-02-21
forum: Multimedia &amp; Video
---

### Post by fredmv on 2008-02-21
Hopefully this isn't too re-hashed of a topic, but I've done my fair share of searching, and here's where I've arrived at.    So, SDL-based games used to work for me, but all of a sudden whenever I try to launch one, I get the following error:

```
root@viper:/etc/X11# sauerbraten
init: sdl
[color=red]**Unable to initialize SDL: No available video device**[/color]
root@viper:/etc/X11# 
```

So far, I've: [list=a][*]installed *libsdl1.2debian-all * (originally via synaptic and then I tried compiling the source); [*] tried an *xhost + localhost* which appears to be a common fix for this kind of problem; [*] checked out my xorg.conf which looks correct to me;[/list]  all to no avail.    

The most relevant thread I found, FWIW, was this one: [http://ubuntuforums.org/showthread.php?t=16110](http://ubuntuforums.org/showthread.php?t=16110) although that was back in 2005 and evidently his problem was fixed by upgrading to Hoary.   In this Gutsy-era, I'm really wondering what the solution is.

Thanks everyone.

---

### Post by fredmv on 2008-02-21
Bumping this.    Any ideas guys?

---

### Post by fredmv on 2008-02-22
OK, this seems to work.--almost.  I suppose I should've "RTFM" a little bit more.   Directly from the libsdl website (libsdl.org):

> Q:	I get the error: "no video devices available"
A:	SDL doesn't use the X11 video driver if it can't open the X display, and if no other drivers are available, it will report this error.
To fix this, set your display environment variable appropriately:
sh: DISPLAY=:0 ; export DISPLAY
csh: setenv DISPLAY :0
If you still have problems, try running xhost + localhost
Finally, if all those didn't work, and you built SDL from source, make sure that you have the X11 development libraries installed, otherwise you'll get a version of SDL that doesn't include X11 display support. After you install the X development libraries, you need to "make clean" and then rerun the configure and build process.

I tried everything there except the instillation of X11 development libs, which evidently are needed if you are building SDL from source.  These are are found in a package called **xorg-dev**.   So, after installing xorg-dev, and then recompiling SDL from source, *some* SDL-based stuff seems to work.      However, for other games (e.g., neverball) now I get a new error:   > fred@viper:/etc/X11$ neverball: X11 driver not configured with OpenGL

---

