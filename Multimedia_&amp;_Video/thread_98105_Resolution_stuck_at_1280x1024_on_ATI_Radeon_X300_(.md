---
title: "Resolution stuck at 1280x1024 on ATI Radeon X300 (Solved)"
date: 2005-12-02
forum: Multimedia &amp; Video
---

### Post by Roobert on 2005-12-02
I'm using a 32bit dual-boot pentium4  running XP and 5.10 Breezy.  My display monitor (NEC Accusync LCD 200VX) works great on Windows at 1600x1200 res. Under Breezy, my highest res available under System/Preferences/Screen Resolution is 1280x1024. I just finished typing ```
sudo dpkg-reconfigure xserver xorg
```with the vesa driver option, which gets me where I'm at now, no 1600x1200. I've tried the ATI driver option, but that just gives me a [blank screen]("http://www.ubuntuforums.org/showthread.php?t=97203&"). 

The sticky posted on this forum inidcated that ATI drivers should only be installed for Radeon 8000/9000 series...is this correct? I'm kind of nervous installing new drivers  - will this interfere in any way with the drivers installed under Windows?

Sorry for my noob questions, I'm just not sure what questions I need to be asking you.

Thanks

SOLVED: I selected fglrx driver, and entered my graphics card memory of 65536KB. When I got to the section on configuring monitor resolutions and refresh rates, I choose the 'medium' option instead of the 'advanced' option as I had always done. The advanced option doesn't let you explicitly choose a resolution and refresh rate combination, whereas you can do so with the medium option. Also, I noticed that when I selected the medium option, the program had automatically selected 1280x1024 resolution by default. Maybe it was always selecting this resolution and I had never noticed it, where I had used the advanced option and never saw what resolution-refresh combination were being selected for me. Anyway, choosing 1600x1200 and 60Hz refresh from the medium potion fixed this problem.

---

