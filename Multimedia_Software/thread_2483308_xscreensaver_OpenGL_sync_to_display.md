---
title: "xscreensaver OpenGL sync to display"
date: 2023-01-26
forum: Multimedia Software
---

### Post by mocha on 2023-01-26
Using Xubuntu 22.10 here with Nvidia proprietary drivers.  I started to notice that xscreensaver OpenGL screensavers no longer synchronize to the vertical scan rate of my monitor.  This seems to be a new thing with 22.10.

Prior I used to specify some environment variables in a script before starting xscreensaver like this.

```
export __GL_SYNC_DISPLAY_DEVICE="DP-1"
export __GL_SYNC_TO_VBLANK=1
xscreensaver -no-splash & disown
```

This would synchronize any Open GL screensaver to the 60 Hz of my monitor.  It doesn't seem to work any more on 22.10.  I see tearing.  Anyone else notice this?  I suspect it's not just an Nvidia issue.  glxgears is sync'd to the 60 Hz and so are other OpenGL and Vulkan programs.

---

