---
title: "How do I dissable screensaver"
date: 2009-10-04
forum: Mythbuntu
---

### Post by trevs.bronco on 2009-10-04
Hi All,

I have upgraded my Mplayer for VDPAU support in mythtv using JYA's repository. When I watch a video the screen fades to black every 10 minutes. how do I stop this from happening. It does not happen durring live tv or playback of recordings.
Thanks,
Trev

---

### Post by bsntech on 2009-10-07
Go to your Menu - System - Preferences - Screen Saver.

Turn off/deactivate the screensaver.  Also click the Power Management button and ensure you have the monitor to never turn off.

---

### Post by sisco311 on 2009-10-07
> **trevs.bronco said:**
> Hi All,

I have upgraded my Mplayer for VDPAU support in mythtv using JYA's repository. When I watch a video the screen fades to black every 10 minutes. how do I stop this from happening. It does not happen durring live tv or playback of recordings.
Thanks,
Trev

try:
```
mplayer -heartbeat-cmd "gnome-screensaver-command -p" file
```

---

