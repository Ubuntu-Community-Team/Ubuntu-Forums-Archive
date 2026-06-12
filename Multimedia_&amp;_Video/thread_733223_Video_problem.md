---
title: "Video problem"
date: 2008-03-23
forum: Multimedia &amp; Video
---

### Post by icarus punk on 2008-03-23
First off i am very new new to this, iv'e just left windows so don't have any real knowledge with terminal, everything has installed fine (Kubuntu V.3.5.8. )

my problem is that every time i try to play a video (.avi) it opens the video in a window then compresses the video into the bottom half of this window and plays very jerkily and with a lot of noise. screendump attached.

so far i have tried using VLC, Mplayer, which is slightly better and kaffeine which just crashes outright.

i have an ATI graphics card and have heard horror stories of these not working properly, i cant remember what card it is and can't figure out how to check in kubuntu.

any ideas on how to fix this?

---

### Post by icarus punk on 2008-03-23
i posted this already in multimedia, then saw this and thought it was more suitable (sorry mods)

First off i am very new new to this, iv'e just left windows so don't have any real knowledge with terminal, everything has installed fine (Kubuntu V.3.5.8. )

my problem is that every time i try to play a video (.avi) it opens the video in a window then compresses the video into the bottom half of this window and plays very jerkily and with a lot of noise.al though in the picture it looks clear it is unwatchable. screendump attached.

so far i have tried using VLC, Mplayer, which is slightly better and kaffeine which just crashes outright.

i have an ATI graphics card and have heard horror stories of these not working properly, i cant remember what card it is and can't figure out how to check in kubuntu.

any ideas on how to fix this?


edit: web videos work fine so im guessing not a graphics card issue, i'm even more confused now

---

### Post by xc3RnbFO8P on 2008-03-23
Try first: open VLC> settings> preferences> video> output module> check advanced options
in  video output module choose **x11**
See if it works.

---

### Post by herbster on 2008-03-23
Which card exactly do you have, and which driver are you using? Go to System > Admin > Restricted drivers and post back what is there.

---

### Post by icarus punk on 2008-03-23
i dont get the option of output module after video in options, even with advanced options, couldn't find anything about x11 in there either. im running VLC version  0.8.6c if that helps.

---

### Post by icarus punk on 2008-03-23
it just says ATI accelerated graphics driver in there?

---

### Post by ubuntu-freak on 2008-03-23
How long ago did you install Ubuntu? It's best to avoid x11 if possible, so try this first and follow the prompts;
 
**sudo dpkg-reconfigure -phigh xserver-xorg** 

If you still don't get any joy, you could try the [ATI sticky thread](http://ubuntuforums.org/showthread.php?t=515573), or even do a fresh install of Hardy. 
 
Nathan

---

### Post by herbster on 2008-03-23
Okay, and your screen resolution and all works great? Just checking that it's not a bad driver issue.

How many different video files have you attempted to play?

---

### Post by icarus punk on 2008-03-23
yeah screen res is fine, youtube videos work fine, ive only tried running .avi as thats how all the videos i have are formatted. is there a set of .avi codecs i need from adept like the ones i needed for mp3 playback?

---

### Post by herbster on 2008-03-23
[https://help.ubuntu.com/7.10/musicvideophotos/C/codecs.html](https://help.ubuntu.com/7.10/musicvideophotos/C/codecs.html)

---

### Post by icarus punk on 2008-03-23
maybe a couple of months ago, i havn't used it for video until now though, i just checked youtube and videos work fine on there, so i guess its not a graphics card issue?

---

### Post by icarus punk on 2008-03-23
i already have all the GStreamer codecs installed.

---

### Post by ubuntu-freak on 2008-03-23
> **icarus punk said:**
> maybe a couple of months ago, i havn't used it for video until now though, i just checked youtube and videos work fine on there, so i guess its not a graphics card issue?

 
Flash is different. Try the suggestions I mentioned.
 
Nathan

---

### Post by icarus punk on 2008-03-23
ok, im trying **sudo dpkg-reconfigure -phigh xserver-xorg** how do i select which resolutuon to use, ie what do i have to do to remove the ones i don't want?

---

### Post by ubuntu-freak on 2008-03-23
> **icarus punk said:**
> ok, im trying **sudo dpkg-reconfigure -phigh xserver-xorg** how do i select which resolutuon to use, ie what do i have to do to remove the ones i don't want?

 
Doesn't it ask to confirm your resolution?

---

### Post by Ub1476 on 2008-03-23
Press <Space> to select/unselect.

---

