---
title: "saa7134 analog no sound but picture"
date: 2007-12-02
forum: Multimedia &amp; Video
---

### Post by amsch on 2007-12-02
Hi!

I have searched the forums here already but I could not find a post which solved my problem:

Im using Kubuntu 7.10 and I want to watch TV using my TV card (analog). I have already managed to see a picture but there is still no sound available.

```

andreas@neo:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 2: ALC883 Analog [ALC883 Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: SAA7134 [SAA7134], device 0: SAA7134 PCM [SAA7134 PCM]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

andreas@neo:~$ lsmod | grep saa7134
saa7134_alsa           15392  0
snd_pcm                80388  4 saa7134_alsa,snd_hda_intel,snd_pcm_oss
saa7134               129100  1 saa7134_alsa
snd                    54660  14 saa7134_alsa,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video_buf              26244  2 saa7134_alsa,saa7134
compat_ioctl32          2304  1 saa7134
ir_kbd_i2c              9872  1 saa7134
i2c_core               26112  3 nvidia,saa7134,ir_kbd_i2c
ir_common              35460  2 saa7134,ir_kbd_i2c
videodev               29312  1 saa7134
v4l2_common            18432  2 saa7134,videodev
v4l1_compat            15364  2 saa7134,videodev
andreas@neo:~$

```

```

[ 1105.654813] saa7134 ALSA driver for DMA sound unloaded
[ 1120.384546] saa7130/34: v4l2 driver version 0.2.14 loaded
[ 1120.384788] saa7133[0]: found at 0000:02:01.0, rev: 209, irq: 22, latency: 84, mmio: 0xfddff000
[ 1120.384794] saa7133[0]: subsystem: 16be:000d, board: LifeView FlyTV Platinum Mini [card=39,insmod option]
[ 1120.384801] saa7133[0]: board init: gpio is 0
[ 1120.518392] saa7133[0]: i2c eeprom 00: be 16 0d 00 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[ 1120.518401] saa7133[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff 00 01 50 32 79 01 3c ca 50
[ 1120.518408] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 03 01 00 06 ff 00 29 02 51 96 2b
[ 1120.518415] saa7133[0]: i2c eeprom 30: a7 58 7a 1f 03 8e 84 5e da 7a 04 b3 05 87 b2 3c
[ 1120.518421] saa7133[0]: i2c eeprom 40: ff 28 00 c0 96 10 03 00 c0 1c fd 79 44 9f c2 8f
[ 1120.518428] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1120.518435] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1120.518441] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1120.610159] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[ 1123.421844] saa7133[0]: registered device video0 [v4l2]
[ 1123.421948] saa7133[0]: registered device vbi0
[ 1123.492233] saa7134 ALSA driver for DMA sound loaded
[ 1123.492258] saa7133[0]/alsa: saa7133[0] at 0xfddff000 irq 22 registered as card -2

```

I have a seperate partion where Windows is installed and there everything work fine. Furthermore I have already tried watching TV using tvtime, kdetv and mplayer - with all 3 I get a picture but no sound.

```

v4lctl -c /dev/video0 volume mute on
alsamixer

```

both did not work as well.


Can anybody please help me?

Thank you very much!

---

