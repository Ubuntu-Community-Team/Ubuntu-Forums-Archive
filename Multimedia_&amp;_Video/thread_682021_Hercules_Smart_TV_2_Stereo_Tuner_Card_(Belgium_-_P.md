---
title: "Hercules Smart TV 2 Stereo Tuner Card (Belgium - Pal)"
date: 2008-01-29
forum: Multimedia &amp; Video
---

### Post by Skerit on 2008-01-29
After years this card still won't work...

But don't be fooled! This *does* work, there are just SOOO many variables - finding the right ones seems impossible!

There are quite a lot of posts regarding this card and getting it to work, and not  a lot of them end well... I remember I got mine working a year and a few months ago, but on the same day I botched it again and I never was able to change the frequency on my card again!

Yes, I do believe it is some strange tuner problem (This card is number 100, and since I live in Belgium I think I must use tuner 5 or 38 - but so far, none works...)

So, could *anyone* on the internet, really ANYONE, shed some light on this matter?

---

### Post by Skerit on 2008-01-29
Sooo, anyone? *sigh*

Here's my bttv module file;

# i2c
alias char-major-89 i2c-devb
options i2c-algo-bit bit_test=1
# bttv
alias char-major-81 videodev
alias char-major-81-0 bttv
# Askey TV Capturer
options bttv card=100 tuner=5


What are all those aliases for, anyway? Don't these differ from machine to machine?

---

### Post by Skerit on 2008-01-30
Here's my dmesg


[   49.579360] bttv: driver version 0.9.17 loaded
[   49.579367] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   49.581942] bttv: Bt8xx card found (0).
[   49.581985] bttv0: Bt878 (rev 17) at 0000:00:08.0, irq: 17, latency: 32, mmio: 0xfdfff000
[   49.582012] bttv0: using: Hercules Smart TV Stereo [card=100,insmod option]
[   49.582055] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   49.585172] bttv0: using tuner=5
[   49.585180] bttv0: i2c: checking for TDA9875 @ 0xb0... found
[   49.602371] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   49.629513] bttv0: i2c: checking for TDA9887 @ 0x86... found
[   49.665871] bttv0: registered device video0
[   49.668735] bttv0: registered device vbi0
[   49.670339] bttv0: PLL: 28636363 => 35468950 .. ok

---

### Post by Skerit on 2008-01-30
The mystery continues!

I'm convinced the Hercules Smart TV 2 Stereo card uses a Philips tuner, yet it says "LG" on the card itself! Is there another component in the device, made by LG? How strange ...

Anyhoo, I still can't get it to work on my VIA motherboard, with a regular celeron processor, so I decided to test it out on my aus P5B-E motherboard (Dual core processor, E6400 or something)

To my surprise, and quite quickly too, the card worked here!

It could not detect the card type or tuner immediately, but when I told it which card it was it also correctly loaded the tuner, and apparently it IS tuner number 5 ...

This is very strange because I have tried this tuner so many times on the other device.

On this pc, however, it worked without any "alias" bits .. But the dmesg is also a bit different, it only has 2 of those "i2c checking for TDA..." in stead of 3, like the other pc. and I can't find out what these actually do, so ...

Here's this computer's dmesg:

[   41.162387] bttv: driver version 0.9.17 loaded
[   41.162390] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   41.279623] bttv: Bt8xx card found (0).
[   41.279665] bttv0: Bt878 (rev 17) at 0000:05:01.0, irq: 22, latency: 64, mmio: 0xdfefe000
[   41.279673] bttv0: using: Hercules Smart TV Stereo [card=100,insmod option]
[   41.279697] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   41.280552] bttv0: tuner type=5
[   41.280555] bttv0: i2c: checking for TDA9875 @ 0xb0... found
[   41.301363] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   41.390601] bttv0: registered device video0
[   41.390615] bttv0: registered device vbi0
[   41.392629] bttv0: PLL: 28636363 => 35468950 .. ok
[  175.851517] bttv0: PLL can sleep, using XTAL (28636363).
[  189.875336] bttv0: PLL: 28636363 => 35468950 .. ok

---

