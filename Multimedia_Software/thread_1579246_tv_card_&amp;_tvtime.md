---
title: "tv card &amp; tvtime"
date: 2010-09-21
forum: Multimedia Software
---

### Post by enemotrop on 2010-09-21
Hello.

I've got an BestBuy EasyTV analogic tv card (AKA Tview99), and it worked fine on past versions of Ubuntu, althought I had to change some values for the right modules to be load.

I've recently passed to Ubuntu 10.04, and the system detects the card correctly. This is the output of a dmesg:

> [   11.393950] bttv: driver version 0.9.18 loaded
[   11.393955] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   11.394581] bttv: Bt8xx card found (0).
[   11.394607] bttv 0000:00:0d.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   11.394619] bttv0: Bt878 (rev 2) at 0000:00:0d.0, irq: 18, latency: 64, mmio: 0xf7e00000
[   11.394641] bttv0: detected: (Askey Magic/others) TView99 CPH06x [card=38], PCI subsystem ID is 144f:3000
[   11.394644] bttv0: using: Askey CPH06X TView99 [card=38,autodetected]
[   11.394647] IRQ 18/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
[   11.394752] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   11.394889] bttv0: tuner type=1
[   11.591963] bttv0: audio absent, no audio device found!
[   11.812243] bttv0: registered device video0
[   11.812306] bttv0: registered device vbi0
[   11.812323] bttv0: PLL: 28636363 => 35468950 .. ok
[   11.847647] input: bttv IR (card=38) as /devices/pci0000:00/0000:00:0d.0/input/input6 BUT tvtime-scanner isn't able to find any signal. I've tried with

> sudo rmmod bttv 
sudo rmmod tuner
sudo modprobe bttv card=38 tuner=34
, and even tried with an script that tries with every tuner in the [list]("http://enpc3240.eas.asu.edu/lxr/linux/http/source/Documentation/video4linux/bttv/CARDLIST") , but it didn't finds any signal. The fact is that I've lost the right values and module or modules I used in the past, but I THINK the card and tuner are right (38 and 34, respectively).

This is my lsmod | grep bt output:

> bttv                  111669  0 
ir_common              38875  1 bttv
videobuf_dma_sg        10782  1 bttv
videobuf_core          16356  2 bttv,videobuf_dma_sg
btcx_risc               3624  1 bttv
tveeprom               11102  1 bttv
snd_bt87x               9735  1 
snd_pcm                70662  5 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_bt87x,snd_pcm_oss
v4l2_common            15431  5 tuner,bttv,tvaudio,tda7432,msp3400
videodev               34361  6 tuner,bttv,tvaudio,tda7432,msp3400,v4l2_common
snd                    54148  19 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_bt87x,snd_pcm_oss,snd_mpu401_uart,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            5028  2 bttv,radeon
snd_page_alloc          7076  4 snd_via82xx,snd_via82xx_modem,snd_bt87x,snd_pcmWhat I am doing wrong? Perhaps I've to use another module? I remember that the one that worked with other versions of Ubuntu needed to be configurated with the options above (card, tuner... and others optional, like remote, etc).

Thanks in advance.

---

### Post by lkjoel on 2010-09-21
> **enemotrop said:**
> Hello.

I've got an BestBuy EasyTV analogic tv card (AKA Tview99), and it worked fine on past versions of Ubuntu, althought I had to change some values for the right modules to be load.

I've recently passed to Ubuntu 10.04, and the system detects the card correctly. This is the output of a dmesg:

BUT tvtime-scanner isn't able to find any signal. I've tried with

, and even tried with an script that tries with every tuner in the [list]("http://enpc3240.eas.asu.edu/lxr/linux/http/source/Documentation/video4linux/bttv/CARDLIST") , but it didn't finds any signal. The fact is that I've lost the right values and module or modules I used in the past, but I THINK the card and tuner are right (38 and 34, respectively).

This is my lsmod | grep bt output:

What I am doing wrong? Perhaps I've to use another module? I remember that the one that worked with other versions of Ubuntu needed to be configurated with the options above (card, tuner... and others optional, like remote, etc).

Thanks in advance.
It might help for others if you do this:
Click on Edit Post.
Then click on Go Advanced.
Then scroll down to Additional Options.
Then check: Disable smilies in text.
Then click on Save Changes.

---

### Post by enemotrop on 2010-09-22
Emoticons out. Any suggestions?

TY

---

### Post by enemotrop on 2010-09-23
Solved. I made an script based in other I found at the net to test the reception of any signal passing for each tuner model, and... the right model was the 0 :P

---

