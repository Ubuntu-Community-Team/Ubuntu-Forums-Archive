---
title: "proprietary ATI drivers drive me nuts - looking for new gfx card"
date: 2007-07-19
forum: Multimedia &amp; Video
---

### Post by therapiekind on 2007-07-19
Hi all!

First, excuse me for another thread on this topic, as it seems to be discussed quite often.

I spent a lot of time now for getting the fglrx drivers to work on my system (Radeon 9200). I wanted to use the s-video out in order to watch things on my tv and thought the proprietary drivers are the solution to this. Several how-tos and tutorials didn't work and right now I'm pretty tired of this. I got stuck at compiling the drivers, trying to build them with
```
$ module-assistant build fglrx
```

This didn't work, the log file can be found here: [http://typeofundefined.com/stuff/fglrx-kernel-source.buildlog.2.6.20-15-generic.1184848753](http://typeofundefined.com/stuff/fglrx-kernel-source.buildlog.2.6.20-15-generic.1184848753)

It's German output but it's pretty clear that there are a lot of errors. If there's still hope, let me know.

Nonetheless, I'm tired of this and am glad that my system still operates. I think about getting a new gfx card, one that will be less painful. Any recommendations on a card that provides tv functionality over s-video without much hassle? I don't care if it is Nvidia or ATI, just one that works. And it needn't be top-notch, as my system isn't as well.

Thanks in advance for every useful tip!

[edit]
Btw, I'm using xubuntu (7.04 Feisty Fawn).
[/edit]

---

### Post by dodgePT on 2007-07-19
If you're still thinking about buying a new gfx card, try nvidia because ati still sucks when it comes to linux drivers. They released a new driver, 8.39.4, but i didn't tried it yet.

Try the new driver, maybe it will work. Latelly, ATI/AMD have been releasing new drivers more often, maybe this time they're really trying to improve their proprietary drivers.

---

### Post by therapiekind on 2007-07-20
They say the latest drivers don't support the Radeon 9200 anymore. And as far as I can tell the installation process doesn't seem to differ much from what I have done so far with the "suitable" one. Which in my eyes is too much trouble.

Any advice on a specific Nvidia card? As I said, it doesn't need to be the latest bleeding edge.

---

### Post by tseliot on 2007-07-20
> **therapiekind said:**
> They say the latest drivers don't support the Radeon 9200 anymore.
That's true. The fglrx driver which supported your card is 8.28.8 but doesn't work on Feisty. You should use the open source driver instead.

> **therapiekind said:**
> Any advice on a specific Nvidia card? As I said, it doesn't need to be the latest bleeding edge.
Any card from series 5xxx, 6xxx or 7xxx should work fine with the latest driver.

---

### Post by therapiekind on 2007-07-20
> **tseliot said:**
> That's true. The fglrx driver which supported your card is 8.28.8 but doesn't work on Feisty. You should use the open source driver instead.


Any card from series 5xxx, 6xxx or 7xxx should work fine with the latest driver.

Right, building the drivers already didn't work anymore. And I read the open source drivers ain't able to support s-video and such.

Thanks for the tipps, I'll go with one of those cards you mentioned.

---

