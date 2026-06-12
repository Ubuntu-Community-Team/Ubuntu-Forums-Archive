---
title: "[SOLVED] Ubuntu way to configure alternate Nvidia driver?"
date: 2008-11-03
forum: Multimedia Software
---

### Post by dawynn on 2008-11-03
OK -- we have the 96.43.09 drivers available for Intrepid (at least in the proposed directory).  I have upgraded all of the modaliases, and installed only the nvidia-glx-96 driver.  But what's the ubuntu way to make it usable?

When I start jockey-gtk, it indicates that I can activate the 173 driver, but does not mention any of the other drivers.

Problem is, 173 may work with my card, but it uses SSE instructions, and I have an Athlon Classic CPU.  The Athlon Classic did not support SSE.  So, I need the 96 drivers, but Jockey is so "intelligent" that it won't even allow me to install the 96 drivers, because my video card is supported by the newer drivers.

So, what's the current Ubuntu way to install the legacy drivers, when the video card can support later drivers, but the CPU can't?

Update: Saw a note in another thread about legacy drivers being blacklisted in Jockey, how can I check whether that's the case on my PC?  (if needed, please provide additional instructions on how to un-blacklist)

---

### Post by dawynn on 2008-11-05
Yay!  Jockey has been updated in Proposed.  So, I was able to get the 96.43.09 drivers working.

Normal video works.  OpenGL works.  Just one thing broken now.

How do I force my computer to remember my video settings?  I'm a traditional computer user: I shut my PC down when I'm not using it.  Every time I boot up, the system feels that it knows better than I do what resolution I want.  So, it keeps switching me back from 1024x768 to 800x600.

There are two places that I have found that allow me to set the resolution (I use Ubuntu, by the way).  One is the nvidia settings tool.  That one always lets me change the setting, and provide proper choices.  (1024x768, 60hz)

The other is under System Preferences -- Screen Resolution (or something like that).  If I go here first, the best that it will allow is 800x600.  If I fiddle with nvidia first, this will allow 1024x768, but only at 87hz.

But each time, when I reboot, I'm back to 800x600.  Any suggestions?

---

### Post by sisco311 on 2008-11-05
try to run nvidia-settings as root:
```
gksu nvidia-settings
```

select your resolution, then click on the *Save to X configuration file* button.

---

### Post by dawynn on 2008-12-10
Thank you very much.  That should have been obvious to me.  Thank you for the very helpful reminder.  Closing this thread.

---

