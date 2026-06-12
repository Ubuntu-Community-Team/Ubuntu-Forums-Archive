---
title: "Hauppuage WinTV HVR1110 (not hvr-1100 owners) owners please read!"
date: 2008-09-29
forum: Mythbuntu
---

### Post by db260179 on 2008-09-29
My patch has been accepted into the linux-dvb list

[http://linuxtv.org/hg/v4l-dvb/rev/40d58d92d183bfe13ab7834434ea438a4fb20813](http://linuxtv.org/hg/v4l-dvb/rev/40d58d92d183bfe13ab7834434ea438a4fb20813)

If you are a owner of this card and have found the following not working:-

1.When plugging in a 3.5 stereo lead in the LINE IN socket, and selecting S-video or Composite to record from, no sound will be heard, even after a 'sox redirect'.

2.Tuning the Analog TV will produce no results.

3.Radio feature - no radio stations and sound.

Just on a side note, i'm doing a patch for the Avermedia Super 007 remote support. (I have a working patch, if any avermedia owners wish to test it!)

:guitar:

---

### Post by sandman652001 on 2008-10-12
How do I use your pach?
Thanks for the help

---

### Post by db260179 on 2008-10-12
Install the latest v4l-dvb, this overwrite your current kernel drivers.

[http://www.linuxtv.org](http://www.linuxtv.org)

> **sandman652001 said:**
> How do I use your pach?
Thanks for the help

---

### Post by iborg1013 on 2008-10-22
For first time I can tune and listen FM radio with my HVR-1110 in Ubuntu Intrepid after compile the new drivers. 

THANK YOU VERY MUNCH !!!!

---

### Post by db260179 on 2008-10-23
My pleasure,

This was bugging me so much! so i decided to fix it myself.

Glad i could help?

> **iborg1013 said:**
> For first time I can tune and listen FM radio with my HVR-1110 in Ubuntu Intrepid after compile the new drivers. 

THANK YOU VERY MUNCH !!!!

---

### Post by sauron_jr on 2008-11-04
Sorry, i'm a bit new to installing thing in linux, how and what i have to install from the site you spoke.

Thank you a lot

---

### Post by iborg1013 on 2008-11-04
> **sauron_jr said:**
> Sorry, i'm a bit new to installing thing in linux, how and what i have to install from the site you spoke.

Thank you a lot

Try this:
```

sudo apt-get install mercurial  linux-headers-$(uname -r) build-essential dvb-utils
hg clone http://linuxtv.org/hg/v4l-dvb
cd v4l-dvb
make
sudo make install

```
and reboot

---

### Post by iborg1013 on 2008-11-05
After install the new drivers (or with the kernel ones) I cant make the remote work. 
```

$ cat /proc/bus/input/devices 

I: Bus=0018 Vendor=0000 Product=0000 Version=0000
N: Name="HVR 1110"
P: Phys=i2c-0/0-0071/ir0
S: Sysfs=/devices/virtual/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=100003
B: KEY=100fc312 214a80200000000 0 18000 41a800004801 9e168000000000 10000ffc

```

Then I've install lirc 
```

$ sudo apt-get install lirc 
$ cat /etc/lirc/hardware.conf

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Linux input layer (/dev/input/eventX)"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event5"
REMOTE_LIRCD_CONF="generic/devinput.conf"
REMOTE_LIRCD_ARGS=""

```
but when I try irrecord 
```

sudo irrecord -H dev/input -d /dev/input/event5 hvr1110.conf

```
I press a button but i only got the error
```

irrecord: gap not found, can't continue
irrecord: closing '/dev/input/event5'

```

---

### Post by megamania on 2008-11-07
> **db260179 said:**
> 1.When plugging in a 3.5 stereo lead in the LINE IN socket, and selecting S-video or Composite to record from, no sound will be heard, even after a 'sox redirect'.
2.Tuning the Analog TV will produce no results.
3.Radio feature - no radio stations and sound.


Thank you! You helped me solve my major complaint about the Hauppauge HVR 1110, the "no audio with composite" problem.

However, I still have no audio when trying to listen to the radio with mplayer (mplayer radio://100.0). Is there something else I need to do in order to get it to work?

---

### Post by iborg1013 on 2008-11-07
> 
However, I still have no audio when trying to listen to the radio with mplayer (mplayer radio://100.0). Is there something else I need to do in order to get it to work?

Radio works for me using gnomeradio after redirect analog sound with sox  
```

sox -c 1 -t alsa hw:1,0 -t alsa default

```

What about IR remote? Can you make it work?

---

### Post by megamania on 2008-11-07
> **iborg1013 said:**
> Radio works for me using gnomeradio after redirect analog sound with sox  
Thanks - fixed! It works now (I had messed up sound redirection).

> **iborg1013 said:**
> 
What about IR remote? Can you make it work?
I have never tried it, sorry. I'll give it a try one of these days.

And do you know how to record analog tv easily. I tried a few scripts using mencoder, but I come up with no sound. I'm looking for a simple program allowing me to use timeshift with both analog and digital tv...

---

### Post by alexef on 2008-12-16
> **db260179 said:**
> 
Just on a side note, i'm doing a patch for the Avermedia Super 007 remote support. (I have a working patch, if any avermedia owners wish to test it!)


Hi, I have a Super 007 card, can you please give me the patch so I can test it?

Thanks

---

### Post by db260179 on 2009-03-12
You need to modify this for the ubuntu intrepid kernel. Just a case of modifying the lines to fit the intrepid kernel source code

Some mapped keys dont work as they should, only a couple though.

> **alexef said:**
> Hi, I have a Super 007 card, can you please give me the patch so I can test it?

Thanks

---

### Post by zoutmax on 2009-04-29
> **iborg1013 said:**
> Radio works for me using gnomeradio after redirect analog sound with sox  
```

sox -c 1 -t alsa hw:1,0 -t alsa default

```

What about IR remote? Can you make it work?

Hi,

I got the sound with sox too but too much latency,
I am posting here because desperate to make working my :

```
Hauppauge WinTV-HVR1110 DVB-T/Hybrid
```

From lspci output :

```
Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
```

I am running [COLOR="Red"]Ubuntu 9.0.4 jaunty[/COLOR]:

```
Ubuntu 9.0.4 Linux 2.6.28-11-generic
```

I tried with the build in drivers from the [COLOR="Red"]Ubuntu 9.0.4[/COLOR] install disk,
and with the drivers that i compiled from [COLOR="Red"]Linux TV org (V4L-DVB)[/COLOR].

Both give me the same result : [COLOR="Red"]No TV or radio tuner sound output[/COLOR]

The sound is working fine on this system only this TV card does not produce any...

I checked the volume parameters tried with different sound servers (alsa, oss, etc..) no results.

I assume that the sound card i am using is OK, details from lspci :

```
Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 02)
```

Working on the TV card [COLOR="Red"]tested with TV Time and K Radio[/COLOR] :

Video (the video output is ok, i can watch TV on the different channels)
Video Channel Seeking (the card detect all my TV channels but no sound)
Radio Channel Seeking (the card detect all my Radio channels but no sound)
Remote Control Lirc (Infrared remote control [COLOR="Red"]plugged in the TV card[/COLOR] working fine)

The only problem is that i can't get any sound output from this TV card, i checked the modules :

```
lsmod
Module                  Size  Used by
binfmt_misc            16776  1
radeon                342816  2
drm                    96296  3 radeon
bridge                 56340  0
stp                    10500  1 bridge
bnep                   20224  2
ivtv                  150436  0
i2c_algo_bit           14084  1 ivtv
cx2341x                22020  1 ivtv
lirc_dev               19892  0
input_polldev          11912  0
video                  25360  0
output                 11008  1 video
lp                     17156  0
tda1004x               24068  1
saa7134_dvb            30476  0
videobuf_dvb           15108  1 saa7134_dvb
dvb_core               93312  1 videobuf_dvb
saa7134_alsa           20000  0
ir_kbd_i2c             16272  0
tda827x                18052  2
ppdev                  15620  0
snd_intel8x0           37532  3
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  4 saa7134_alsa,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
tda8290                21000  1
snd_seq_dummy          10756  0
snd_seq_oss            37760  0
tuner                  30984  1
snd_seq_midi           14336  0
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
saa7134               160716  2 saa7134_dvb,saa7134_alsa
ir_common              56068  2 ir_kbd_i2c,saa7134
v4l2_common            23808  4 ivtv,cx2341x,tuner,saa7134
snd                    62628  17 
saa7134_alsa,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_
device
videodev               44832  4 ivtv,tuner,saa7134,v4l2_common
v4l1_compat            21764  1 videodev
iTCO_wdt               19108  0
iTCO_vendor_support    11652  1 iTCO_wdt
psmouse                61972  0
videobuf_dma_sg        20484  3 saa7134_dvb,saa7134_alsa,saa7134
pcspkr                 10496  0
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
serio_raw              13316  0
intel_agp              34108  1
videobuf_core          26244  3 videobuf_dvb,saa7134,videobuf_dma_sg
tveeprom               20228  2 ivtv,saa7134
agpgart                42696  2 drm,intel_agp
shpchp                 40212  0
parport_pc             40100  1
parport                42220  3 lp,ppdev,parport_pc
usbhid                 42336  0
3c59x                  49192  0
mii                    13312  1 3c59x
floppy                 64324  0
fbcon                  46112  0
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
```



They look loaded,then i tried to reroute the sound to alsa by using sox:

```
sox -q -c 2 -s -r 32000 -t alsa hw:1 -t alsa -r 32000 hw:0
```

[COLOR="Red"]This is the only way i can get the sound but it implicate starting sox every time i want to use TV or Radio...........[/COLOR]

The /var/messages does not show any problems :

```

Apr 29 00:53:27 Ubuntu kernel: [   13.200361] Linux video capture interface: v2.00
Apr 29 00:53:27 Ubuntu kernel: [   13.446769] saa7130/34: v4l2 driver version 0.2.15 loaded
Apr 29 00:53:27 Ubuntu kernel: [   13.447106] saa7134 0000:02:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr 29 00:53:27 Ubuntu kernel: [   13.447119] saa7133[0]: found at 0000:02:09.0, rev: 209, irq: 17, latency: 66, mmio: 0x40000000
Apr 29 00:53:27 Ubuntu kernel: [   13.447133] saa7133[0]: subsystem: 0070:6701, board: Hauppauge WinTV-HVR1110 DVB-T/Hybrid [card=104,autodetected]
Apr 29 00:53:27 Ubuntu kernel: [   13.447248] saa7133[0]: board init: gpio is 6400000
Apr 29 00:53:27 Ubuntu kernel: [   13.605809] saa7133[0]: i2c eeprom 00: 70 00 01 67 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
Apr 29 00:53:27 Ubuntu kernel: [   13.605832] saa7133[0]: i2c eeprom 10: ff ff ff 0e ff 20 ff ff ff ff ff ff ff ff ff ff
Apr 29 00:53:27 Ubuntu kernel: [   13.605851] saa7133[0]: i2c eeprom 20: 01 40 01 32 32 01 01 33 88 ff 00 aa ff ff ff ff
Apr 29 00:53:27 Ubuntu kernel: [   13.605871] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Apr 29 00:53:27 Ubuntu kernel: [   13.605889] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 03 32 15 60 ff ff ff ff ff ff
Apr 29 00:53:27 Ubuntu kernel: [   13.605908] saa7133[0]: i2c eeprom 50: ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Apr 29 00:53:27 Ubuntu kernel: [   13.605927] saa7133[0]: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Apr 29 00:53:27 Ubuntu kernel: [   13.605945] saa7133[0]: i2c eeprom 70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Apr 29 00:53:27 Ubuntu kernel: [   13.605963] saa7133[0]: i2c eeprom 80: 84 09 00 04 20 77 00 40 e0 f1 4f f0 73 05 29 00
Apr 29 00:53:27 Ubuntu kernel: [   13.605983] saa7133[0]: i2c eeprom 90: 84 08 00 06 cb 05 01 00 94 48 89 72 07 70 73 09
Apr 29 00:53:27 Ubuntu kernel: [   13.606002] saa7133[0]: i2c eeprom a0: 23 5f 73 0a fc 72 72 0b 2f 72 0e 01 72 0f 03 72
Apr 29 00:53:27 Ubuntu kernel: [   13.606021] saa7133[0]: i2c eeprom b0: 10 01 72 11 ff 79 1e 00 00 00 00 00 00 00 00 00
Apr 29 00:53:27 Ubuntu kernel: [   13.606040] saa7133[0]: i2c eeprom c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Apr 29 00:53:27 Ubuntu kernel: [   13.606058] saa7133[0]: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Apr 29 00:53:27 Ubuntu kernel: [   13.606076] saa7133[0]: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Apr 29 00:53:27 Ubuntu kernel: [   13.606095] saa7133[0]: i2c eeprom f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Apr 29 00:53:27 Ubuntu kernel: [   13.606123] tveeprom 0-0050: Hauppauge model 67019, rev B4B4, serial# 5239264
Apr 29 00:53:27 Ubuntu kernel: [   13.606131] tveeprom 0-0050: MAC address is 00-0D-FE-4F-F1-E0
Apr 29 00:53:27 Ubuntu kernel: [   13.606137] tveeprom 0-0050: tuner model is Philips 8275A (idx 114, type 4)
Apr 29 00:53:27 Ubuntu kernel: [   13.606145] tveeprom 0-0050: TV standards PAL(B/G) NTSC(M) PAL(I) SECAM(L/L') PAL(D/D1/K)ATSC/DVB Digital (eeprom 0xfc)
Apr 29 00:53:27 Ubuntu kernel: [   13.606152] tveeprom 0-0050: audio processor is SAA7131 (idx 41)
Apr 29 00:53:27 Ubuntu kernel: [   13.606159] tveeprom 0-0050: decoder processor is SAA7131 (idx 35)
Apr 29 00:53:27 Ubuntu kernel: [   13.606164] tveeprom 0-0050: has radio, has IR receiver, has IR transmitter
Apr 29 00:53:27 Ubuntu kernel: [   13.606170] saa7133[0]: hauppauge eeprom: model=67019
Apr 29 00:53:27 Ubuntu kernel: [   13.885196] tuner 0-004b: chip found @ 0x96 (saa7133[0])
Apr 29 00:53:27 Ubuntu kernel: [   13.964088] tda829x 0-004b: setting tuner address to 61
Apr 29 00:53:27 Ubuntu kernel: [   14.022981] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr 29 00:53:27 Ubuntu kernel: [   14.045005] ppdev: user-space parallel port driver
Apr 29 00:53:27 Ubuntu kernel: [   14.096084] tda829x 0-004b: type set to tda8290+75a
Apr 29 00:53:27 Ubuntu kernel: [   14.644024] intel8x0_measure_ac97_clock: measured 55969 usecs
Apr 29 00:53:27 Ubuntu kernel: [   14.644033] intel8x0: clocking to 41146
Apr 29 00:53:27 Ubuntu kernel: [   17.988392] input: HVR 1110 as /devices/virtual/input/input6
Apr 29 00:53:27 Ubuntu kernel: [   17.994320] ir-kbd-i2c: HVR 1110 detected at i2c-0/0-0071/ir0 [saa7133[0]]
Apr 29 00:53:27 Ubuntu kernel: [   18.056323] saa7133[0]: registered device video0 [v4l2]
Apr 29 00:53:27 Ubuntu kernel: [   18.056442] saa7133[0]: registered device vbi0
Apr 29 00:53:27 Ubuntu kernel: [   18.056560] saa7133[0]: registered device radio0
Apr 29 00:53:27 Ubuntu kernel: [   18.086624] saa7134 ALSA driver for DMA sound loaded
Apr 29 00:53:27 Ubuntu kernel: [   18.086695] saa7133[0]/alsa: saa7133[0] at 0x40000000 irq 17 registered as card -2
Apr 29 00:53:27 Ubuntu kernel: [   18.214944] dvb_init() allocating 1 frontend
Apr 29 00:53:27 Ubuntu kernel: [   18.256592] DVB: registering new adapter (saa7133[0])
Apr 29 00:53:27 Ubuntu kernel: [   18.256610] DVB: registering adapter 0 frontend -858993460 (Philips TDA10046H DVB-T)...
Apr 29 00:53:27 Ubuntu kernel: [   18.331451] tda1004x: setting up plls for 48MHz sampling clock
Apr 29 00:53:27 Ubuntu kernel: [   18.497660] lp0: using parport0 (interrupt-driven).
Apr 29 00:53:27 Ubuntu kernel: [   18.621371] tda1004x: found firmware revision 20 -- ok
Apr 29 00:53:28 Ubuntu kernel: [   24.071387] lirc_dev: IR Remote Control driver registered, major 61 
Apr 29 00:53:28 Ubuntu kernel: [   24.183952] ivtv: Start initialization, version 1.4.1
Apr 29 00:53:28 Ubuntu kernel: [   24.186600] ivtv: End initialization

```


Everything look fine to me but no TV / Radio sound output without using sox.

The Card is not broken because this system has dual boot and when i run windows everything is fine :O)

[COLOR="Lime"][B]I believe that the drivers are not able to route the sound from the pci port to the Alsa server.
[/B][/COLOR]
This TV card does not have any jack sound output, no wire possible between TV card and sound card, sound goes over PCI no choice,which make a latency when using sox with Linux or under Windows i still have the sound not properly synchronized (really minimal but noticeable if you pay attention).

The Wire (Double jack 3.5) connection between TV sound out and the sound card Line In was a better concept as this work fine on my other Pinnacle TV Tuner with no latency but just fine...

Please doe anyone has any idea for get the TV sound from my HVR1110 over pci without using any service like sox ? (not working, big latency)

or maybe working HVR1110 drivers on Ubuntu 9.0.4, or a "wire Patch" who send the TV pci sound output to the sound server will help me...

Thx

---

### Post by megamania on 2009-04-30
> **zoutmax said:**
> I am posting here because desperate to make working my :
...
Everything look fine to me but no TV / Radio sound output without using sox.

The Card is not broken because this system has dual boot and when i run windows everything is fine :O)
...
Please doe anyone has any idea for get the TV sound from my HVR1110 over pci without using any service like sox ? (not working, big latency)

This is a known problem with no solution I'm aware of.

You can get direct audio (i.e. no sox) by using Mplayer/Mencoder (radio, analog tv, digital tv) or Kaffeine (digital TV).

---

