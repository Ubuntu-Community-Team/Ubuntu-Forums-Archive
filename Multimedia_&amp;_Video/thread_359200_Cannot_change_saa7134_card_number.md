---
title: "Cannot change saa7134 card number"
date: 2007-02-11
forum: Multimedia &amp; Video
---

### Post by truptrup on 2007-02-11
I have tried with edgy and feisty, i really need feisty for it to work because i need to new kernel. anyway i cant get the card number to change.

here is the commands
rmmod saa7134_alsa
rmmod saa7134
modprobe card=107  -- i have tried many different numbers but none seem to work 107 is the number for my card. it just reverts to card=0 unknown/generic after dmesg.

card is enltv-fm

i have got the tuner working but i cant change to svideo etc or use the remote without the right

---

### Post by Vox754 on 2007-02-13
Don't use Feisty if you don't know what you're doing. It is still in development.

Look at this thread [http://ubuntuforums.org/showthread.php?t=315379&highlight=ENLTV-FM](http://ubuntuforums.org/showthread.php?t=315379&highlight=ENLTV-FM)

Look at this page [http://gentoo-wiki.com/HARDWARE_saa7134](http://gentoo-wiki.com/HARDWARE_saa7134) for more info.

If your card really is ENCORE ENLTV-FM it may be "card=3 tuner=2".
You need to write this options to "/etc/modprobe.d/saa7134"
```

options saa7134 card=3 tuner=2

```

Remember to use "sudo".

---

### Post by truptrup on 2007-02-13
thanks for the quick reply but the real problem is i cant change the card number in feisty or edgy.

---

### Post by Vox754 on 2007-02-15
I that case you should try giving more info.
Motherboard, chipsets, sound card, Ubuntu version, kernel, and maybe the output of "dmesg", and "lspci".
```

dmesg | grep saa
sudo lspci -v

```

And please use "[CODE]" tags.

I just can't believe what you are saying about "not being able to change card number".

What application have you tried?
Try "xawtv", it has a bad interface but it is the only one that works for me.

---

### Post by truptrup on 2007-02-15
It was my fault i figured it out i was putting in the wrong card number i was using 107 which is the number for that card according to this place. and i guess the kernel does not support it yet. [http://www.linuxtv.org/v4lwiki/index.php/CARDLIST.saa7134]("http://www.linuxtv.org/v4lwiki/index.php/CARDLIST.saa7134"). 
It says "/usr/src/linux/Documentation/video4linux/CARDLIST.saa7134" is supposed to have cards numbers listed supported by the kernel but i cant find the file for anything in edgy or feisty.
Those numbers worked on everything but the remote unless i am doing something wrong with it in lirc. Did you get the remote working with card?

i was following the instructions on this page under "using with lirc" but i cant seem to get it working.
[http://www.linuxtv.org/v4lwiki/index.php/Remote_controllers]("http://www.linuxtv.org/v4lwiki/index.php/Remote_controllers")

---

### Post by Vox754 on 2007-02-16
[QUOTE=truptrup]It was my fault i figured it out i was putting in the **wrong card number** i was using 107 which is the number for that card according to this place. and i guess the kernel does not support it yet. [http://www.linuxtv.org/v4lwiki/index...RDLIST.saa7134](http://www.linuxtv.org/v4lwiki/index...RDLIST.saa7134).
It says "/usr/src/linux/Documentation/video4linux/CARDLIST.saa7134" is supposed to have cards numbers listed supported by the kernel but i cant find the file for anything in edgy or feisty.
[/QUOTE]
That information should apply correctly only if you follow their steps. Ubuntu versions come with their own compiled kernel and packages so information may vary.

The real card is showed by the output of "dmesg"
```

[17179584.160000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17179584.160000] saa7130[0]: found at 0000:00:08.0, rev: 1, irq: 193, latency: 32, mmio: 0xf6000000
[17179584.160000] saa7130[0]: subsystem: 1131:0000, board: **LifeView/Typhoon FlyVIDEO2000 [card=3**,insmod option]
[17179584.160000] saa7130[0]: board init: gpio is 5d31ff
[17179584.160000] saa7130[0]: there are different flyvideo cards with different tuners
[17179584.160000] saa7130[0]: out there, you might have to use the tuner=<nr> insmod
[17179584.160000] saa7130[0]: option to override the default value.
[17179584.160000] input: **saa7134 IR (LifeView/Typhoon Fl as /class/input/input3 **

```

[QUOTE=truptrup]Those numbers worked on everything but the remote unless i am doing something wrong with it in lirc. Did you get the remote working with card?[/QUOTE]

NO. I haven't tested the remote control nor the radio. Actually, I bought this cheap card only to watch coaxial TV on my PC and nothing else. I haven't even unpackaged the remote or the batteries from the box. I haven't used "lirc"; sorry, I can't help you with that.

```

sudo rmmod saa7134_alsa
sudo rmmod saa7134
sudo modprobe saa7134 card=3 tuner=2

```

Is this topic solved? If so, don't go away, keep posting and checking the forums.

---

### Post by truptrup on 2007-02-16
That problem is solved i can get the svideo part and coax working i havent tried the radio either but i really want to get that remote working

---

### Post by billstei on 2007-05-02
> **truptrup said:**
> It was my fault i figured it out i was putting in the wrong card number i was using 107 which is the number for that card according to this place. and i guess the kernel does not support it yet. [http://www.linuxtv.org/v4lwiki/index.php/CARDLIST.saa7134]("http://www.linuxtv.org/v4lwiki/index.php/CARDLIST.saa7134"). 
It says "/usr/src/linux/Documentation/video4linux/CARDLIST.saa7134" is supposed to have cards numbers listed supported by the kernel but i cant find the file for anything in edgy or feisty.
Those numbers worked on everything but the remote unless i am doing something wrong with it in lirc. Did you get the remote working with card?

i was following the instructions on this page under "using with lirc" but i cant seem to get it working.
[http://www.linuxtv.org/v4lwiki/index.php/Remote_controllers]("http://www.linuxtv.org/v4lwiki/index.php/Remote_controllers")

That web page [http://www.linuxtv.org/v4lwiki/index.php/CARDLIST.saa7134]("http://www.linuxtv.org/v4lwiki/index.php/CARDLIST.saa7134"). 
 lists card  #106 as 1131:2341, but I have that card (i.e. 1131:2341) and it has the FM radio, so 1131:2341 is supposed to be #107.  Kernel 2.6.20 in source file saa7134.h does not yet list cards above #105, so Feisty at this time does not recognize the card.  I have not checked 2.6.21.x kernel yet.

---

### Post by billstei on 2007-05-02
Just checked kernel 2.6.21.1 and it does list cards #106 (ENLTV) and #107 (ENLTV_FM) but saa7134_cards.c lines #3937-3941 have the problem I mentioned above which is that I have 1131:2341 and this is coded as SAA7134_BOARD_ENCORE_ENLTV rather than SAA7134_BOARD_ENCORE_ENLTV_FM.

---

### Post by billstei on 2007-05-03
After testing this further, card #107 does not work at all for TV or FM with my Encore ENLTV-FM, but card #106 which is supposed to be ENLTV (no FM) works with both TV and FM.  So in the end I do not need any modprobe options to make it work (meaning it auto-detected card 106), but the kernel source code is a bit green.

---

