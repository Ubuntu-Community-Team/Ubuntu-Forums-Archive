---
title: "mic problem in ubuntu 8.04"
date: 2010-06-02
forum: Multimedia Software
---

### Post by ignacio69 on 2010-06-02
Hello,
I have already read most of the posts in internet related to: ubuntu sound problem, trubleshootings, ekiga sound problem, mic sound problem, capture audio problem, pulseaudio (already killed and removed), ALSA, gnome-volume-control (evrything is red, nothing is unmuted), alsamixer: see my .png
This are the output of the commands that are normally required for people being able to help you:
arecord -l:
**** Lista de CAPTURE dispositivos hardware ****
tarjeta 0: NVidia [HDA NVidia], dispositivo 0: HDA Generic [HDA Generic]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
aplay -l:
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: NVidia [HDA NVidia], dispositivo 0: HDA Generic [HDA Generic]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
speaker-test -Dplughw:0,0 -c2:
I can hear all kind of test through my headphones

I can hear all kind of sounds in youtube, in shockwave, in adobe, mp3, wav, audacity, rythmbox, and totem; play sounds fine.

I just cannot use my mic either in ekiga, either in sound recorder, either in audacity.
My mic is a SPEEDLINK headphones with mic that I plugged in with a jack.
uname -r:
2.6.24-27-generic
can you tell me what information I can post to try it further.
thank you in advance

I followed a guide found in ubuntuforums: with this output
cat /proc/asound/card0/codec#* | grep Codec:
Codec: VIA ID 4397
vumeter -r &:
[1] 6440
arecord -f cd -vv /dev/null | arecord -f dat -vv /dev/null:
Grabación WAVE '/dev/null' : Signed 16 bit Little Endian, Ratio 44100 Hz, Estéreo
Plug PCM: Rate conversion PCM (48000, sformat=S16_LE)
Its setup is:
  stream       : CAPTURE
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
  start_threshold  : 1
  stop_threshold   : 15052
  silence_threshold: 0
  silence_size : 0
  boundary     : 986447872
Slave: Soft volume PCM
Control: Digital Capture Volume
min_dB: -30
max_dB: 30
resolution: 121
Its setup is:
  stream       : CAPTURE
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
  start_threshold  : 1
  stop_threshold   : 16384
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
Slave: Direct Snoop PCM
Its setup is:
  stream       : CAPTURE
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
  start_threshold  : 1
  stop_threshold   : 16384
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
Hardware PCM card 0 'HDA NVidia' device 0 subdevice 0
Its setup is:
  stream       : CAPTURE
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
  tstamp_mode  : MMAP
  period_step  : 1
  sleep_min    : 0
  avail_min    : 1024
  xfer_align   : 1024
  start_threshold  : 1
  stop_threshold   : 1073741824
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
Grabación WAVE '/dev/null' : Signed 16 bit Little Endian, Ratio 48000 Hz, Estéreo
Plug PCM: Soft volume PCM
Control: Digital Capture Volume
min_dB: -30
max_dB: 30
resolution: 121
Its setup is:
  stream       : CAPTURE
  access       : RW_INTERLEAVED
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
  start_threshold  : 1
  stop_threshold   : 16384
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
Slave: Direct Snoop PCM
Its setup is:
  stream       : CAPTURE
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
  start_threshold  : 1
  stop_threshold   : 16384
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
Hardware PCM card 0 'HDA NVidia' device 0 subdevice 0
Its setup is:
  stream       : CAPTURE
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
  tstamp_mode  : MMAP
  period_step  : 1
  sleep_min    : 0
  avail_min    : 1024
  xfer_align   : 1024
  start_threshold  : 1
  stop_threshold   : 1073741824
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
####+                                              | 06%
Abortado por la señal Interrupción...
Abortado por la señal Interrupción...
[1]+  Exit 1                  vumeter -r

 uname -r:
2.6.24-27-generic

can you tell me what information I can post to try it further.
thank you in advance

---

### Post by ignacio69 on 2011-01-03
Dear all,
after nobody answering, I upgraded to 10.04 
and in this link I found the solution: [http://ubuntuforums.org/showthread.php?t=1504904](http://ubuntuforums.org/showthread.php?t=1504904)
I decided to mark it as solved because I cannot try it anymore with ubuntu 8.04, but I have the feeling that if the set up of "alsamixer"  will have the mic controls in playback 'mute', it should work.
If anybody needs more help, I will be glad to answer them

---

