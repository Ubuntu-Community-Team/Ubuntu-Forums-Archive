---
title: "sound suddenly gone"
date: 2009-04-18
forum: Multimedia Software
---

### Post by jdforsythe on 2009-04-18
After my last update, or sometime around there, my sound quit working.

I have had issues in the past, but it only affected audio in Flash and restarting pulseaudio (sudo killall pulseaudio then pulseaudio -D) would cure it for awhile.

Now all my sound is gone. All my media players work fine. When I do sudo alsa force-reload, it makes a pop through the speakers (like it did when I restarted pulseaudio).

Some output:

jdf@jdf-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


jdf@jdf-desktop:~$ dmesg
...
[   19.959308] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   19.959563] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
...


jdf@jdf-desktop:~$ grep 'audio' /etc/group
audio:x:29:pulse:jdf



jdf@jdf-desktop:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/jdf/.gvfs
      Output information may be incomplete.
Terminating processes: 7482 7522lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/jdf/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/jdf/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/jdf/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-via82xx snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-mpu401-uart snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.
Loading ALSA sound driver modules: snd-via82xx snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-mpu401-uart snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.



Any ideas?

---

### Post by jdforsythe on 2009-04-20
anybody?

---

