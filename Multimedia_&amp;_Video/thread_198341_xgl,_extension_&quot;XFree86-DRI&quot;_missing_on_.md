---
title: "xgl, extension &quot;XFree86-DRI&quot; missing on display &quot;:1.0&quot;."
date: 2006-06-17
forum: Multimedia &amp; Video
---

### Post by enkidu75 on 2006-06-17
Hi all. I've read a LOT of threads around this issue, but I'm don't have a lot of clarity on exactly what is going on, and I'm hoping someone can tell me if I actually have a problem or not.



I've intalled xgl and compiz on my laptop, running dapper. I'm using the fglrx drivers, and if I start a session without xgl, when I run fglrxinfo everything looks fine.

Now if I start xgl like this:

```
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1
```

Xgl and compiz work fine- everything is hunky dory. However if I do fglrxinfo

I get
```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600 Generic
OpenGL version string: 2.0.5814 (8.25.18)
```

Running fgl_glxgears give me

```
Using GLX_SGIX_pbuffer
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Error: couldn't get fbconfig
```

The xgl [faq]("http://swik.net/Xgl/Xgl+FAQ") says that you can't run programs that use 3d acceleration under xgl. Is this why I can't do this? Is anyone else out there running xgl, but is getting OK output from  fgl_glxgears?

Cheers

---

### Post by alejandrops on 2006-06-19
HI! im in the exact same situation as you are. did you found any answers?
everything seems to work OK (XGL, Tux racer...) but same error in fgl_glxgears and 

```

alejandrops@alejandrops-laptop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400 Generic
OpenGL version string: 2.0.5814 (8.25.18)

```

thanks for your time!

---

### Post by didobuntu on 2006-06-20
Hi ,
I have exactly the same problem with my laptop. My video card is an ATI Mobility X1600 ..

when running fglrxinfo | grep rendering ... answer is : direct rendering = No ...

But but when I start  with gnome (with no Xgl/Compiz) all is ok

---

### Post by Eleaf on 2006-06-20
This is NORMAL.  When using xgl, the x server takes over direct rendering.  That means that none of your apps will have direct 3d rendering, and therefore will show that there is no dri.

This is normal, the only way to get around this is to launch a seperate xorg session so you can have direct rendering for your applications.

=)

---

### Post by enkidu75 on 2006-06-21
Hmm I suspected as much. It doesn't really bother me all that much- most of the GL screensaver run quite nicely on my desktop. However Google Earth is slow slow slow. If I start a normal gnome session it works fine.

Guess that's the price I pay for all that eye candy :(

---

### Post by JepUbu on 2007-10-24
Hi!

The only thing I can do to display fgl_glxgears is to display it on :0.0 with the following command```
DISPLAY=:0.0 fgl_glxgears
```
This opens a window without borders, be ready to kill it because you cannot control it.

For other applications like games that can be quit from the window there isn't any problem.

I hope it will be useful.

---

