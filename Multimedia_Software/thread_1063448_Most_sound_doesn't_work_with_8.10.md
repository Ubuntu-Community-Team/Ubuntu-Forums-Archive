---
title: "Most sound doesn't work with 8.10"
date: 2009-02-07
forum: Multimedia Software
---

### Post by awacs on 2009-02-07
since upgrading to 8.10, (most) sound doesn't work. I have the terminal bell and nothing else. Where to begin? I have:

e# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

# lsmod|grep snd
snd_intel8x0           37532  5 
snd_ac97_codec        110372  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46720  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83332  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38400  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29832  3 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  18 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16264  2 snd_intel8x0,snd_pcm

---

### Post by awacs on 2009-02-07
Just found this is user.log:

Feb  5 23:55:10 yankel-laptop bonobo-activation-server (awacs-11817): could not associate with desktop session: Failed to connect to socket /tmp/dbus-RIWnuR5pus: Connection refused
Feb  7 19:28:42 yankel-laptop pulseaudio[5196]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb  7 19:28:42 yankel-laptop pulseaudio[5198]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb  7 19:28:42 yankel-laptop pulseaudio[5198]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb  7 19:28:42 yankel-laptop pulseaudio[5198]: shm.c: shm_open() failed: Permission denied
Feb  7 19:28:42 yankel-laptop pulseaudio[5198]: core.c: failed to allocate shared memory pool. Falling back to a normal memory pool.
Feb  7 19:28:59 yankel-laptop pulseaudio[5198]: module-x11-xsmp.c: X11 session manager not running.
Feb  7 19:28:59 yankel-laptop pulseaudio[5198]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.


I just added the pulseaudio icon to the gnome panel, but starting Volume Control from it gives "Connection Refused". Starting the Manager gives "n/a" for the server information, and Failure: Connection Refused at the bottom.

---

### Post by markbuntu on 2009-02-07
Go here and follow the directions

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

