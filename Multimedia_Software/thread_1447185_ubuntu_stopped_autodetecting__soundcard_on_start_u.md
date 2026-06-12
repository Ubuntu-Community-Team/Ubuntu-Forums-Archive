---
title: "ubuntu stopped autodetecting  soundcard on start up"
date: 2010-04-05
forum: Multimedia Software
---

### Post by birdy62 on 2010-04-05
Hi

Karmic 9.10
Asus F6J laptop

Previously I have had no problems with sound. After the installation of gnome-network-admin package, my soundcard was no longer autodetected on startup. I have since removed the package  but the problem remains. After boot-up in 'Sound Preferences' > 'Hardware' there is nothing shown. In > 'Output' it shows 'Dummy Output' . I can regain the sound by using 

```
alsa force-reload
```

Which gives the following output:

```
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/alasdair/.gvfs
      Output information may be incomplete.
Terminating processes: 1206lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/alasdair/.gvfs
      Output information may be incomplete.
 1721lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/alasdair/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/alasdair/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/alasdair/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-codec-si3054 
snd-hda-codec-realtek snd-hda-intel snd-hda-codec 
snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm 
snd-seq-dummy snd-seq-oss snd-seq-midi 
snd-rawmidi snd-seq-midi-eventsnd-seq snd-timer 
snd-seq-device snd-page-alloc 
(failed: modules still loaded: snd-hda-codec-si3054
 snd-hda-codec-realtek snd-hda-codec snd-hwdep snd-pcm 
snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-codec-si3054
 snd-hda-codec-realtek snd-hda-intel snd-hda-codec 
snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy 
snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event 
snd-seq snd-timer snd-seq-device snd-page-alloc.

```

Sound Preferences 'Hardware' then shows 'Internal Audio' 1 output 1 input Analogue Sterio

I added the package to run a modem for a short while, which is also onboard the sound chip, perhaps some conflict there?

Any clues?

---

### Post by birdy62 on 2010-04-06
bump! Is there anything I need to clarify in this post?

---

