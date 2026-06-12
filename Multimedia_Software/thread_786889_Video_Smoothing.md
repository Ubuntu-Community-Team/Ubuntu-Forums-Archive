---
title: "Video Smoothing"
date: 2008-05-08
forum: Multimedia Software
---

### Post by spectrevk on 2008-05-08
I'm not sure how else to describe this...back when my laptop was running XP, regardless of what program I was using, when I went to fullscreen with a video, the edges were, generally speaking, smoothed. In Ubuntu, whether I'm using VLC or the default player, when I go fullscreen, I see jaggies, which is mildly annoying. I'm guessing there's either a library or a video driver that would fix this. I'm using a Compaq Presario V5000 with an ATI Radeon XPress 200M. I'm using the proprietary ATI driver that Ubuntu gets via the "Hardware Drivers" app, but I'm not sure about how to ensure that I'm using the latest version.

---

### Post by airbornemist6 on 2008-05-08
Are you using gstreamer or xine? Generally speaking gstreamer is pretty much crap. Xine tends to run things better but has a more limited number of supported formats. To use Xine, go to add/remove and search for totem and install the xine backend. That should help.

---

### Post by spectrevk on 2008-05-08
What if I'm using VLC? Is there a similar backend?

---

### Post by airbornemist6 on 2008-05-08
Also, try using the medibuntu packages:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

EDIT:
Btw, no there isn't a similar backend for VLC, however, you could also try changing it to run opengl

---

### Post by spectrevk on 2008-05-08
Thanks. Apparently there's something wrong with my OpenGL support in Ubuntu, because when I switch to that for output any file I try to open immediately closes the program without playing.

---

### Post by airbornemist6 on 2008-05-08
I personally don't know anything about that, I've just seen it suggested as a possible solution in the past.

---

### Post by spectrevk on 2008-05-21
Well, it's still not quite working. Also, I've noticed that full-screen video is kind of sluggish in any program, regardless of whether I'm using video overlay or not. Any ideas about what I can do about this? I don't think it's the hardware, because I didn't have this problem under XP.

---

### Post by gnivler on 2008-05-21
It sounds like you are talking about image tearing, it's related to to vertical sync.

---

### Post by spectrevk on 2008-05-21
No, the problem I'm having isn't tearing, it's pixelization, particularly when I go full-screen. The slowdown could be due to vertical sync (good catch, I'll look into that), but the original issue is that the video looks blocky in full screen, instead of having some kind of smoothing applied. Open GL kind of fixes this, but I can't get it to work in VLC (or Totem, for that matter) with my video card driver.

---

### Post by gnivler on 2008-05-22
> **spectrevk said:**
> No, the problem I'm having isn't tearing, it's pixelization, particularly when I go full-screen. The slowdown could be due to vertical sync (good catch, I'll look into that), but the original issue is that the video looks blocky in full screen, instead of having some kind of smoothing applied. Open GL kind of fixes this, but I can't get it to work in VLC (or Totem, for that matter) with my video card driver.

Ahh sorry I misunderstood.  I have seen that issue in windows before but not yet in linux.  I remember changing the type overlay between VMR7 and VMR9 or some non overlay output mode, I don't fully understand and having different quality results, some of which were very pixelized.  The fglrx (proprietary one anyway) driver has two settings in xorg.conf relating to overlay might be worth taking a look and also VLC has settings when in advanced mode to change the video output module, I have the most success with Xvideo but I'm using an nvidia card.

These are the device options from xorg.conf:
Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
[B][I]        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "on"[/I][/B]
EndSection

---

### Post by PTR999 on 2008-05-22
Just registered to reply to this thread.

Have the same problem, video looks alright when not in full screen but when in full screen the video looks "jaggy"/"pixelated". The same fault in all players.
(Looks like the video is zoomed in 1% or something)
But,the video is played smooth without tearing.
 


Once solved this when using my laptop with a external monitor,
when i disabled the laptop screen and only had the external monitor activated the problem went away.(Ubuntu 7.10 ati prop drivers)

But now i do not have any ext. monitor so is using the laptop screen and the problem is back.
Upgraded to 8.04 in hope to get this problem solved but still same, so is now using ubu 8.04 with the prop. ati drivers.

The computer is a Fujitsu Siemens Amilo PA1510(notebook) with an ATI Radeon Xpress 1100. 

/P

---

