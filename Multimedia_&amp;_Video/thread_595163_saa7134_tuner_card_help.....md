---
title: "saa7134 tuner card help...."
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by Bally on 2007-10-28
Hi 

I am trying to get TV via a Pinnacle tv capture card, all the modules appear to be loaded correctly and to be honest given my lack of knowlegde of linux I am stuck. here;s my mod output:

bally@bally:~$ lsmod |grep saa
saa7134_alsa           15392  1
snd_pcm                79876  4 saa7134_alsa,snd_ens1371,snd_ac97_codec,snd_pcm_oss
saa7134               132432  1 saa7134_alsa
snd                    54020  15 saa7134_alsa,snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
compat_ioctl32          2304  1 saa7134
videobuf_dma_sg        14596  2 saa7134_alsa,saa7134
videobuf_core          18052  2 saa7134,videobuf_dma_sg
ir_kbd_i2c             10768  1 saa7134
ir_common              36100  2 saa7134,ir_kbd_i2c
i2c_core               22656  9 i2c_ec,tuner,tea5767,tda8290,tuner_simple,mt20xx,saa7134,ir_kbd_i2c,i2c_viapro
videodev               29056  1 saa7134
v4l2_common            18432  3 tuner,saa7134,videodev
v4l1_compat            15236  2 saa7134,videodev

and the dmesg:
[  122.862766] saa7130/34: v4l2 driver version 0.2.14 loaded
[  122.863430] saa7134[0]: found at 0000:00:07.0, rev: 1, irq: 21, latency: 32, mmio: 0xcfffb800
[  122.863435] saa7134[0]: subsystem: 11bd:002b, board: Pinnacle PCTV Stereo (saa7134) [card=26,autodetected]
[  122.863445] saa7134[0]: board init: gpio is 0
[  123.009275] saa7134[0]: i2c eeprom 00: bd 11 2b 00 f8 f8 1c 00 43 43 a9 1c 55 d2 b2 92
[  123.009283] saa7134[0]: i2c eeprom 10: 00 00 19 0e ff 20 ff ff ff ff ff ff ff ff ff ff
[  123.009289] saa7134[0]: i2c eeprom 20: 01 40 01 03 03 ff 03 01 08 ff 00 53 ff ff ff ff
[  123.009295] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  123.009301] saa7134[0]: i2c eeprom 40: ff 07 00 c0 86 ff 01 01 ff ff ff ff ff ff ff ff
[  123.009307] saa7134[0]: i2c eeprom 50: 0c 22 17 34 02 82 73 31 ff ff ff ff ff ff ff ff
[  123.009313] saa7134[0]: i2c eeprom 60: 03 03 19 71 fb ff ff ff ff ff ff ff ff ff ff ff
[  123.009319] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  123.264790] tuner 1-0043: chip found @ 0x86 (saa7134[0])
[  123.288752] tuner 1-0060: chip found @ 0xc0 (saa7134[0])
[  123.435059] saa7134[0]: registered device video0 [v4l2]
[  123.435081] saa7134[0]: registered device vbi0
[  124.636381] saa7134 ALSA driver for DMA sound loaded
[  124.636411] saa7134[0]/alsa: saa7134[0] at 0xcfffb800 irq 21 registered as card -2

I interpret this as showing that the card has been detected, configured and modules loaded.....so what now?

Any help will be greatly appreciated, if you need further just let me know

Cheers Bally ( :mad: frustrated but keen to learn!)

---

### Post by Bally on 2007-10-28
Problem resolved......well sort of:

I was trying to use kaffine, so......

Installed Tvtime and got signal reception, :) turns out that there was nothing really wrong! (with the card install anyway)

However i have No sound from the channels I guess it could be an alsa configuration issue...will now look into this...........

But any ideas appreciated?


Bally

---

### Post by Bally on 2007-10-29
Well I got sound working.....how?

By installing xawtv and selecting option to turn off automute in the options. Went back to TV time and hey presto sound is working.....

Hope this helps someone.....

Bally

---

### Post by eldragon on 2007-10-30
ive got a pinnacle tv card and i was never able to get sound OFF the card directly, i had to pass the sound through a patch cable to the sound card's line in.

did you accomplish that? how? xawtv never really worked for me

---

### Post by Bally on 2007-10-30
Ok to answer your question and give an update:

For connections I have now tried two methods, 

I have an audio out connector on the card (ie. internal within pc) which I connected to an internal aux on my sound card.(via a std cdrom internal sound lead) this works.

I also have an audio out jack on the card which I looped to the line in on the sound card.

The looped connection is better as it allows volume control from TVtime to work.:confused: (don't forget to "unmute" channels in alsamixer!)

I have tried adding "load  "v4l" to my xorg.conf and it actually removed automute from the Xawtv options???  :confused:

Automute appears to be set by default, the problem is that if the signal drops below a certain level then auto mute kicks in, however it does not mute sound but simply replacs it with a rather annoying static hiss!

However Picture seems stable and sound is good,

I really need to try to enable DVB-t as at the moment all I have is analoge channels. Anyone got any suggestions?

A real newbie question here but seeing as most of the drivers were default loaded during OS install where are the config files likley to be for loading and passing options to modules, I looked in modprobe but nothing there???

Bally

---

