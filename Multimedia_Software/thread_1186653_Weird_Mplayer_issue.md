---
title: "Weird Mplayer issue"
date: 2009-06-13
forum: Multimedia Software
---

### Post by PureLoneWolf on 2009-06-13
Hi all

I started using mplayer to play videos as it is very very solid.  That said, I am having an issue with it at the moment.  I can adjust the volume as much as I want, but it doesn't actually do anything.  I even muted in mplayer and nothing happened.

Has anyone experienced this?  I can use the master volume control ok obviously, but I like to use each applications controls and leave the master alone.

Cheers

---

### Post by briguy47 on 2009-06-15
I've never had that issue with Mplayer.  But since we are on the subject, I've gotta throw in a shameless plug for VLC.  It would especially rock for your purposes because it not only has isolated volume control, but it also has built in amplification up to 200%

---

### Post by PureLoneWolf on 2009-06-15
Thanks...no problem for the shameless plug, VLC has always annoyed me over my varied attempts to use it over the years.  Its track timer bar has always been hit or miss and I don't like anything with built in codecs...I want to control things myself... :D

I had the same issue in SMPlayer, but there I realised that the flag was set to use the system mixer for volume, which I then changed.  Mplayer presumably has the same flag set somewhere...I will find it :)

---

### Post by briguy47 on 2009-06-15
Have you tried this command line option?:

```
mplayer -softvol
```


Oh, and you can get the increased amplification with:

```
**mplayer** -softvol -softvol-max 200
```

---

### Post by PureLoneWolf on 2009-06-15
Superb, thanks :)

---

### Post by briguy47 on 2009-06-15
> **PureLoneWolf said:**
> Superb, thanks :)

I'm guessing that it worked?  Wootz!  :D

---

