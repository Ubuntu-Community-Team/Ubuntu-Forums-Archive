---
title: "Sound Problem With Toshiba Notebook"
date: 2008-04-20
forum: Multimedia &amp; Video
---

### Post by LightFighter on 2008-04-20
Hey^^

I got a Toshiba Satego P100-10F ([http://de.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/productPage.do?service=DE&PRODUCT_ID=126480&toshibaShop=false](http://de.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/productPage.do?service=DE&PRODUCT_ID=126480&toshibaShop=false))
I installed Ubuntu Ultimate 7.10 and everything's working fine so far
except for the sound card (Conexant)
I know from my Windows times that the soundcard is strongly connected with the modem -  maybe this is important for you

I just cant get any sound out of this notebook and I'd really appreciate it, if you can help me

some informations:
```
timo@NBTIMO:~$ cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.14 emulation code)
Kernel: Linux NBTIMO 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
HDA Intel at 0xd2400000 irq 22

Audio devices:
0: CONEXANT Analog (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers:
0: Conexant CX20549 (Venice)

```

---

### Post by wolfen69 on 2008-04-20
your sound card is an Intel HDA (high definition audio)
see this: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by LightFighter on 2008-04-21
thanks for you quick response :)

i read through the link but non of those instructions helped :/
still no sound
I think the problem is, that I cant find my soundcard in the ALSA-Configuration.txt
any other solutions?

---

