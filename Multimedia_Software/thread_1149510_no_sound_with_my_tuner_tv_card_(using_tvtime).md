---
title: "no sound with my tuner tv card (using tvtime)"
date: 2009-05-05
forum: Multimedia Software
---

### Post by befalimpertinent on 2009-05-05
Hello,
I use Kubuntu 9.04 and I don't get sound from my tuner Tv Hauppauge wintv express. It's a Pci card with an external jack link to the input line of my sound card.
To make some test for now I just plug directlymy speakers to the output of the Tuner card. On Alsa mixer, all chanels are enable and set to maximum volume.
All work fine on Xp and worked well with my previous 8.04 version.

I 've got an image on tvtime since I had into /etc/modprobe.d/bttv
```
options bttv radio=0 card=34 tuner=24 gbuffers=8
```and the line 

```
bttv 
``` into /etc/modules


----------------------
More details, Here some output :
```
[INDENT]dmesg | grep bt
[   17.321831] bt87x0: Using board 1, analog, digital (rate 32000 Hz)
[   17.453744] bttv: driver version 0.9.17 loaded
[   17.453747] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   17.453814] bttv: Bt8xx card found (0).
[   17.453826] bttv 0000:05:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   17.453835] bttv0: Bt878 (rev 17) at 0000:05:01.0, irq: 22, latency: 64, mmio: 0xdfefe000
[   17.453870] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[   17.453872] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,insmod option]
[   17.453897] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[   17.453958] bttv0: tuner type=24
[   17.453960] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   17.456610] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   17.458935] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   17.490187] tuner' 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   17.573081] bttv0: registered device video0
[   17.573102] bttv0: registered device vbi0
[   17.573124] bttv0: registered device radio0
[   17.573144] bttv0: PLL: 28636363 => 35468950 .. ok
[   17.604745] input: bttv IR (card=34) as /devices/pci0000:00/0000:00:1e.0/0000:05:01.0/input/input6
[/INDENT]
``````
[INDENT]lsmod | grep bt
bttv                  171924  0
videodev               41600  2 tuner,bttv
ir_common              52228  1 bttv
compat_ioctl32          9344  1 bttv
i2c_algo_bit           14084  1 bttv
snd_bt87x              21028  2
v4l2_common            20992  2 tuner,bttv
videobuf_dma_sg        20484  1 bttv
snd_pcm                82948  3 snd_hda_intel,snd_bt87x,snd_pcm_oss
videobuf_core          26500  2 bttv,videobuf_dma_sg
btcx_risc              13064  1 bttv
snd                    62628  20 snd_hda_intel,snd_seq_oss,snd_rawmidi,snd_seq,snd_bt87x,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
tveeprom               20100  1 bttv
snd_page_alloc         16904  3 snd_hda_intel,snd_bt87x,snd_pcm
[/INDENT]
```Thanks for your help ! [IMG]http://forum.ubuntu-fr.org/img/smilies/hmm.png[/IMG]

---

### Post by befalimpertinent on 2009-05-07
OMHO, cause when I use directly the TV card audio output I heard nothing (no noise), I think that only the video module was loaded and the audio module is missing.
Is there something wrong with this line into my /etc/modprobe.d/bttv

options bttv radio=0 card=34 tuner=24 gbuffers=8Someone can tell me how to be sure of these values ?

Something else, 
```
befa@befa-desktop:~$ lspci | grep Bt
05:01.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
05:01.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

```
that seems showing that both audio and video parts are well detected. The only thing to do seems to load audio module. Using btaudio ?

---

### Post by bizhat on 2009-06-01
Have you find any solution for the problem ? I too have no sound in tvtime for pinnacle pctv 100i internal pci card.

---

