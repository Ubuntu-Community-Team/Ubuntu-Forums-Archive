---
title: "Compare out Glxgears fps score :)"
date: 2006-01-10
forum: Multimedia &amp; Video
---

### Post by Dark Damo on 2006-01-10
I got these with only the ubuntu forums webpage in the background on a Powercollor Radeon 9800pro

27136 frames in 5.0 seconds = 5427.187 FPS
27147 frames in 5.0 seconds = 5429.227 FPS
27149 frames in 5.0 seconds = 5429.714 FPS
27145 frames in 5.0 seconds = 5428.909 FPS
27144 frames in 5.0 seconds = 5428.723 FPS
27147 frames in 5.0 seconds = 5429.312 FPS

---

### Post by IronWolve on 2006-01-11
75732 frames in 5.0 seconds = 15146.297 FPS
74720 frames in 5.0 seconds = 14943.880 FPS
65945 frames in 5.0 seconds = 13187.678 FPS
74828 frames in 5.0 seconds = 14965.534 FPS
76028 frames in 5.0 seconds = 15205.527 FPS

Pentium D 820 with Geforce 7800 GT.

---

### Post by Damburger on 2006-01-11
With a Geforce 6800...

37701 frames in 5.0 seconds = 7540.129 FPS
31141 frames in 5.0 seconds = 6228.108 FPS
32622 frames in 5.0 seconds = 6524.315 FPS
37705 frames in 5.0 seconds = 7540.947 FPS
30582 frames in 5.0 seconds = 6116.363 FPS

Seems a little low :(

---

### Post by IronWolve on 2006-01-11
What cpus are those scores?

---

### Post by Dark Damo on 2006-01-11
Mine is a Celeron 320 2.4ghz socket 478... Shitty yes i know.

---

### Post by mmcmonster on 2006-01-11
How do I find out my score?

---

### Post by TheForumTroll on 2006-01-11
Look at the sticky in this forum ;)

---

### Post by mmcmonster on 2006-01-11
An AMD Athlon XP 3200+ with a NVidia GeForce 6200 video card.

6617 frames in 5.0 seconds = 1323.274 FPS
6637 frames in 5.0 seconds = 1327.266 FPS
6637 frames in 5.0 seconds = 1327.378 FPS
6639 frames in 5.0 seconds = 1327.605 FPS
6797 frames in 5.0 seconds = 1359.266 FPS
6640 frames in 5.0 seconds = 1327.927 FPS

I expected better. :-(.  Maybe I need to do some tweaking?

---

### Post by IronWolve on 2006-01-11
Make sure you are using the nvidia driver from nvidia not the stock one for xorg. You will have to download and compile it.

---

### Post by TheForumTroll on 2006-01-11
I get ~600 fps with a geforce 2 and a AMD64 3500+ :eek: 

Isn't that a bit low? I started a [thread]("http://ubuntuforums.org/showthread.php?t=116016") to find out how to test if 3d acceleration works but no luck so far.

---

### Post by 23meg on 2006-01-11
Let me be the voluntary jackass and say it: glxgears scores aren't a good indication of the overall 3D performance of your device. And we have at least one more huge thread of the same kind, which you can find by doing a search.

---

### Post by az on 2006-01-11
2227 frames in 5.0 seconds = 445.312 FPS


Ati Rage128 (pci) with 16 Megs of ram - Pentium III 600Mhz/512 cache


W00t!

---

### Post by mmcmonster on 2006-01-12
[QUOTE=mmcmonster]An AMD Athlon XP 3200+ with a NVidia GeForce 6200 video card.

6617 frames in 5.0 seconds = 1323.274 FPS
6637 frames in 5.0 seconds = 1327.266 FPS
6637 frames in 5.0 seconds = 1327.378 FPS
6639 frames in 5.0 seconds = 1327.605 FPS
6797 frames in 5.0 seconds = 1359.266 FPS
6640 frames in 5.0 seconds = 1327.927 FPS

I expected better. :-(.  Maybe I need to do some tweaking?[/QUOTE]

The above was using the stock 7667 NVidia drivers.  I just updated the NVidia drivers to 8178, and got the following.  Nothing else has changed.  Same windows were open (one terminal, one firefox), and I haven't messed with anything like compositing yet.:

6637 frames in 5.0 seconds = 1327.342 FPS
6676 frames in 5.0 seconds = 1335.091 FPS
6677 frames in 5.0 seconds = 1335.212 FPS
6676 frames in 5.0 seconds = 1335.131 FPS
6677 frames in 5.0 seconds = 1335.312 FPS
6676 frames in 5.0 seconds = 1335.084 FPS


I was kind of hoping for more than an 8 fps rise. ;-)  Anyway, I hope the driver is at least more stable for compositing. :-)

---

### Post by john131971 on 2006-01-12
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  30
  Current serial number in output stream:  30

???

ATI (:

---

### Post by TheForumTroll on 2006-01-12
I found the problem. Just correct this:
[QUOTE=john131971]
ATI (:[/QUOTE] :p

---

### Post by az on 2006-01-12
[QUOTE=TheForumTroll]I found the problem. Just correct this:
 :p[/QUOTE]

Glad to hear it!

Your scores cannot be lower than mine - Post 'em!

---

### Post by pelle.k on 2006-01-14
[QUOTE=Damburger]With a Geforce 6800...

37701 frames in 5.0 seconds = 7540.129 FPS
31141 frames in 5.0 seconds = 6228.108 FPS
32622 frames in 5.0 seconds = 6524.315 FPS
37705 frames in 5.0 seconds = 7540.947 FPS
30582 frames in 5.0 seconds = 6116.363 FPS

Seems a little low :([/QUOTE]

Well... that depends.
I got around 2600 FPS with a 686 kernel, using a Pentium M 1,8 Ghz + GF 6800 with latest driver from nvidia. :(
Seems a little low considering BF2 runs nice as ever in my native 1440*900 res.
But again, glxgears is not a benchmark, but anyway.

---

### Post by handy on 2006-01-15
So, because glxgears is NOT a true indication of 3D performance...

We need a true 3D benchmark.

If everyone had UT2k4 we could organise something.  But everyone doesn't.

Is there a free OpenGL 3D demo out there that can display average fps, or can be timed acurately?

Or do we need something that tests all of the different capabilities of the GPUs?

Beyond me...

---

### Post by handy on 2006-01-15
Look what I found!

Some one has started a ***_real_* benchmark** Wiki.

[http://nooms.de/benchwiki/](http://nooms.de/benchwiki/)

& this was there too for Unreal:

[http://www.unrealmark.net/](http://www.unrealmark.net/)

Has to be good...:D

---

