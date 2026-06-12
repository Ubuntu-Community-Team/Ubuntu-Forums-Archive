---
title: "Annoying things while playing video back"
date: 2009-12-19
forum: Multimedia Software
---

### Post by sonicb00m on 2009-12-19
There's a couple of things in Ubuntu Gnome that really bug me when watching full screen video.

1. The mouse cursor keeps popping up every 30 or seconds or so. I keep having to remember to put it in the top corner so it doesn't disturb me.

2. Monitor powerdown isn't being turned off while watching full screen back either. I have to keep turning off the powerdown to watch a film and then remember to put it back.

I've also noticed that video playback is a bit weird with Compiz enabled. Are there some optimisations for this so I don't having to keep enabling/disabling compiz to watch 720p video? Since Vista/W7 have good video playback while the 3d desktop is enabled I wondered if Ubuntu has any works around for this?

---

### Post by sonicb00m on 2009-12-20
Ok, I tried install unclutter (which hides the mouse pointer just fine) but it doesn't work under video playback. It seems that whatever is going on with the video playback it triggers the mouse pointer to popup every 10 seconds or so.

This works with all the players i try.....smplayer and totem

---

### Post by sonicb00m on 2009-12-22
does anyone get this issue or is it just me? it's driving me nuts.

---

### Post by rvm4000 on 2009-12-22
[A mouse pointer keeps reappearing during video playback in smplayer](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/455073)

---

### Post by Stason on 2010-02-24
Menu (or right click) ==> Video ==> Stay on top ==> While playing


This would hide the pointer, which pops up when the "disable screensaver" script moves the mouse every now and then.

---

### Post by sonicb00m on 2010-02-25
thanks for the tip.

there's a patch for mplayer which solves this bug. unfortunately, some update put it back again so i need to recompile it. will try that tip of yours though!

---

