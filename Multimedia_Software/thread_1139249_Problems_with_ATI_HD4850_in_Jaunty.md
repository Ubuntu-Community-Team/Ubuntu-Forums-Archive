---
title: "Problems with ATI HD4850 in Jaunty"
date: 2009-04-26
forum: Multimedia Software
---

### Post by kewlito on 2009-04-26
First of all, everything was working good with intrepid. Today I upgraded to jaunty and this two problems appeared.
First, whenever I restart, I need to set compiz on manually in the last tab of "Appearance". I choose some level of effects, it says that it's looking for drivers, and then compiz works.

The second (and more important) problem, is that whenever a put a video in fullscreen in VLC, there's a delay of about 5 seconds, showing just a black screen. And then the video appears but looking awkward until the next keyframe.

I'm using the fglrx drivers, those were installed automatically. Is there anything I can do to be in a better situation? 
I'll be thankful for any kind of help.

---

### Post by logan85 on 2009-06-04
Hi, i had the same problem, and i disabled compiz, after that vlc worked fine. does somebody know if the new ati hardware fixes this bug?

---

### Post by kewlito on 2009-06-04
I've tried many things, like installing the 9.5 drivers, but the problem is still active.

---

### Post by logan85 on 2009-06-20
I've installed the 9.6 drivers, but it's the same... 
had somebody find a solution? anticipated  thanks for suggestions.

---

### Post by chrisj26 on 2009-06-20
I made the same mistake. Upgrading caused so many problems with my graphics card that the only way I could get a fully functional pc was to do a fresh install. in any case i'll try and help you. what's the problem with your current drivers? do they not work at all? for any graphics queries first [this]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide") is the best guide you can find. secondly i'd try using all the different video modes on VLC. I've found that depending on what you're playing (DVD, Xvids, H.264) XVideo and X11 tend to be the most stable with ATI cards. I currently use X11 for Xvid and H.264 and Xvideo for DVDs these. Using anything other than them causes the same problems you refer to. Failing that, I'd go for a fresh install.

---

### Post by waspbr on 2009-06-21
I have a HD3300 IGP, I have just tried the new 9.6 drivers and that did not go very well, the playback performance was awful and desktop effects would not be enabled. The strange thing is that some 3d applications did work. But they are not essential. 

Until they get their act together in ATI I am gonna have to stick to the opensource drivers, video playback works beautifully well with them. And I can always use the metacity compositor to make my desktop look fancy with gnome do, shadows and all that.

---

### Post by markbuntu on 2009-06-21
> **waspbr said:**
> I have a HD3300 IGP, I have just tried the new 9.6 drivers and that did not go very well, the playback performance was awful and desktop effects would not be enabled. The strange thing is that some 3d applications did work. But they are not essential. 

Until they get their act together in ATI I am gonna have to stick to the opensource drivers, video playback works beautifully well with them. And I can always use the metacity compositor to make my desktop look fancy with gnome do, shadows and all that.

Generally, if you cannot enable desktop effects then the driver kernel modules are not installed. This is a common issue when the old kernel modules are not removed before installing the new driver. The uninstall script in the last few drivers do not seem to remove the old driver kernel modules so they must be removed by hand and the new ones installed likewise.

 Some 3D apps will still seem to work with indirect rendering.

---

### Post by chrisj26 on 2009-06-21
Did you get them off AMD's site? I've found (on my computer & several other PCs) that once you get AMD's latest drivers you generally have a more stable system (i.e. with effects enabled, certain features of certain programs will need the most up to date drivers available). your problem sounds like something hasn't been enabled or disabled properly. And also you have to experiment with different driver versions according to the card and the one that's most compatible with all the apps you use.

---

