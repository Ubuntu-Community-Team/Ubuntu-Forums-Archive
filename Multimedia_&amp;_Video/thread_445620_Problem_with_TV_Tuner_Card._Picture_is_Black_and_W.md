---
title: "Problem with TV Tuner Card. Picture is Black and White."
date: 2007-05-16
forum: Multimedia &amp; Video
---

### Post by chris.hand on 2007-05-16
Hey, I am fairly new to Ubuntu and all has gone well for me so far. But recently I found an old tv tuner card and stuck it in my pc to see if I could record a little TV.  

Anyway, I live in New Zealand and we don't have the luxury of cable, so I am recording TV through RCA plugs. My problem is basically I get a black and white picture.

I am using the following setup: 

Prolink Pixelview PlayTV tuner
Asus a7v400-mx	motherboard with on-board VIA/S3G KM400A Graphics

Using "lsmod | grep via" I get this:

```

via                    44160  2 
drm                    81044  3 via
snd_via82xx            29208  1 
snd_ac97_codec         98336  1 snd_via82xx
snd_pcm                79876  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10888  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9472  1 snd_via82xx
gameport               16520  2 snd_via82xx,analog
via_ircc               27540  0 
irda                  201276  1 via_ircc
snd                    54020  13 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
via_agp                11264  1 
i2c_viapro             10132  0 
agpgart                35400  2 drm,via_agp
i2c_core               22784  5 i2c_ec,i2c_viapro,bttv,i2c_algo_bit,tveeprom
via82cxxx              10372  0 [permanent]
via_rhine              25608  0 
mii                     6528  1 via_rhine


```

I'm guessing that it might be because I'm not using S-Video connectors, but just want to get a second opinion before I go buy yet another cable. 

Thanks in advance for any help. Please let me know if you need any more information etc and keep in mind I'm fairly new to Linux thing! :KS

---

### Post by Dekunuts on 2007-05-16
I used to have black and white image from my tv card, but that was because ubuntu thought it was a slightly different one. I changed the settings to the correct one and the picture was ok from then on. So maybe you also have a slightly different version configured.

---

### Post by chris.hand on 2007-05-17
Hey,

Thanks for the reply.

I have a strange feeling I'm not actually changing the card and tuner settings. I have been reading up on the topic, and I've still got the black and white picture. Here is what "dmesg" dumped out:

```

[   19.368000] bttv: driver version 0.9.16 loaded
[   19.368000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   19.368000] bttv: Bt8xx card found (0).
[   19.368000] bttv0: Bt878 (rev 17) at 0000:00:08.0, irq: 16, latency: 32, mmio: 0xea000000
[   19.368000] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   19.368000] bttv0: gpio: en=00000000, out=00000000 in=00ffc0ff [init]
[   19.372000] tveeprom 1-0050: Huh, no eeprom present (err=-121)?
[   19.372000] bttv0: using tuner=-1
[   19.372000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   19.372000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   19.372000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   19.372000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   19.372000] bttv0: registered device video0
[   19.372000] bttv0: registered device vbi0

```

How do I go about changing the tuner and card? I am using the instructions on link below at the moment, but from the first command, i get an error as follows:

```

ubuntu@ubuntu:~$ rmmod bttv
ERROR: Module bttv is in use by bt878

```

