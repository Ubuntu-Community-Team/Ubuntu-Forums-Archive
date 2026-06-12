---
title: "Ati X1400 on Intrepid: flickering video and screensavers"
date: 2008-11-02
forum: Multimedia Software
---

### Post by Ultimusbuntu on 2008-11-02
Hello,

I've recently installed Ubuntu Intrepid and with the fresh install I noticed that none of the video players (both Totem and VLC) worked for me, although I had installed some codec packages and later on the restricted extras. Basically, I would try to open a video file or a DVD and the player would close right after without giving me any error message or anything.


I then went to install the hardware drivers for my Ati X1400 (now 8.54.3) and the video finally started showing up, but now it would flicker like crazy. I then read something about changing the [gstreamer properties](http://ubuntuforums.org/showthread.php?p=4872863) and only the X window system (no XV) option would work for me without flickering but it seemed far more resource heavy so I chose not to use it. By this time I also noticed that the problem wasn't just concerning my video viewing but also my screensavers as well, as my computer would go crazy even from previewing anything else than the black screen.


I then read various posts which mostly seemed to have the same advice of adding "Option TexturedVideo "on"" to your xorg.conf's device section (for example: [https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/197639](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/197639)). I tried adding that line but it seems to have only made all the gstream property options flicker. There seems to be some experience on editing the x1400 xorg.conf ([http://ubuntuforums.org/showpost.php?p=5197345&postcount=2](http://ubuntuforums.org/showpost.php?p=5197345&postcount=2)) but I'm a bit hesitant of just editing things aimlessly as I'm still quite the n00b when it comes to Ubuntu.


Thanks

---

### Post by onaka_the_kaka on 2008-11-02
I have the same problem on Ati Mobile x1300 on my Inspiron 6400 laptop! Maybe we should file a bug-report about this...

---

### Post by jdorenbush on 2008-11-03
I have an ATi card and Totem video player. After upgrading to 8.10 I am also experiencing the flickering problem.

---

### Post by tuxsheadache on 2008-11-03
I am suffering from the same problem using my ATI Radeon 2600XT

---

### Post by Wickedone on 2008-11-05
You can add me to the bug, although when I checked there are several already filed that might deal with this.  

The solution I found on [http://www.blog.arun-prabha.com/2008/10/29/ubuntu-810-to-be-released-tomorrow/]("Arun's Blog") fixes it.  That is to go to System / Preferences / Appearance / Visual Effects and select "None".

This fixed it for me, although it is somewhat disheartening that 3D desktop and video/opengl don't work.  This to me seems to be a regression since it worked on 8.04/7.10 on my Toshiba A215 with ATI x1300 with no problems.

But the way I look at it someone will get it fixed and in the mean time I don't really need the eye candy it just is nice.

FGLRX driver
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/179042]("Launchpad Bug 179042")

You should add yourself to the bug report since it seems AMD seems to think this is a feature request instead of a regression.

---

### Post by tuxsheadache on 2008-11-05
I found post #14 useful [http://ubuntuforums.org/showthread.php?t=964912&page=2]("http://ubuntuforums.org/showthread.php?t=964912&page=2") which means I can watch videos on VLC media player with no problems. The rest of the thread could be useful as well =D

---

### Post by Ultimusbuntu on 2008-11-06
> **Wickedone said:**
> The solution I found on [http://www.blog.arun-prabha.com/2008/10/29/ubuntu-810-to-be-released-tomorrow/]("Arun's Blog") fixes it.  That is to go to System / Preferences / Appearance / Visual Effects and select "None".

Yes, this works for me as well. Although I had read about something like this before, I was under the impression that this would't be enabled by default and that it would need a separate install or something but I guess not.

Hope this can be fixed soon.

---

### Post by jdorenbush on 2008-11-17
If you haven't fixed the problem already...

SOLUTION 1
1. Hit Alt+F2
2. Type: gstreamer-properties
3. Click the 'Video' tab
4. Set the output to "X Window System (No Xv)"

SOLUTION 2
Turning off Visual Effects seemed to work.

SOLUTION 3
VLC Player seems to work without any problems.

---

### Post by alexroat on 2008-11-30
> **jdorenbush said:**
> If you haven't fixed the problem already...

SOLUTION 1
1. Hit Alt+F2
2. Type: gstreamer-properties
3. Click the 'Video' tab
4. Set the output to "X Window System (No Xv)"

SOLUTION 2
Turning off Visual Effects seemed to work.

SOLUTION 3
VLC Player seems to work without any problems.

This is not a solution to the problem, it is a workaround.
For example I've the same problem with my Radeon HD 2400 XT on a Dell Inspiron bought in june.
Considering that on an another older (5 years) machine (nvidia fx5500 and AMD64 3200) I can watch videos/screensaver and openGL games without any problem when compiz is enabled, it is quite hard to renounce to use togheter the Visual Effects (compiz) and GL games on the newest one (ATI 2400 XT and intel dual core).
I think it is due to ATI driver and/or settings of xorg.conf.
I hope maintainer will fix this problem as soon even because this problem in Hardy was not present.

All the best.

Alessandro

---

### Post by Daikoni on 2008-12-01
I've got an ATI x1400 too, and the same bug.
and glxgears half times crashes and the whole desktop with it..

For the flickering, i write in console "**metacity --replace**" before play anything, and when i'm done seeing it, i write "**compiz --replace**". This don't solve the problem, but it's just the way i could see any movies =P

I hope someone find a solution soon.. i'm not an expert at this.. =/

---

### Post by tomitzel on 2009-01-17
I have the same problem on Ati x1200

---

### Post by sideaway on 2009-04-10
it seems to be a recurring problem on the ATi x1*00 cards...

I have the same problem on a mobility x1400

---

