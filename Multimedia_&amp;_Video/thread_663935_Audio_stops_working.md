---
title: "Audio stops working"
date: 2008-01-10
forum: Multimedia &amp; Video
---

### Post by reets on 2008-01-10
I am using Kubuntu 7.10 and randomly lose sound sometimes. Here is some info I have seen others ask for. I have also freshly rebooted and system sounds seem to work.

I have tried:
dave@dave-desktop:~$ sudo /etc/init.d/alsa-utils restart
dave@dave-desktop:~$ sudo alsactl store


Info:
dave@dave-desktop:~$ aplay
aplay: main:545: audio open error: Device or resource busy

dave@dave-desktop:~$ groups
dave adm dialout cdrom floppy audio dip video plugdev scanner netdev lpadmin powerdev admin mythtv vboxusers

dave@dave-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

dave@dave-desktop:~$ lsof /dev/dsp

dave@dave-desktop:~$ ls -l /dev/dsp
crw-rw---- 1 root audio 14, 3 2008-01-10 17:58 /dev/dsp

dave@dave-desktop:~$ ls -l /dev/audio
crw-rw---- 1 root audio 14, 4 2008-01-10 17:58 /dev/audio

---

### Post by scriptfighter on 2008-03-04
Hi,

I have the same problem, but who knows what this exactly is about.

I play a video in mplayer, it works fine at the start and then it stops, I mean the screen is still up but it is stopped and I have to quit mplayer or kill it. There is no pattern for stopping, only thing is that after it stops once, then the next stops after mplayer restart with the same video happen much sooner.

Same video in xine works fine, never stops, but the sound stops randomly, sometimes recovers after a long time, 20 - 30 minutes. In xine it is also recoverable by switching the audio channel.

Also flash in firefox or opera stops randomly, while on youtube, I'm guessing for the same reason.

Some system info:

$uname -l
Linux lnx 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

$aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$lsmod | grep snd
snd_intel8x0           34972  4 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec
snd_timer              24324  2 snd_pcm
snd                    54660  10 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm

After the sound stops, I try to run the aplay in verbose mode, this is what I get, and it never finishes, have to press Ctrl+C:

$ aplay -v /usr/share/sounds/login.wav 
Playing WAVE '/usr/share/sounds/login.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
Plug PCM: Rate conversion PCM (48000, sformat=S16_LE)
Its setup is:
  stream       : PLAYBACK
  access       : RW_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 2
  rate         : 44100
  exact rate   : 44100 (44100/1)
  msbits       : 16
  buffer_size  : 15052
  period_size  : 940
  period_time  : 21333
  tick_time    : 0
  tstamp_mode  : NONE
  period_step  : 1
  sleep_min    : 0
  avail_min    : 940
  xfer_align   : 940
  start_threshold  : 15040
  stop_threshold   : 15052
  silence_threshold: 0
  silence_size : 0
  boundary     : 986447872
Slave: Direct Stream Mixing PCM
Its setup is:
  stream       : PLAYBACK
  access       : MMAP_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 2
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 16
  buffer_size  : 16384
  period_size  : 1024
  period_time  : 21333
  tick_time    : 0
  tstamp_mode  : NONE
  period_step  : 1
  sleep_min    : 0
  avail_min    : 1024
  xfer_align   : 1024
  start_threshold  : 16384
  stop_threshold   : 16384
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
Hardware PCM card 0 'Intel ICH5' device 0 subdevice 0
Its setup is:
  stream       : PLAYBACK
  access       : MMAP_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 2
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 16
  buffer_size  : 16384
  period_size  : 1024
  period_time  : 21333
  tick_time    : 4000
  tstamp_mode  : NONE
  period_step  : 1
  sleep_min    : 0
  avail_min    : 1024
  xfer_align   : 1024
  start_threshold  : 1
  stop_threshold   : 1073741824
  silence_threshold: 0
  silence_size : 1073741824
  boundary     : 1073741824



-------------

Any ideas anybody ? 
I'm searching and trying for a week now, nothing is helping so far.

---

### Post by superprash2003 on 2008-03-04
maybe this might help [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by scriptfighter on 2008-03-07
Hey,

I'm still trying and digging. However I discovered something very interesting.
During night time, approx. 11 PM or later, the sound works perfect. Either I play a DVD or watch youtube, it works.
I know it sounds crazy, but this is the fact. 
I'm wondering if there is something running in the daytime that is messing up the sound. I checked for cron jobs, and I canno find any. What else is there that could be causing this ?

NO NO NO, I was wrong, it stops even at night. :(

Still looking......

Thanks.

---

### Post by scriptfighter on 2008-03-07
Some progress:

turns out that the problem was with the nvidia driver. I changed my xorg.conf to use "nv" instead, for now, and the videos play just fine. This was a bit surprising, since during the video playback the sound would disapear in mplayer and then shortly after that the video would stop. Even bigger mistery is xine, where the sound would vanish, but the video would continue playing without problems.

I played only one full DVD, browsed youtube and also played xmms for an hour, so not that much test results yet, but looks very promissing.

Anybody has an idea of why would the nvidia driver cause this kind of mess ?

Thanks.

---