Here is the page.
[http://www.mythtv.org/wiki/index.php/Bttv](http://www.mythtv.org/wiki/index.php/Bttv)

I am probably doing something wrong, Please help me. Any links, information would be greatly appreciated.

Cheers,
Chris.

---

### Post by Dekunuts on 2007-05-17
I can tel you the following :

Now, read the following with great attention so you know what I mean.

1. dmesg | grep bttv will give you information on your tv card
2. sudo gedit /etc/modules  -> 'bttv' should be in there, if not, add it to the end of the file
3. according to [http://www.linuxtv.org/v4lwiki/index.php/Cardlist.BTTV](http://www.linuxtv.org/v4lwiki/index.php/Cardlist.BTTV) your card number should be 16
4.so what you need to do is fill in this file correctly : sudo gedit /etc/modprobe.d/bttv, mine looks like this : (if it does not exist yet, it wil be created)

alias      char-major-89    i2c-dev
options    bttv             card=100 tuner=38

so the 100 should be 16 for you and since the cards are based on the same chipset i would take a 'risk' (not really a risk eh) and just copy my config (do change the 100 inot 16), save  and reboot. 

ask further questions if it doesn't help. Oh and btw i'm not an expert at all, just someone who has been trying to fix every problem he's ran into since installing ubuntu and learning a lot about computers like it.

---

### Post by chris.hand on 2007-05-17
Thanks mate for taking the time to practically spell it out for me! 

Thanks to your instructions, it finally works... in colour! I was putting the "options bttv card=100 tuner=38" in  /etc/modules file :oops:

Hopefully some time in the future I will be able to help you out with something since we are both learning. 

All the best,
Chris - I'm off to watch some "colour" TV!

---

### Post by Dekunuts on 2007-05-17
Ah, it makes me happy that I could help you.:) I try my best to help anyone I can. These forums are one of those rare places where people are still calm, forgiving, helpful,.. the least i can do is try to help. Feel free to ask me other questions anytime

---

### Post by chris.hand on 2007-05-18
Hey, I am back.

All is well and I can watch TV in colour fine, but I don't have any sound coming out of the tv tuner card. At the moment I have got around this by just plugging the decoder RCA plugs into the on board sound card line in using a rca->3.5mm adapter. This is all good for watching TV, but now I am thinking of recording TV as well.

Anyway, so here is what I got so far:

/etc/modprobe.d/bttv contents:

```
alias char-major-89 i2c-dev
options bttv card=16 tuner=28
```

The model of the card and tuner isn't exactly the same, but I'm guessing thats probably not the problem, here is the exact model numbers taken off the card:

[B]Tuner: TPI8PSB02P (Assumed LG brand)
Card: Prolink PixelView PV-BT878P+ (rev.9D)[/B]

Also, here is the output from "dmesg | grep bttv"

```
[   19.232000] bttv: driver version 0.9.16 loaded
[   19.232000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   19.232000] bttv: Bt8xx card found (0).
[   19.232000] bttv0: Bt878 (rev 17) at 0000:00:08.0, irq: 16, latency: 32, mmio: 0xea000000
[   19.232000] bttv0: using: Prolink Pixelview PlayTV (bt878) [card=16,insmod option]
[   19.232000] bttv0: gpio: en=00000000, out=00000000 in=00ffc0ff [init]
[   19.232000] bttv0: using tuner=28
[   19.232000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   19.232000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   19.236000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   19.408000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   19.448000] bttv0: registered device video0
[   19.448000] bttv0: registered device vbi0
[   19.448000] bttv0: PLL: 28636363 => 35468950 .. ok
```

I'm guessing the "not found" is not good. Reading around the other related post on the forum, it looks like its just a case of getting the right card. Here is the card numbers I have tried already:

[B]card=16 - Prolink Pixelview PlayTV (bt878) 
card=37 - Prolink PixelView PlayTV pro
card=50 - Prolink PV-BT878P+4E / PixelView PlayTV PAK / Lenco MXTV-9578 CP 
card=70 - Prolink Pixelview PV-BT878P+ (Rev.4C,8E)
card=72 - Prolink Pixelview PV-BT878P+9B (PlayTV Pro rev.9B FM+NICAM)
card=138 - Prolink Pixelview PV-BT878P+ (Rev.2E)
card=139 - Prolink PixelView PlayTV MPEG2 PV-M4900[/B]

Could it be the wrong tuner or something else? 

Cheers.

---

### Post by psavva on 2007-05-24
I've got MPEG2 PlayTV.

I managed to get one channel working.

Can anybody help out with this?

I set the card to 139 on modprobe.

Any help will be greatly appreciated

---

### Post by thimiouc on 2007-07-10
> **chris.hand said:**
> Hey, I am back.

All is well and I can watch TV in colour fine, but I don't have any sound coming out of the tv tuner card. At the moment I have got around this by just plugging the decoder RCA plugs into the on board sound card line in using a rca->3.5mm adapter. This is all good for watching TV, but now I am thinking of recording TV as well.

Anyway, so here is what I got so far:

/etc/modprobe.d/bttv contents:

```
alias char-major-89 i2c-dev
options bttv card=16 tuner=28
```

The model of the card and tuner isn't exactly the same, but I'm guessing thats probably not the problem, here is the exact model numbers taken off the card:

[B]Tuner: TPI8PSB02P (Assumed LG brand)
Card: Prolink PixelView PV-BT878P+ (rev.9D)[/B]

Also, here is the output from "dmesg | grep bttv"

```
[   19.232000] bttv: driver version 0.9.16 loaded
[   19.232000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   19.232000] bttv: Bt8xx card found (0).
[   19.232000] bttv0: Bt878 (rev 17) at 0000:00:08.0, irq: 16, latency: 32, mmio: 0xea000000
[   19.232000] bttv0: using: Prolink Pixelview PlayTV (bt878) [card=16,insmod option]
[   19.232000] bttv0: gpio: en=00000000, out=00000000 in=00ffc0ff [init]
[   19.232000] bttv0: using tuner=28
[   19.232000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   19.232000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   19.236000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   19.408000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   19.448000] bttv0: registered device video0
[   19.448000] bttv0: registered device vbi0
[   19.448000] bttv0: PLL: 28636363 => 35468950 .. ok
```

I'm guessing the "not found" is not good. Reading around the other related post on the forum, it looks like its just a case of getting the right card. Here is the card numbers I have tried already:

[B]card=16 - Prolink Pixelview PlayTV (bt878) 
card=37 - Prolink PixelView PlayTV pro
card=50 - Prolink PV-BT878P+4E / PixelView PlayTV PAK / Lenco MXTV-9578 CP 
card=70 - Prolink Pixelview PV-BT878P+ (Rev.4C,8E)
card=72 - Prolink Pixelview PV-BT878P+9B (PlayTV Pro rev.9B FM+NICAM)
card=138 - Prolink Pixelview PV-BT878P+ (Rev.2E)
card=139 - Prolink PixelView PlayTV MPEG2 PV-M4900[/B]

Could it be the wrong tuner or something else? 

Cheers.
Just remove the "alias char-major-89 i2c-dev" line and all should be well. That's what I did anyway ^ ^ I'm a newbie too and this post did help me configure my card.

---

### Post by pentzol on 2007-10-24
Brilliant  - thanks  it helped me - at least I can see TV now ( the antenna blew down in a storm so I thought thats why I cannot see anything)
I have a Pixelview Playtv MPeg2 pv-m4900 - I added card=139 to the bttv module.
Now just the remote left

Lourens

---

