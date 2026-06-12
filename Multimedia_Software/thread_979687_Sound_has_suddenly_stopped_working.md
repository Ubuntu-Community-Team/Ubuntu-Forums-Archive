---
title: "Sound has suddenly stopped working"
date: 2008-11-12
forum: Multimedia Software
---

### Post by Rhapsody on 2008-11-12
This is a bizarre problem that I have no explanation for.

I use a Sound Blaster X-Fi with OSS4 on Kubuntu 8.04. Recently, after having my system up and running for 15 days, I ended up rebooting. After that point, there has been no sound. ossxmix can see my X-Fi, KDE System Settings doesn't see any MIDI devices, the sound test doesn't work, but switching sound systems tends to cause a noise to come out the speakers (exactly the same sound it typically would before playing a sound), but nothing else happens.

At exactly the same time, KNetworkManager also stopped seeing my router through my ethernet cable, but strangely can see it through my wireless connection. I am currently focusing on the sound though.

This exact situation did happen once before, but leaving the system off for several hours fixed both. I have had no such luck this time around.

I have installed OSS 4.1 through Mercurial and removed my old OSS 4.0 deb package (in that order), but this seems to have made absolutely no difference to anything. I suspect the problem probably doesn't even lie with OSS as ossxmix can see my sound card just fine, it's the KDE apps that can't.

---

