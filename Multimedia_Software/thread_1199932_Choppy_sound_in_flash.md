---
title: "Choppy sound in flash"
date: 2009-06-29
forum: Multimedia Software
---

### Post by happygizmo11 on 2009-06-29
Hi I have seen alot of problems with choppy flash video but not the sound. When I am watching flash videos the sound is a little choppy like a blade spinning across it. The video works fine but the sound is choppy. Does anyone have any ideas?

---

### Post by lovinglinux on 2009-06-29
[Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by happygizmo11 on 2009-06-29
Hey thanks for the link but it did not resolve my problem. More suggestions would be appreciated.

---

### Post by happygizmo11 on 2009-06-30
bump

---

### Post by lovinglinux on 2009-06-30
> **happygizmo11 said:**
> Hey thanks for the link but it did not resolve my problem. More suggestions would be appreciated.

This should fix your problem

> **[color=#CC0000]Remove pulseaudio and install esound:[/color]** this can improve performance considerably and solve issues of audio out-of-sync.

[How-To](http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html)

**[color=#FF0000]Warning:[/color]** *when you remove pulseaudio or install esound, the package manager also removes the metapackage ubuntu-desktop. Don't worry, this file is used only for upgrades between Ubuntu releases. Just make sure you install it before upgrading. If you do clean installs between releases, then you don't need to worry about it.*

If you are uncomfortable by removing pulseaudio, then you can easily revert this and install it again.

Another option would be trying to [fix pulseaudio](http://ubuntuforums.org/showthread.php?t=789578).

---

