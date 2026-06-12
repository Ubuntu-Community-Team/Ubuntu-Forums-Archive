---
title: "Low sound after installing Kubuntu 14.04"
date: 2014-05-14
forum: Multimedia Software
---

### Post by baruch60610 on 2014-05-14
I just installed Kubuntu 14.04 on my Toshiba NB505.  Now the sound is very faint.  When I have it turned to max, and then use VLC to go over 100%, I barely get a decent sound.  Anything else, it's so faint as to be useless.

Does anyone know why this would happen, or better yet, how to fix it?

I will note that when I grepped the logs I found several curious entries like so:

```
dpkg.log:2014-04-16 17:34:04 status half-installed pulseaudio-utils:i386 1:4.0-0ubuntu11
```

and:

```
dpkg.log:2014-04-16 17:35:44 status half-configured pulseaudio-utils:i386 1:4.0-0ubuntu11
```


That looks intriguing, since it seems as though I'm only getting "half" the sound; but that's probably a naive interpretation.  But I don't know whether that "half-installed" is significant, or if it's always like that.

I'd sure like to figure this one out.

I forgot to mention that with Kubuntu 13.10, I had normal sound on this machine.

---

