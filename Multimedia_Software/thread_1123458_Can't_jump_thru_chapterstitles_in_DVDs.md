---
title: "Can't jump thru chapters/titles in DVDs"
date: 2009-04-12
forum: Multimedia Software
---

### Post by Extreedoc on 2009-04-12
Ubuntu 8.10, Totem movie player.

The title sums it up, I can't fast forward/jump chapters or titles in DVDs, otherwise it works fine. Same problem with home cooked DVDs and commercial ones. In Windows it works fine so I reckon it must be a software/driver issue.
I can't see anything in the Howto which relates to this specific problem; what do I need to install?

---

### Post by Keith Hedger on 2009-04-12
Try using gxine, I never got totem to navigate DVD's properly

---

### Post by Extreedoc on 2009-04-12
> **Keith Hedger said:**
> Try using gxine, I never got totem to navigate DVD's properly

gxine is good then? I looked in the synaptic at it, should I just install the program gxine and not any of the others with similar names? I see also that there is a Totem-xine which appears to be Totem and gxine combined, what about that?

---

### Post by Keith Hedger on 2009-04-12
The advantages to a package system like apt is that you can install different packages and if they dont work just uninstall them.

I tried a number of different packages to play DVD's with proper navigation of the menus and as I said gxine worked best for me, so yes you can just try installing the gxine package or you can install as many video players as are in the repos, then just get rid of the ones you don't like.
Thats all part of the fun!

---

### Post by Extreedoc on 2009-04-12
Hmm, so I can install several and try them out and no need to uninstall the others first? I will be offered the choices of which app to use when I put a DVD in the machine?

---

### Post by soltanis on 2009-04-12
Use VLC.

```

sudo apt-get install vlc

```

It is your #1 multimedia app on Linux, supports just about every format (DVDs included) with high quality.

---

### Post by Keith Hedger on 2009-04-12
> **Extreedoc said:**
> Hmm, so I can install several and try them out and no need to uninstall the others first? I will be offered the choices of which app to use when I put a DVD in the machine?

you can set the default action to take when a dvd is inserted in nautilus, or you can right click on a mounted dvd/cd and select what to open it with.

---

### Post by Extreedoc on 2009-04-13
> **Keith Hedger said:**
> you can set the default action to take when a dvd is inserted in nautilus, or you can right click on a mounted dvd/cd and select what to open it with.

Thanks Keith, that is really helpful and thanks also Soltanis, I have looked at VLC and think I will try it first as I have heard quite a lot about it.
John

An update: I have installed VLC and it is working, just one small criticism: the audio is slightly choppy, occasional breaks in the audio stream. Is there some way I can improve on this?

---

