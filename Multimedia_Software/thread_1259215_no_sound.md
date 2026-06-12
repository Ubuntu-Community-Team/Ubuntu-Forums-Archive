---
title: "no sound"
date: 2009-09-06
forum: Multimedia Software
---

### Post by shrimpboi13 on 2009-09-06
i've been using ubuntu 9.04 for the last couple of months and just recently i've lost the sound. :confused: it's really weired because the speakers are definitely working (tested with ipod) but when plugged into the machine all i get is crackling. this vexes me as when i first installed the OS the sound worked flawlessly i'm just wondering if anyone has an idea of how to fix this problem because i don't want to have to reinstall the OS.

p.s. i'm sure it isn't an internal hardware problem because my headphones don't work in an alternative jack.

any suggestions appreciated thankyou in advance.

---

### Post by scragar on 2009-09-06
```
killall pulseaudio
sudo alsa force-reload
pulseaudio -D
```Try running those in a terminal one after the other to restart the audio.

---

### Post by shrimpboi13 on 2009-09-07
this is what i got when i typed in the seccond command aka 
"sudo alsa force-relaod"
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/bill/.gvfs
      Output information may be incomplete.
Terminating processes: 6139lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/bill/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/bill/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/bill/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

thanks for the help so far.

---

