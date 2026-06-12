---
title: "BBC iPlayer shows through black areas"
date: 2011-05-30
forum: Multimedia Software
---

### Post by SystemParadox on 2011-05-30
Hi everyone.

I have a very strange bug with the BBC iPlayer. The video/radio display area shows through black pixels on other windows. This includes other Firefox tabs, windows that cover Firefox, and different virtual desktops. It does make text somewhat difficult to read and is very irritating.

I'm blaming the flash plugin, but it does seem to be specific to iPlayer- YouTube videos work fine for example. I haven't been able to reproduce the problem with any other video software either. I don't have flash working in any other browsers so I can't test that.

I've had this issue since at least before Ubuntu 10.04. I'm currently on a fully updated 11.04 setup and the problem persists. I'm using KDE, but without Compiz or any other special rendering mode.

This problem includes both Firefox 3 and Firefox 4. I do use flashblock, but I find it very unlikely that makes any difference.

I'm mainly looking to see if this is a known problem before I do any more debugging or posting config files, etc. I haven't been able to find anything so far, but it's not obvious what terms to search for.

Any suggestions?

Thanks.
Simon

---

### Post by SystemParadox on 2011-05-30
It seems this issue is specific to NVidia, and is something to do with flash using OpenGL and VDPAU at the same time.

Symptoms seem to be referred to as an 'overlay'.

[https://bbs.archlinux.org/viewtopic.php?id=113368](https://bbs.archlinux.org/viewtopic.php?id=113368)

[http://boardreader.com/thread/New_flashplugin_10_2_video_overlay_issue_4vucX3fab.html?o=10](http://boardreader.com/thread/New_flashplugin_10_2_video_overlay_issue_4vucX3fab.html?o=10)

[http://www.nvnews.net/vbulletin/showthread.php?t=159779](http://www.nvnews.net/vbulletin/showthread.php?t=159779)

[https://bugs.launchpad.net/ubuntu/+bug/764620](https://bugs.launchpad.net/ubuntu/+bug/764620)

Problem persists with Chromium.

---

