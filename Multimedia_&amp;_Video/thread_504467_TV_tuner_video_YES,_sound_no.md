---
title: "TV tuner: video: YES, sound: no"
date: 2007-07-19
forum: Multimedia &amp; Video
---

### Post by Matthai on 2007-07-19
I have a TV tuner card from Pinnacle.

I am using TV time, and video is good, but there is no sound, just loud noise when I turn on "AUX" or "Line-in" in ALSAmixer (depending where sound cable is connected). I have connected sound cable.


However, lspci says:

02:00.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
02:00.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

And lsmod says:

tuner 61864 0
bttv 173684 1 bt878
video_buf 26116 1 bttv
ir_common 31236 1 bttv
compat_ioctl32 2304 1 bttv
i2c_algo_bit 8712 1 bttv
btcx_risc 5896 1 bttv
tveeprom 15888 1 bttv
i2c_core 22656 5 i2c_ec,tuner,bttv,i2c_algo_bit,tveeprom
videodev 28160 1 bttv
v4l2_common 25216 3 tuner,bttv,videodev
v4l1_compat 15236 1 videodev

snd_intel8x0 34332 1
snd_ac97_codec 98464 1 snd_intel8x0
ac97_bus 3200 1 snd_ac97_codec
snd_pcm_oss 44544 0
snd_mixer_oss 17408 1 snd_pcm_oss
snd_pcm 79876 3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy 4740 0
snd_seq_oss 32896 0
snd_seq_midi 9600 0
snd_rawmidi 25472 1 snd_seq_midi
snd_seq_midi_event 8448 2 snd_seq_oss,snd_seq_midi
snd_seq 52592 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer 23684 2 snd_pcm,snd_seq
snd_seq_device 9100 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
bt878 11960 0
pcspkr 4224 0
snd 54020 12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore 8672 1 snd


Any idea?

---

