---
title: "Weird screen flicker when starting and starting videos"
date: 2008-11-01
forum: Multimedia Software
---

### Post by xhero0 on 2008-11-01
Greetings,

I UPGRADED from8.04 to 8.10 yesterday, now when I start up the laptop I get a weird screen flicker on the bottom like a few bars about 1/4" wide and no more that 1/2 way up the screen vertically.and when I play a video with totem it looks it flashes when i thinks it's gonna play the video but then finally settles where it gonna play...

What I have done:
I disables all compviz effects, no help 
I am out of ideas...
Here is the video part of a lspci
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

```


Thank you ahead of time!

Joe M.

---

### Post by viken.boyadjian on 2008-11-03
Same problem, same card, same release
No ideas

---

### Post by daspooky on 2008-11-14
Same everything...

---

### Post by stoopidnewb on 2008-11-14
Same problem.  Same release.  I get flickering only when watching video files.  Other than that no problems.  The strange thing is that when I first installed Hardy Heron I couldn't get the ATI video card drivers to work at all with my card (X1950 Pro AGP) even after using envy, a couple command line methods I found, as well as installing the "3rd party" video software thing that popped up.  I always got a black screen after restarting.  After upgrading to Intrepid Ibex, I can now run full effects and the latest ati software works flawlessly except for the flicker.  I am glad I am not the only one with this problem.  

What video drivers is everyone with this problem using?  Are we all in the ATI crappy video driver club or is this just an Intrepid Ibex bug that needs to be fixed?

I tried both Mplayer and gstreamer and it does the same with both

Also does the same regardless of screen resolution or effects quality setting.

---

### Post by daspooky on 2008-11-16
I'm using xserver-xorg-video-intel

---

### Post by macghsot on 2008-11-16
I'm having the same problem, but when I play a video in firefox it plays great without any flicker. I"m still searching the net for an answer.:confused:

---

### Post by MonGol on 2008-11-16
do you have the desktop effects enabled? if you have then change the video output to X11 (that workes with vlc and enabled desktop effects).

you can change the video output in vlc as follows:
VLC->Extras->Settings (or Preferences)->Video (left hand-side)->(Video) Output -> change to X11 (if this doesn't work test other video outputs ;-))

greez,
marcel

---

### Post by macghsot on 2008-11-16
thanks alot MonGol that really worked.:)

---

### Post by xhero0 on 2008-11-17
> **MonGol said:**
> do you have the desktop effects enabled? if you have then change the video output to X11 (that workes with vlc and enabled desktop effects).


greez,
marcel

How do you change the video output to x11 in desktop effects?

joe m.

---

### Post by lokutus25 on 2008-12-17
I have the same problem. But If I change the video output to X11 in VLC I'm loosing in video quality anyway. In mplayer if I set the video output to X11 I cant go full screen...Not what I expected from such video card. Or Intrepid. I'm using the Ubuntu fglrx drivers. Any suggestion?
Thx

---

### Post by lokutus25 on 2008-12-18
Ok...it was Compiz giving the flicker problem. Diabling the Visual Effects have my video play fine. Now I just need a good Compiz Switch... :-P 
Thanx Guys ;)

---

### Post by f1nn on 2008-12-20
> **MonGol said:**
> do you have the desktop effects enabled? if you have then change the video output to X11 (that workes with vlc and enabled desktop effects).

you can change the video output in vlc as follows:
VLC->Extras->Settings (or Preferences)->Video (left hand-side)->(Video) Output -> change to X11 (if this doesn't work test other video outputs ;-))

greez,
marcel


good on you mate!
[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

