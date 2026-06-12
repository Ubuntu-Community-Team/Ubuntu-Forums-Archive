---
title: "Audio Disappears After A While"
date: 2008-12-31
forum: Multimedia Software
---

### Post by PCHome on 2008-12-31
Using Ubuntu release 8.10 with kernel 2.6.27-9-generic and Gnome 2.24.1, when the system is first booted up, the audio is fine. However, when it is unused for some time, say overnight or even for a few hours, it takes a reboot to get the audio working again. There are no errors but there is also no audio from any source. The audio hardware is build-in to the Shuttle motherboard but I am not sure of the chipset or how to find out in Ubuntu.

I'm not sure whether to report this as a bug or not. Any ideas as to the cause (and a solution) or is it a bug?

Thanks.
Don

---

### Post by markbuntu on 2008-12-31
There is a problem with some of the alsa drivers that will hopefully be fixed soon. Meanwhile you can do this and at least you will not have to reboot

```

killall pulseaudio

sudo alsa force-reload

pulseaudio -D

```

If you are not using pulseaudio, you can skip the pulseaudio commands.

---

### Post by PCHome on 2008-12-31
Thanks for the tip! I tried it - all of it since I was unsure of which parts were needed on my system - but it generated errors and the audio is still missing. Maybe there is something in the error to give a clue:

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/don/.gvfs
      Output information may be incomplete.
Terminating processes: 6615lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/don/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/don/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/don/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-via82xx snd-ac97-codec snd-mpu401-uart snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-via82xx snd-ac97-codec snd-mpu401-uart snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

---

