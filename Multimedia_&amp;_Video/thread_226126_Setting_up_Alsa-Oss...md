---
title: "Setting up Alsa-Oss..?"
date: 2006-07-30
forum: Multimedia &amp; Video
---

### Post by Kalinda on 2006-07-30
Hello all!

In another thread I heard that using "aoss" (Alsa-Oss) for Firefox Flash sound would make it work properly. At one point I had it working, but I couldn't play music in AmaroK and watch Flash movies at the same time and AmaroK would start attacking me with messages about sound being in use if I tried to play music before leaving a Flash page.

But in another thread it said that I could set it up for hardware mixing. I have a Creative SBLive! 24-bit card, so I assume I have hardware mixing; but I don't know how one goes about configuring aoss.

Anyway, I installed Automatix after hearing from other people that it fixed their problem. For me it merely took Flash back to the default, where it crackles all the time and is really annoying; I changed it back to aoss but now sound doesn't work with it anymore and Flash pages crash Firefox. I think this may have something to do with Alsa-oss not getting along with the libflash-mozplugin I installed.. or whatever Automatix did.

So does anyone know how to set up aoss so I can use it like everyone says? I don't want to use artdsp because the sound won't be in sync.

Thanks!

---

### Post by adamkane on 2006-07-30
Maybe you need to install alsa-oss?

```

sudo apt-get install alsa-oss

```

---

### Post by Kalinda on 2006-07-31
Nope; I've got it installed, one of the first things I did when I installed Kubuntu.

I'm thinking removal of the libflash-mozplugin is in order, as Flash worked before I installed it.. but still no hardware mixing.

---

