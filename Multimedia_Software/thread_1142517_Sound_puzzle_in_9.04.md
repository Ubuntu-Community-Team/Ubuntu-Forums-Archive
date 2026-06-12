---
title: "Sound puzzle in 9.04"
date: 2009-04-29
forum: Multimedia Software
---

### Post by gewitty on 2009-04-29
Just installed 9.04 and have an interesting sound problem.

Although I get system sounds and things like Skype work OK, multimedia apps have no sound (at least, it's so quiet you can barely hear it).

I've worked through the various sound problem solutions in other threads, but got nothing until I tried running also force-reload. Immediately, all my sound started working. The problem is that after a re-boot, I have to do the same thing again. Below is the output I get when I run the force-reload command:


dave@dave-desktop:~$ sudo alsa force-reload
[sudo] password for dave: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/dave/.gvfs
      Output information may be incomplete.
Terminating processes: 3729 3799lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/dave/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/dave/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/dave/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
dave@dave-desktop:~$ 

Anybody got suggestions as to how I make the fix permanent?

---

