---
title: "Blender + EeePC 1000H + Jaunty = Strange Artifacts"
date: 2009-07-27
forum: Multimedia Software
---

### Post by bogdan_5844 on 2009-07-27
Desktop version of Ubuntu 9.04 and EeePC 1000H.
Using the Eee kernel found on array.org
EXA acceleration enabled (before following the guide here on ubuntuforums,blender behaved exactly the same)

Screenshot shows what I see in Blender.(I want to run it for some small projects,and my bigger lappy is not available :( )


Compiz is off,running in windowed or fullscreen mode makes no difference.

Advices,anyone?I don't have another PC at my disposal to work in Blender

Thanks in advance :)

---

### Post by igorzwx on 2009-07-27
have tried Ubuntu Lite (U-Lite)?

---

### Post by igorzwx on 2009-07-27
**[*U*-*lite* Linux | Where Speed Meets Ease]("http://u-lite.org/")**

A light-weight distribution, based on Ubuntu, designed to run comfortably on old and low-resource computers. It comes with LXDE, Kazehakase web browser, **...**
**u**-**lite**.org/ - [Cached]("http://209.85.129.132/search?q=cache:lmzKj6L4vJUJ:u-lite.org/+u+lite&cd=1&hl=en&ct=clnk") - [Similar]("http://www.google.com/search?hl=en&q=related:u-lite.org/")
[Get U-lite]("http://www.google.com/url?q=http://u-lite.org/content/get-u-lite&ei=GktuSr_uCoWlsAapytz5Bg&sa=X&oi=smap&resnum=1&ct=result&cd=1&usg=AFQjCNF3hgjpLM5yXYZ6lO2hRVFCirJPKQ")
[Requirements]("http://www.google.com/url?q=http://u-lite.org/content/requirements&ei=GktuSr_uCoWlsAapytz5Bg&sa=X&oi=smap&resnum=1&ct=result&cd=2&usg=AFQjCNHUliCGbpeHqwN_EZlFRWeMgFMWyQ")
[U-lite 0.9 Planned Features (dev)]("http://www.google.com/url?q=http://u-lite.org/content/u-lite-09-planned-features-dev&ei=GktuSr_uCoWlsAapytz5Bg&sa=X&oi=smap&resnum=1&ct=result&cd=3&usg=AFQjCNE-PPPM6BWZue1JYz8mlVkW5OerXw")
[Forums]("http://www.google.com/url?q=http://u-lite.org/forum&ei=GktuSr_uCoWlsAapytz5Bg&sa=X&oi=smap&resnum=1&ct=result&cd=4&usg=AFQjCNFTFGLTS82Z9mAsb8EtaHuRadrPLw")
[U-lite Screenshots]("http://www.google.com/url?q=http://u-lite.org/content/u-lite-screenshots&ei=GktuSr_uCoWlsAapytz5Bg&sa=X&oi=smap&resnum=1&ct=result&cd=5&usg=AFQjCNEcIUjeWfBgyomi9T21ojeBf_Aqww")
[About Us]("http://www.google.com/url?q=http://u-lite.org/content/about-us&ei=GktuSr_uCoWlsAapytz5Bg&sa=X&oi=smap&resnum=1&ct=result&cd=6&usg=AFQjCNGMcGKO2Rm99vd_1b3SL-GDoZA0ng")
[More results from u-lite.org »]("http://www.google.com/search?hl=en&q=+site:u-lite.org+u+lite&ei=GktuSr_uCoWlsAapytz5Bg&sa=X&oi=smap&resnum=1&ct=more-results")

---

### Post by bogdan_5844 on 2009-07-28
Sorry,but I do not really want to try another distro...
I worked a lot to tweak this installation in order to work correctly,I don't really want to dump all that:)

---

### Post by igorzwx on 2009-07-28
It is actually the same distro, the same repositories

---

### Post by demosthene1 on 2009-07-28
Blender fix for jaunty.
Command line to start blender:
sh -c "LIBGL_ALWAYS_SOFTWARE=1 blender-bin"

Works for me.

---

### Post by bogdan_5844 on 2009-07-28
Thanks!That did it!

---

### Post by Labello on 2009-07-29
> **demosthene1 said:**
> blender fix for jaunty.
Command line to start blender:
Sh -c "libgl_always_software=1 blender-bin"

works for me.

you are the maaaaaaan!

This is awesome! Thank you soooo much!!!

---

### Post by igorzwx on 2009-07-29
Why not mark this as "solved" and 
put all these Blenders together?

---

### Post by Hacker John on 2009-10-28
> **demosthene1 said:**
> Blender fix for jaunty.
Command line to start blender:
sh -c "LIBGL_ALWAYS_SOFTWARE=1 blender-bin"

Works for me.


This also works for me.  I was having the same problem with K-3D as with Blender so I tried the same command string, substituting "k3d" for "blender-bin" and it worked beautifully.

I've put the commands in the menu launchers and I'm happy as larry.

---

### Post by Hacker John on 2009-11-03
I've had the same problem with nviz in GRASS GIS.  I got around it by using sh -c "LIBGL_ALWAYS_SOFTWARE=1 nviz" from the GRASS prompt in the terminal but it is annoying not to be able to launch it from the GRASS main window.

Is there a way of making OpenGL-dependent apps work without having to do this?

---

### Post by chaos51 on 2009-11-10
@igorzwx - It's not solved because the real issue is a bad Intel video driver, using sh -c "LIBGL_ALWAYS_SOFTWARE=1 appname" is a workaround which turns off hardware acceleration for openGL and uses software rendering instead.  This makes the openGL app very slow to work in.  I've seen this many times on various hardware and it usually gets fixed with an update to a driver (or gl library, I think the last time I had this problem it was with mesaGL or libmesa or something similar) or sometimes a setting in xorg.conf I'm having similar issues with my eeePC 1000HE and while blender runs with the above I know it can be much faster with hardware rendering.

---

