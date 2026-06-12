---
title: "Mplayer segfault in Gutsy: preinit_libvo"
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by Cappy on 2007-11-01
Launchpad URL: [https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/159861](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/159861)

Mplayer worked perfectly on Feisty before I upgraded. I have tried doing a purge remove and then reinstalling mplayer. If I disable compiz and reboot it still occurs. I've tried different -vo's including x11 gl gl2 xv. I rebuild the ~/.gstreamer-0.10 directory in case there was something that was kept from my upgrade from Feisty.

Most importantly, mplayer will play my videos at first but if I start a new mplayer later in my gnome session this is when it will crash! When I reboot or restart X mplayer begins working again. It seems to be something with the screensaver.

Happens with every video. Using the Gutsy nvidia-new drivers. Running AMD64.

And one more thing ... I tried using Valgrind from the instructions at [https://wiki.ubuntu.com/Valgrind](https://wiki.ubuntu.com/Valgrind) but mplayer ALWAYS works when I use the valgrind debugger.

The crash:
```

$ mplayer -v options Monster\ -\ 30.avi
MPlayer 2:1.0~rc1-0ubuntu13 (C) 2000-2006 MPlayer Team
............................. (edited)
Using built-in default codecs.conf.
............................. (edited)
Clip info:
 Software: VirtualDubMod 1.5.10.1 (build 2366/release)
get_path('sub/') -> '/home/cappy/.mplayer/sub/'
xscreensaver_disable: Could not find XScreenS
X11 opening display: :0.0
vo: X11 color mask: FFFFFF (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1280x1024 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
Disabling DPMS
DPMSDisable stat: 1aver window.

MPlayer interrupted by signal 11 in module: preinit_libvo
- MPlayer crashed by bad usage of CPU/FPU/RAM.
...... (edited out debug info) .....
vo: uninit ...

```

---

### Post by skibrianski on 2007-11-03
I'm having this problem too. I also notive that mplayer is *very* slow to start in gutsy, and it seems to be associated with searching for the xscreensaver window to disable it (although that is just speculation). Are you also on x86-64?

We should probably post this on launchpad.

PS - If I run mplayer32 from a chroot jail, it works fine. I'm not sure if that means the problem doesn't exist on x86, or that I just have different codecs, etc. installed which don't happen to crash in the jail).

---

### Post by Cappy on 2007-11-03
I've reported this on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/159861](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/159861)

---

### Post by Cappy on 2007-11-05
Disabling the screensaver is a temporary fix for this problem.

---

### Post by Cappy on 2007-11-06
running ```
killall gnome-screensaver
``` before running mplayer also resolves the problem but there it causes a pause.

I'm just going to leave my screensaver disabled since it also causes a SDL bug where I will start doing 180s in UT2004.

---

### Post by Cappy on 2007-11-16
Fix:
Open your videos with ```
gmplayer %f
```
as the command line in the "Open With.." dialog you get when you right click on a video.

---

