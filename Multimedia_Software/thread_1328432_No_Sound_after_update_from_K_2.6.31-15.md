---
title: "No Sound after update from K 2.6.31-15"
date: 2009-11-16
forum: Multimedia Software
---

### Post by deadgobby on 2009-11-16
After the last mass up date from 2.6.31-15 I have no sound running at all. It seems to contradict my sound blaster and the on board device. Mainly  Rest a sure that the BIOS has the on board device disable. Reverted back to a older kernel and the sound works through the blaster. However, I am a lost to this one kids.  
 It sees my sound blaster card and my on board as the same device. Ump I am a lost. Here is my list sound list. 
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

It work fine a couple a days ago and now. I am being cool and see if some one knows the KISS method. Soon I am going to take this out of marinade and put this on the grill. 
Love Ubutie since 2005
Gobby

---

### Post by deadgobby on 2009-11-17
bump

---

### Post by deadgobby on 2009-11-17
Here what it says when trying to force ALSA


lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/doug/.gvfs
      Output information may be incomplete.
Terminating processes: 2725lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/doug/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/doug/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/doug/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-ca0106 snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-ca0106 snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
doug@Gobby-desktop:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/doug/.gvfs
      Output information may be incomplete.
Terminating processes: 3533lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/doug/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/doug/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/doug/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-ca0106 snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-ca0106 snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
doug@Gobby-desktop:~$

---

### Post by xc3RnbFO8P on 2009-11-17
Did you check **dmesg**?

---

### Post by deadgobby on 2009-11-17
This is what I got on dmesg

[   20.847972] CA0106 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.848116] snd-ca0106: Model 1006 Rev 00000000 Serial 10061102

Thank you for your help.

---

### Post by xc3RnbFO8P on 2009-11-17
You can try this, 
in Terminal:
> alsamixer
if it isn't installed:
> sudo apt-get install gnome-alsamixer
If got Audigy Analog/ digital output jack, uncheck it

---

### Post by deadgobby on 2009-11-17
I have a sound blaster live card and that did not work.

---

### Post by deadgobby on 2009-11-17
I'll be damned. Rebooted for the F of it. Working now. Thanks for your help.

---

