---
title: "[SOLVED] v-sync problem with video"
date: 2008-11-06
forum: Multimedia Software
---

### Post by Linux user 66 on 2008-11-06
During video playback I experience horizontal tearing (similar to what happens when you don't have v-sync enabled in the video options in games), meaning that the video image often splits a little bit when there is movement. On my secondary hard drive with Vista there's no such issue.

What can I do to fix this?

I'm running Ubuntu 8.10 64-bit with an NVIDIA GeForce 8800GTX VGA card (177.80 driver). I experienced the same problem on 8.04.1 with the previous driver.

---

### Post by Open-SuSe-A-Me on 2008-11-06
i had experienced the same problem on my desktop with hardy and a newer Nvidia card, fixed it by messing with the compiz settings (enabled sync to v-blank) and did the same within nvidia-settings app. no more video tearing and cube tearing.

now on Intrepid on my laptop with a generic intel 965 graphics card i get horrible tearing on videos out of the box which i cannot find a fix for besides going into gstreamer-properties and using "Video Overlay" in the video settings which only fixes Totem but as a side effect my whole desktop flickers randomly.

ive also found out that /etc/X11/xorg.conf has been redone and all i see now is "configured video device" so i cant really troubleshoot that.

---

### Post by Linux user 66 on 2008-11-09
> **Open-SuSe-A-Me said:**
> i had experienced the same problem on my desktop with hardy and a newer Nvidia card, fixed it by messing with the compiz settings (enabled sync to v-blank) and did the same within nvidia-settings app. no more video tearing and cube tearing.

now on Intrepid on my laptop with a generic intel 965 graphics card i get horrible tearing on videos out of the box which i cannot find a fix for besides going into gstreamer-properties and using "Video Overlay" in the video settings which only fixes Totem but as a side effect my whole desktop flickers randomly.

ive also found out that /etc/X11/xorg.conf has been redone and all i see now is "configured video device" so i cant really troubleshoot that.

Thanks for your suggestion! However, I've enabled *Sync to VBlank* in the NVIDIA settings application in both *XVideo Settings* and *OpenGL Settings*, but the problem persists. I've been testing with a DVD video in VLC media player, MPlayer and Totem Movie Player. I can't find any settings in those players that help either.

I've installed the *CompizConfig Settings Manager*, but there's no *Sync to VBlank* option there. Do you have any other suggestions?

---

### Post by dexter on 2008-11-10
Check under CCSM -> General -> Display Settings Tab, enable "Sync To VBlank". For me this solves choppiness of cube rotations, fast window movements etc, but video playback is still not as smooth as i would like it.

---

### Post by psyke83 on 2008-11-10
> **Linux user 66 said:**
> During video playback I experience horizontal tearing (similar to what happens when you don't have v-sync enabled in the video options in games), meaning that the video image often splits a little bit when there is movement. On my secondary hard drive with Vista there's no such issue.

What can I do to fix this?

I'm running Ubuntu 8.10 64-bit with an NVIDIA GeForce 8800GTX VGA card (177.80 driver). I experienced the same problem on 8.04.1 with the previous driver.

While the posters are giving valuable information (i.e., do enable vsync in compiz), a little while ago I was researching the same problem. One of the NVIDIA Linux developers replied to a post on the [nvnews.net]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14") forum that the latest Xorg and NVIDIA driver don't communicate the V-Sync signal properly for video, causing visible tears (and sometimes diagonal artifacts). 

You should do a search on those forums for more information, as I lost the original link.

---

### Post by Linux user 66 on 2008-11-11
> **dexter said:**
> Check under CCSM -> General -> Display Settings Tab, enable "Sync To VBlank". For me this solves choppiness of cube rotations, fast window movements etc, but video playback is still not as smooth as i would like it.

> **psyke83 said:**
> While the posters are giving valuable information (i.e., do enable vsync in compiz), a little while ago I was researching the same problem. One of the NVIDIA Linux developers replied to a post on the [nvnews.net]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14") forum that the latest Xorg and NVIDIA driver don't communicate the V-Sync signal properly for video, causing visible tears (and sometimes diagonal artifacts). 

You should do a search on those forums for more information, as I lost the original link.

@ dexter:

Thanks a lot! With that setting enabled it's fixed!

@ psyke83:

I appreciate the info!

---

### Post by fyo on 2008-11-11
THANK YOU!

I do find it astounding, though, that this wasn't caught earlier and that it took a non-standard (non-Ubuntu-supported, "universe" repo in this case) application to fix.

Don't get me wrong, I love Ubuntu and have used it exclusively for the past year and a half or so (and other Linux flavors before that), but testing before final release isn't one of its strong points.

---

### Post by Greenwidth on 2009-05-08
> **dexter said:**
> Check under CCSM -> General -> Display Settings Tab, enable "Sync To VBlank". For me this solves choppiness of cube rotations, fast window movements etc, but video playback is still not as smooth as i would like it.

Thanks! Fixed it for me too.

---

### Post by sorryd on 2009-05-21
Not sure if its the same thing, but I had horrible video tearing until I used CCSM to disable video playback in the Utilities section.
I think I have fixed it but I am not 100% sure.
This is the one thing that is really annoying me about Ubuntu. The video playback performance has been pretty miserable on what should be a decent system (Pentium D 820, 2GB RAM, GF8600GT) as I am experiencing tearing and even occasional dropped frames.
Anyway... it seems to be better now, so I will stop ranting.

---

### Post by FSHero on 2009-06-11
Hello all you lucky NVIDIA-graphics-owning people!

I have a Dell Inspiron 1525 laptop with Intel onboard graphics, revealed by "sudo lspci -vv" as:
```

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
        Subsystem: Dell Device 022f

```

I run Kubuntu 9.04 Jaunty Jackalope amd64.

Now, I am having similar problems to those mentioned earlier: during video playback (in all programs: VLC, Kaffeine, Dragon player) I experience horizontal tearing. I can connect the laptop to my HDTV, but the video playback experiences tearing, which in fast scenes is quite irritating. I suspect that horizontal tearing occurs at all times (e.g. KDE desktop effects) but I only notice it during video playback.

In Windows 7 RC (and Windows Vista, I assume), playing these videos doesn't result in horizontal tearing. It seems that NVIDIA users have a VSync option in their graphics control panel program. I was wondering if there is something similar for Intel graphics?

I'm at my wits' end here, because I have done some searching in the Ubuntu forums for such an option, but the advice only applies to NVIDIA or ATI graphics cards.

Could someone please point me in the right direction? e.g. xorg.conf settings, intel graphics driver switches, etc.

---

