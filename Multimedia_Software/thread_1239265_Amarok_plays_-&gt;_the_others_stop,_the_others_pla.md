---
title: "Amarok plays -&gt; the others stop, the others play -&gt; amarok stops"
date: 2009-08-13
forum: Multimedia Software
---

### Post by saysec on 2009-08-13
Hi
I use Ubuntu 9.04, and I installed Amarok 2.0.2
I installed and I can listen to music without any problem. On the other hand when I open it, the other sounds such as youtube, is disabled. Vice versa.

Do you have any idea what could it be?

---

### Post by ronaldprettyman on 2009-08-13
Amarok's been doing this to me, I switched to Exaile, much better player. But if you insist on using amarok. A quick fix when switching is close amarok completely then run.

sudo /etc/init.d/alsa restart (might be alsatools tab key works great here)
could also try
sudo alsa reload

---

### Post by saysec on 2009-08-13
I tried the first one, it said the command couldn't found
and for the second one:

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/saygin/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 3266(pulseaudio) 3529(mixer_applet2).
Unloading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-intel snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-eventsnd-seq snd-timer snd-seq-device snd-page-alloc.


I like Amarok, but if I cannot solve this prob, of course I have to use sth else.

---

### Post by BbUiDgZ on 2009-08-13
> **saysec said:**
> I tried the first one, it said the command couldn't found
and for the second one:

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/saygin/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 3266(pulseaudio) 3529(mixer_applet2).
Unloading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-intel snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-eventsnd-seq snd-timer snd-seq-device snd-page-alloc.


I like Amarok, but if I cannot solve this prob, of course I have to use sth else.

type "sudo /etc/init.d/alsa" then press the TAB key for auto complete

---

### Post by markbuntu on 2009-08-13
The problem with Amarok2 is that is uses the phonon sound server which is part of KDE4. Phonon uses the xine backend for now though a gstreamer backend is in the works. If you are using gnome you have no way to change the phonon default. But you can change the xine audio preference to alsa or pulseaudio using xine-ui which is the xine player and user interface. It is in the repositories so you can get it with Synaptic package manager.

If you use applications like amark and vlc that use xine the xine-ui is very handy for setting and changing all the xine defaults (which is a lot).

If you have pulseaudio set up properly then all your applications should have no problem sharing the hardware. If you need help with that go here

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

---

### Post by Old Old Duffers on 2009-08-17
> **ronaldprettyman said:**
> Amarok's been doing this to me, I switched to Exaile, much better player. But if you insist on using amarok. A quick fix when switching is close amarok completely then run.

sudo /etc/init.d/alsa restart (might be alsatools tab key works great here)
could also try
sudo alsa reload

You're correct about Exaile being a better play than Amarok!  Love it!!!

---

