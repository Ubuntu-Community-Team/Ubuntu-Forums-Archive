---
title: "dark video in vlc, mplayer, totem"
date: 2007-10-31
forum: Multimedia &amp; Video
---

### Post by acorrigan on 2007-10-31
I'm using gutsy.  Any video I play in vlc, mplayer, or totem looks extremely dark.

I tried changing the brightness as described here, but it didn't help:
[http://ubuntuforums.org/showthread.php?t=209986&highlight=mplayer+brightness+totem+915&page=2](http://ubuntuforums.org/showthread.php?t=209986&highlight=mplayer+brightness+totem+915&page=2)  

This appears to be a problem with X or whatever handles video by default since when I changed the Video Output module in VLC to OpenGL all videos play at a normal brightness.

How can this be fixed?

---

### Post by erythro on 2007-11-06
I'm experiencing the same issue. What graphics card do you have? Are you sporting dual monitors with xinerama?

---

### Post by arito on 2007-11-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/152377](https://bugs.launchpad.net/ubuntu/+bug/152377) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Same problem here with Gutsy. My graphics card is Nvidia GeForce 8800 GTS. I found a bug report that looks similar, but I'm not sure if it's the same though.

---

### Post by arito on 2007-11-15
I just tried to adjust the video settings in Totem media player and to my suprise that solved the problem. I'm suprised because the problem was also present in VLC (where I couldn't find a relevant setting). I also had already tried to adjust contrast and brightness in nvidia-settings without success (it may be though that I accidentally tried with "X Server Colour Correction" instead of "X Server XVideo Settings").

There may be something wrong with the default installation in this regard, because I haven't touched any of the video settings in question before this, and this is also the first time I have had this "dark video" problem.

---

### Post by erythro on 2007-11-16
Yep. It was a matter of resetting the color balance in the display preferences under Totem. Made me feel real stupid. But I don't see why these settings changed in the first place. I certainly never touched them. And why should they affect the settings in VLC is beyond me as well. In fact, I just checked them again and the sliders were slightly off balance again! I'm not sure what's going on with this. Maybe the nvidia driver settings control application level stuff? But even then, why would they change on their own? Would be cool if someone could shed some light on this...

---

### Post by sethtriggs on 2008-01-20
I dunno, but it worked for me. Thanks!

-Seth

---

### Post by unwiredbrain on 2008-02-12
Same problem here.:(

Graphic card:
```
nVidia Corporation GeForce 8400 GS
```X.Org extensions:
```
BIG-REQUESTS Composite DAMAGE DOUBLE-BUFFER DPMS Extended-Visual-Information 
GLX MIT-SCREEN-SAVER MIT-SHM MIT-SUNDRY-NONSTANDARD NV-CONTROL NV-GLX RANDR 
RECORD RENDER SECURITY SHAPE SYNC TOG-CUP X-Resource XAccessControlExtension 
XC-APPGROUP XC-MISC XFIXES XFree86-Bigfont XFree86-DGA XFree86-Misc 
XFree86-VidModeExtension XINERAMA XInputExtension XKEYBOARD XTEST XVideo
```OpenGL module:
```
Vendor              NVIDIA Corporation
Renderer            GeForce 8400 GS/PCI/SSE2
Version             2.1.1 NVIDIA 100.14.19
Direct Rendering    Yes
```System:
```
Ubuntu       7.10 "Gutsy Gibbon"
Kernel       2.6.22-14-generic (i686)
C Library    GNU C Library version 2.6.1 (stable)
```

---

### Post by jakethecake on 2008-02-12
I've got it with a 8800GTS on 64bit Gutsy as well. 

If I reset to 'hardware default' under the 'X Server XVideo Correction' tab with nvidia-settings then it changes brightness of the movie I'm watching (at the moment), But it won't last past closing. 

I've got the bug on a just reinstalled box with the 169.09 Nvidia drivers. The Totem sliders where all off, even though I haven't touched them. I've reset them now, we'll see if that takes care of it.


[IMG]http://www.rancholinux.com.ar/wp-content/uploads/2007/05/nvidia-settings.png[/IMG]

---

### Post by Miroku on 2008-02-24
yea same issue here, totem settings just keep changing on their own -- its rather annoying but simple to fix (even if u have to keep fixing it). have a nvidia 8300gs and running gutsy amd64.

---

