---
title: "Audio stops work on ubuntu 14.04"
date: 2014-09-22
forum: Multimedia Software
---

### Post by dyegomb on 2014-09-22
Hello everybody,

Since I installed ubuntu 14.04, the audio work for a time but  stop work randomly and the headphone dont work at all.
I tried order linux distros like fedora and linux mint and the same occurs. When I was used the ubuntu 13.10 it not happened.

I've tried this procedures, but still not work:
[http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/](http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/)

When I try "sudo alsa force-reload", this message appears:
Unloading  ALSA sound driver modules: snd-hda-intel snd-hda-codec-hdmi  snd-hda-codec-conexant snd-hda-codec snd-hwdep snd-pcm snd-page-alloc  snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device  snd-timer (failed: modules still loaded: snd-hda-intel  snd-hda-codec-hdmi snd-hda-codec-conexant snd-hda-codec snd-hwdep  snd-pcm snd-page-alloc snd-timer).
Loading ALSA sound driver modules:  snd-hda-intel snd-hda-codec-hdmi snd-hda-codec-conexant snd-hda-codec  snd-hwdep snd-pcm snd-page-alloc snd-seq-midi snd-seq-midi-event  snd-rawmidi snd-seq snd-seq-device snd-timer.

The only way to get audio again without reboot is suspending and wake up again the computer...

I've used the alsa script to collect this informations:
[http://www.alsa-project.org/db/?f=884e86af53289e907f97b89b4327062919bfd8b0](http://www.alsa-project.org/db/?f=884e86af53289e907f97b89b4327062919bfd8b0)

[www.alsa-project.org/alsa-info.sh]("http://www.alsa-project.org/alsa-info.sh")

Thanks in anticipation

---

### Post by dyegomb on 2014-11-12
I found a bug report to this problem:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1038479](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1038479)

---

