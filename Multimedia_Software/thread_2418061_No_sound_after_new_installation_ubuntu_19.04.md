---
title: "No sound after new installation ubuntu 19.04"
date: 2019-04-30
forum: Multimedia Software
---

### Post by warrensinden on 2019-04-30
Good day all

I was previously running windows 10.
After flushing my bios windows crashed.
I am running ubuntu 19.04 & have managed to get everything running but don't have any sound.
I am booting from grub.
I have tried two links in trouble shooting but still no sound.
[http://alsa-project.org/db/?f=a88f671eb152ed6a837255b94a1f03984e0cfb3a](http://alsa-project.org/db/?f=a88f671eb152ed6a837255b94a1f03984e0cfb3a)
From the info in the link I see my JACK audio connection is not running
Could this be the problem?

---

### Post by similar2 on 2019-05-02
> From the info in the link I see my JACK audio connection is not running
Could this be the problem?

I don't think so, unless you explicity asked for it (starting JACK when you log in).
If that's the case, make sure you pick the correct soundcard in qjackctl.

Did you check the motherboard settings? Is your soundcard still enabled in BIOS?
Then boot your system and open a terminal (xfce4-terminal) and double-check your sound settings with the following command:

```
alsamixer
```

Run

```
man alsamixer
```

For more information.

---

