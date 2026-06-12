---
title: "Gstreamer Setup and Configuring"
date: 2008-11-09
forum: Multimedia Software
---

### Post by derpnooner on 2008-11-09
Hello,

I am trying to fix a couple of problems.  When I use TOTEM to watch videos i found that when I moved the window, the video didn't follow the window.  I learned that configuring gstreamer to use No NV the video would move with the window, but full screen was slow.

Is there any way to use NO NV mode while in windowed mode and use NV overlay mode while in full screen?

I can use one or the other and I would love to be able to use the best of both worlds.

Thank you,
Community

---

### Post by psyke83 on 2008-11-09
> **derpnooner said:**
> Hello,

I am trying to fix a couple of problems.  When I use TOTEM to watch videos i found that when I moved the window, the video didn't follow the window.  I learned that configuring gstreamer to use No NV the video would move with the window, but full screen was slow.

Is there any way to use NO NV mode while in windowed mode and use NV overlay mode while in full screen?

I can use one or the other and I would love to be able to use the best of both worlds.

Thank you,
Community

Unfortunately that's not possible.

Try toggling the following gconf variable (restart compiz or log out/in to take effect): /apps/compiz/general/screen0/options/unredirect_fullscreen_windows

---

### Post by derpnooner on 2008-11-09
how do i do that?

Sorry, still fairly new to this.

---

