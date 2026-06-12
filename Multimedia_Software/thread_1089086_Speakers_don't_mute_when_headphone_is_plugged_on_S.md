---
title: "Speakers don't mute when headphone is plugged on Samsung X11"
date: 2009-03-06
forum: Multimedia Software
---

### Post by ferreat on 2009-03-06
Ubuntu Intrepid 10.8 installed on Samsung X11 laptop computer. When headphone is plugged in the jack, the in-built speakers don't mute. The problem doesn't happen when the laptop is started with Windows Vista. I've tried many solutions found googling the internet, but unfortunately non of them solved my problem. The system description is as follows:

ferreat:~$ aplay -l
**** Liste von PLAYBACK Geräten ****
Karte 0: Intel [HDA Intel], Gerät 0: AD198x Analog [AD198x Analog]
 Untergeordnete Geräte: 1/1
 Untergeordnetes Gerät '0: subdevice #0
Karte 0: Intel [HDA Intel], Gerät 6: Si3054 Modem [Si3054 Modem]
 Untergeordnete Geräte: 1/1
 Untergeordnetes Gerät '0: subdevice #0

ferreat:~$ lspci -v
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
       Subsystem: Samsung Electronics Co Ltd Device c026
       Flags: bus master, fast devsel, latency 0, IRQ 22
       Memory at d2300000 (64-bit, non-prefetchable) [size=16K]
       Capabilities: <access denied>
       Kernel driver in use: HDA Intel
       Kernel modules: snd-hda-intel
------------------------------------------------------------------------

---

### Post by artemhp on 2010-05-24
Have the same problem
Have tried to do this: [http://ubuntuforums.org/showthread.php?t=314383](http://ubuntuforums.org/showthread.php?t=314383)

Don't work.

---

### Post by artemhp on 2010-05-24
> **artemhp said:**
> Have the same problem
Have tried to do this: [http://ubuntuforums.org/showthread.php?t=314383](http://ubuntuforums.org/showthread.php?t=314383)

Don't work.
Maybe it will be useful:

artem@artem-laptop ~ $ cat /proc/asound/card*/codec#* | grep Codec 
Codec:  Analog Devices AD1986A
Codec: LSI Si3054

artem@artem-laptop ~ $ sudo alsa reload
[sudo] password for artem: 
lsof:  WARNING: can't stat() fuse.gvfs-fuse-daemon file system  /home/artem/.gvfs
      Output information may be incomplete.
/sbin/alsa:  Warning: Processes using sound devices: 1444(pulseaudio). 
Unloading  ALSA sound driver modules: snd-hda-codec-si3054 snd-hda-codec-analog  snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm  snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event  snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still  loaded: snd-hda-codec-si3054 snd-hda-codec-analog snd-hda-intel  snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading  ALSA sound driver modules: snd-hda-codec-si3054 snd-hda-codec-analog  snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm  snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event  snd-seq snd-timer snd-seq-device snd-page-alloc.

---

