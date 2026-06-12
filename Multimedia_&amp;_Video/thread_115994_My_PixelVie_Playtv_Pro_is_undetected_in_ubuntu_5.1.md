---
title: "My PixelVie Playtv Pro is undetected in ubuntu 5.10 breezy :( please help"
date: 2006-01-11
forum: Multimedia &amp; Video
---

### Post by codebox on 2006-01-11
Hi everyone, 

this is my first post here and i salute all the people who contribute in the ubuntu project.

having said that, i m new to linux and learning from a generic linux book. i m unable to get my tv tuner card working in ubuntu 5.10 breezy.

The card i m using is Pixel View Playtv Pro, it ought to be supported but the terminal gives me the following info when i run dmesg:

```
kamran@ABC:~# dmesg | grep bttv
[4294700.756000] bttv: driver version 0.9.15 loaded
[4294700.756000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[4294700.761000] bttv: Bt8xx card found (0).
[4294700.761000] bttv0: Bt878 (rev 17) at 0000:00:07.0, irq: 18, latency: 32, mmio: 0xea000000
[4294700.761000] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[4294700.761000] bttv0: gpio: en=00000000, out=00000000 in=00afc0ff [init]
[4294700.785000] tveeprom(bttv internal): Huh, no eeprom present (err=-121)?
[4294700.785000] bttv0: using tuner=-1
[4294700.785000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[4294700.787000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[4294700.789000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[4294700.792000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[4294700.811000] bttv0: registered device video0
[4294700.822000] bttv0: registered device vbi0

```

and according to the documentation, my card has card number = 37 and tuner = 5

The problem is: How do I set these things?

At some places, i read that doing "rmmod bttv" and reloading it again with proper parameters will do the job, BUT when i try removing the module bttv, it generates the following output:

```

kamran@ABC:~# rmmod bttv
ERROR: Module bttv is in use by bt878

```

the same error occurs even if i issue the above commad with sudo. furthermore, i've even tried to force the module removal with '-f' flag but no use.

I have not altered any of the configuration files yet, so all is at the same default linux configuration.

one more thing, running **lspci** gives me the results of my tv tuner card as desired i.e. it gives me the desired **Brooktree Corp. bt878...** etc.

Can anyone please help me fix this? pleaaase :)

Thanks a lot,
take care,
Kamran.

---

### Post by codebox on 2006-01-12
ok, almost got this to work.. so the above Q is solved. thanks :)

---

### Post by gitfiddler on 2006-01-13
codebox, can you give me an idea about how you (almost) solved your problem? Sharing that info here might help someone else with the same card.

---

### Post by codebox on 2006-01-14
sure :) i just followed the following link:

[http://ubuntuforums.org/showthread.php?t=114664&highlight=TV](http://ubuntuforums.org/showthread.php?t=114664&highlight=TV)

and i was able to view TV on tvtime, but only 1 channel (which was loaded in xp when i last used it on xp) with no sound. and then when i restarted the computer, all the settings got back to default i.e. no driver loaded and all goes to where i started :S. so i have given up hope of watching tv on linux for now... i'll wait when the great guys at ubuntu do some magic so we could just start our computer and all things run out of the box or atleast with little configuration and not a nightmare ;)

---

