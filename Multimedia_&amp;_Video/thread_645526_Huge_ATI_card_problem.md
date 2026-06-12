---
title: "Huge ATI card problem"
date: 2007-12-20
forum: Multimedia &amp; Video
---

### Post by grogger13 on 2007-12-20
I have an ati radeon mobility x1400 and i am running a fresh install of gutsy.  I had the proprietary drivers from the ubuntu repository working and the desktop effects working great, 

Then i stumbled upon this game Frets on Fire.  Installed it from the repositories and started it up when it kept crashing just as i went into a song or the tutorial.  So i searched around and decided to try updating the video driver.

I saw that ati's website had a more recent version so first i went into synaptic and uninstalled the xorg-fglrx driver and downloaded the one from ati.

Once i installed it and restarted x-server everything sucked.  It was all choppy and desktop effects were disabled.

then i followed this tutorial for installing and enabling ati card and Desktop Effects

<http://ubuntuforums.org/showthread.php?t=574302&highlight=ATI>

Desktop effects will enable but everything is extremely slow, moving windows, resizing windows,  The cube animation is basically useless.

The worst and most confusing of all it that my desktop doesn't work.

Nothing such as files or folders on my desktop show up(in the terminal you can seee there still there).  Even right clicking yields no drop down menu.



I need some serious help here.

__________________________________________________
Update-  I restarted my computer and the desktop appears to be back and working, but the effects are still no where near as good as they where before.  Also i did check the box to enable the ati restricted driver.

---

### Post by grogger13 on 2007-12-20
i am completely confused on what to do.  My video is horrible now.  I can't scroll with out it taking 2 seconds to refresh the screen.

When i type ```
fglrxinfo
```

my x server crashes


Is there anyway i can completely unistall all of the video drivers and just reinstall it the way i first did when i installed Gutsy for the first time.

---

