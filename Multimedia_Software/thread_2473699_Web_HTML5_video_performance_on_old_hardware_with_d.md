---
title: "Web HTML5 video performance on old hardware with decent CPU"
date: 2022-04-11
forum: Multimedia Software
---

### Post by pmb2 on 2022-04-11
I have a quite old system that I'd like to use as a video player. When I stream videos in the browser, I get stuttering / judder (not sure about the exact term): especially when panning scenes with many details, the video appears to be choppy. I don't see many dropped frames in Youtube "Stats for Nerds" - for some reason, the problem doesn't show up as dropped frames. I get the issue on other sites, not just YouTube. It's not horrible, but very noticable in some scenes.

I'm using Kubuntu (Plasma desktop). I have enabled an option in the radeon driver to prevent tearing - without this, the video had bad tearing and was unwatchable.

```
/etc/X11/xorg.conf.d/fa-settings.conf:
----
Section "Device"
        Identifier      "AMD Graphics"
        Driver          "radeon"
        Option          "TearFree" "true"
EndSection
```


I have tried various combinations:

 * X11 or Wayland (Wayland gives slightly more dropped frames in Youtube, so I didn't test it much)
 * Firefox and Chrome
 * Enable or disable hardware acceleration in Firefox. When enabled, the CPU utilisation is about 35 %, when disabled, it is about 90 % (80-110%).
 * Disable compositing in X11 (Alt-Shift-F12)
* Playing local files in VLC seems to work perfectly smoothly.


The hardware is a  VM on a home server that I want to use as a video player on a TV (1080p, 60 Hz). It's configured with GPU passthrough. It should have more than enough CPU to do the decoding in software, if it can work in multi-threaded mode. If single-threaded, then probably enough but not sure. The GPU doesn't support codecs like VP9 and WebM, so I think it's not very interesting to mess about with GPU hardware decoding.

CPU: Xeon E5-2697 v2 (8 cores assigned to VM)
GPU :  [AMD/ATI] Turks GL [FirePro V3900]

The fact that it's a VM could lead to some variable latency, but there's no other significant loads running.

I'd really appreciate if someone has any tips to try!

---

### Post by pmb2 on 2022-04-11
I just tried to log into the "Ubuntu" session on the display manager. Using Gnome and Wayland: It's *much* better!

Kind of silly to not try this, sorry. I had changed to KDE due to a bug related to Discord, but I no longer use Discord on this computer, so it's all good.

---

