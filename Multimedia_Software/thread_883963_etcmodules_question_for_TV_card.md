---
title: "/etc/modules question for TV card"
date: 2008-08-08
forum: Multimedia Software
---

### Post by zenkaon on 2008-08-08
Hello,

I have a TV card, I know the correct bttv modprobe options to get it running fine. However I can't seem to set this up on boot. Can soumeone please correct my mistake.

In /etc/modules I have
```

options bttv card=101 tuner=5

```

however dmesg | grep bttv gives:

```

[   64.165172] bttv: driver version 0.9.17 loaded
[   64.165185] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   64.165351] bttv: Bt8xx card found (0).
[   64.166014] bttv0: Bt878 (rev 2) at 0000:00:11.0, irq: 5, latency: 32, mmio: 0xe7000000
[   64.166172] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   64.166232] bttv0: gpio: en=00000000, out=00000000 in=00ebff80 [init]
[   64.167360] bttv0: tuner type unset
[   64.167366] bttv0: i2c: checking for MSP34xx @ 0x80... found
[   64.537892] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   64.538401] bttv0: i2c: checking for TDA7432 @ 0x8a... found
[   65.109369] bttv0: registered device video0
[   65.109406] bttv0: registered device vbi0

```

Which means that I have to set it up manually every time. with:
```

sudo rmmod bt878
sudo rmmod bttv
sudo modprobe bttv card=101 tuner=5

```


Can someone point me in the right direction please?

Cheers

---

### Post by steefjeqv on 2008-08-11
Hi,

You'll have to "blacklist" the bttv driver (in terminal) :

sudo gedit /etc/modprobe.d/blacklist

Now add the following to this file :

blacklist bttv

Save and exit.
Now your /etc/modules should load fine.

Greetings,
Steven

---

