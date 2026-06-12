---
title: "Karmic and VBlank on nvidia"
date: 2009-12-05
forum: Multimedia Software
---

### Post by rossmoore on 2009-12-05
Hi,

I've recently made a new server / HTPC. It runs a Zotac IONITX motherboard (N330 Atom with 9400 nvidia GPU).

I've tried  both the 185 Karmic drivers and the latest and greatest 190 drivers, but I can't get rid of video tearing for the life of me - and that applies to dragged windows, dekstop cubes etc.

I have sync to vblank set in nvidia-setting, compiz (and I've tried disabling that too) and in the vlc/xbmc. Nothing doing.

Am I missing something, or is there a bug? I have seen one other posting something on the interwebs about a similar issue - am I alone? Is this issue broader than just Karmic + Ion?

Hope someone has some ideas,
Thanks,
Ross

---

### Post by siabost on 2009-12-07
I'm afraid I have the same problem on an AMD Athlon 7750 Dual-core/nVidia set-up on Karmic.
I've also tried the vblank synch settings to no avail.

But, after further exploration, it does seem to be a Compiz thing. Changing Window Manager from Compiz to Metacity via the Compiz Fusion Icon cures the tearing for me on videos at least.

Hope the bug gets sorted as it's a pest having to switch.

---

### Post by onemanclapping on 2009-12-07
check out my thread: [http://ubuntuforums.org/showthread.php?t=1309077](http://ubuntuforums.org/showthread.php?t=1309077)

same problem :S

the only way to keep vsync is to shut down all visual effects by compiz... how can this bug be still on? I'd really love to know...

---

### Post by nerdy_kid on 2009-12-08
no, check out my thread :D

[http://ubuntuforums.org/showthread.php?t=1348168](http://ubuntuforums.org/showthread.php?t=1348168)

you can keep compiz running (after doing what the thread says), but you have to check Unredirect Fullscreen Windows under the General tab in the General section of ccsm.  Then all your fullscreen videos will sync, turn off compiz to make eveything sync.

---

### Post by rossmoore on 2009-12-14
Thanks nerdy_kid, onemanclapping. I haven't managed to make videos sync, with or without compiz, if the composite extension is enabled in my xorg.conf.

I would love compositing and compiz to be enabled but the primary purpose of my machine is to serve videos to my TV, music to my amp, and files to other machines over wifi. Therefore I've given up on it for now and have switched compositing off so that the videos look good.

Thanks all, fingers crossed this will get fixed in lucid, I guess.

---

