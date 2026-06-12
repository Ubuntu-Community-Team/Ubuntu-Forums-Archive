---
title: "No Direct Rendering on Radeon 9500"
date: 2006-07-11
forum: Multimedia &amp; Video
---

### Post by krazykirk on 2006-07-11
Hi everyone,

I was about to try playing a 3d game, but i got this error about there being no direct rendering! So i tried running this thing 
```
kirk@kirk-desktop:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No
```

I followed every step in this guide > [http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910) to get the ATI drivers to work, so I figured that direct rendering or whatever would work. Apparantly not.

Is there any way I could enable direct rendering?

---

### Post by thingy on 2006-07-11
What is the output of this command: "fglrxinfo"

---

### Post by DoubtingThomas on 2006-07-11
I have tried about 6 different ATI How-to's on this board and have yet to get direct rendering to work correctly on my ATI Mobility 9700.

I actually "have" DRI loading now, but (and it is a BIG but), loading the DRI crashes X.  So, for me to do anything, I have to comment out the *load "dri"* section in my xorg.conf.  Which allows X to start but effectively disables rendering, so no 3D for me :( .

As for your issue:

1. Make sure load "dri" is in your modules section in your xorg.conf

2. Check to see if the */usr/lib/dri* directory exists.  If it doesn't you will need to link it in.  I didn't have this issue, but many others did.

3. Verify fglrx is loaded. I think the command you want for this:
*modprobe -l | grep fglrx*

Those are just some of the things off the top of my head that I remember from the gazillion How-to's I have waded through.  Hope this helps.

-scott

---

### Post by krazykirk on 2006-07-13
hmm.. well dri was in my modules section, the /usr/lib/dri directoy existed, and fglrx was indeed loaded...  thanks for the help anyway Scott

the output of fglrxinfo:

```
 kirk@kirk-desktop:/usr/lib/dri$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9500 Pro Generic
OpenGL version string: 2.0.5879 (8.26.18)

```

---

### Post by krazykirk on 2006-07-13
whoa i just noticed the XFree86-DRI missing... but I don't know what this means... does anyone know?

---

### Post by krazykirk on 2006-07-15
Bump~

---

### Post by krazykirk on 2006-07-17
Bump..

anyone?

---

### Post by whatever on 2006-07-17
you are not using Xgl, are you?

---

### Post by krazykirk on 2006-07-22
Yes I am using XGL, and i found out that xgl makes that grep command lie, but i tried to play a game (called stepmania) and it said that direct rendering was turned off there.

Anyone know a solution?

---

### Post by whatever on 2006-07-22
direct rendering is not possible with xgl, only accelerated indirect rendering.

---

