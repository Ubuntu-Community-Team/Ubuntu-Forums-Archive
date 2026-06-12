---
title: "Laggy Video on fullscreen Flash"
date: 2014-01-30
forum: Multimedia Software
---

### Post by steveearle86 on 2014-01-30
I am having issues with Flash on full screen in Chrome, Chromium and Firefox. The videos play fine in the default window but the video lags behind the sound on full screen. When you minimise back to the default window, the video quickly speeds up and catches up.

I can watch local files and DVDs fine through VLC full screen so I don't think it is a hardware issue.

There are so many variables, I don't know where to start!

[FONT=arial]I have installed ASLA but that has not done anything
I have disabled the [/FONT][FONT=arial]/opt.google/chrome/PepperFlash/libpepflashpalyer.so plug-in in chrome and left[/FONT][FONT=arial]/usr/lib/flashplugin-installer/libflashplayer.so active but that has done nothing either
Tried this [http://ubuntuforums.org/showthread.php?t=1987116](http://ubuntuforums.org/showthread.php?t=1987116)
and this [http://www.youtube.com/watch?v=SeO8YytqEKE](http://www.youtube.com/watch?v=SeO8YytqEKE)
It doesn't seem Flash Aid exists any more[/FONT]

Specs:

RAM : 3.5 GiB
CPU: AMD E-350D APU with Radeon(tm) HD Graphics × 2 
Graphics: Gallium 0.4 on AMD PALM
64 bit Ubuntu 13.10

Can anyone suggest any further action?

---

### Post by steveearle86 on 2014-01-30
The Youtube videos play perfectly full screen through VLC Open-->Network stream so this must be something with the Flash plugin surely?

---

### Post by Yellow Pasque on 2014-01-30
Yes, the Linux Flash plugin is a CPU hog when it comes to video. There's not much you can do short of using a native player or getting a faster CPU.

---

### Post by monkeybrain20122 on 2014-01-31
For many videos sites you can replace flash with mplayer or the Totem plugins using Viewtube.[http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011)
It is a lot easier on your cpu, but be careful with Firefox's mixed active content blocker, it may not work unless you disable mixed content blocker and reload the page (at the url bar) or use [https://addons.mozilla.org/En-us/firefox/addon/toggle-mixed-active-content/](https://addons.mozilla.org/En-us/firefox/addon/toggle-mixed-active-content/)

If you install the packages gstreamer-ffmpeg, x264 and have gstreamer enabled in Firefox (about:config -> media.gstreamer.enabled=true)you can access some sites without flash as they offer an html5 option if h264 is supported (e.g Ted talks, dailymotion and vimeo) For that to work flash needs to be disabled. When Viewtube works, it is usually the best in terms of performance.

---

### Post by steveearle86 on 2014-02-11
> **monkeybrain20122 said:**
> For many videos sites you can replace flash with mplayer or the Totem plugins using Viewtube.[http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011)


Thanks. So far so good on this:D

---

