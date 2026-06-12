---
title: "OpenGL and X BadAlloc Error"
date: 2011-05-18
forum: Multimedia Software
---

### Post by Solumin on 2011-05-18
Hi all,

I'm starting to learn OpenGL using this: [http://openglbook.com/the-book/](http://openglbook.com/the-book/)
It seems to be a pretty nice start. (though it is only up to Chapter 3 right now)
I'm trying out the first example ([http://openglbook.com/the-book/chapter-1-getting-started/#toc-first-steps](http://openglbook.com/the-book/chapter-1-getting-started/#toc-first-steps)) and things are going smoothly.  However, when I actually try to run the example, I get this error:
```
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  128 (GLX)
  Minor opcode of failed request:  34 ()
  Serial number of failed request:  38
  Current serial number in output stream:  39

```Some googling has revealed that this is a known bug with X11.  I've seen a few solutions that involve adding things to xorg.conf.  I've tried the two solutions that seem to have brought success:
```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
[B]    Option "VideoRam" "65536"
    Option "CacheLines" "1980"[/B]
    *Option   "AccelMethod" "EXA"*
EndSection

```The first solution is bolded, the second is in italics.  Neither has actually helped and I am still getting this error.  Does anyone know of any fixes?


This is the result of lspci | grep VGA:
```
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)

```

---

