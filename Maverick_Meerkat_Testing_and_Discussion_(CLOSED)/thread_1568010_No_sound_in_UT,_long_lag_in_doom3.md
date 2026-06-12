---
title: "No sound in UT, long lag in doom3"
date: 2010-09-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by The Cog on 2010-09-04
I just installed 10.10 beta. Sound is fine in most apps, but there is no sound at all in Unreal Tournament, and the sound in doom3 is very delayed - around 10 second lag.

Anyone else seeing this, or know of a fix?

---

### Post by rajeev1204 on 2010-09-04
> **The Cog said:**
> I just installed 10.10 beta. Sound is fine in most apps, but there is no sound at all in Unreal Tournament, and the sound in doom3 is very delayed - around 10 second lag.

Anyone else seeing this, or know of a fix?


There is a bug for this also in lucid actually 

[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/577727](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/577727)

For id software games , just use OSS instead of ALSA and it will work fine .

When running the game  add this line , for example :
```
quake4 +set s_driver oss
```

Mind the spaces .

---

### Post by The Cog on 2010-09-05
Thanks for the response, Rajeev. 

Killing pulseaudio and using ~/.pulse/client.conf to prevent respawn got doom3 working (it was still configured for using alsa though). 

I didn't manage to get any sound in Unreal Tournament though. It doesn't seem to have any sound driver configuration but a README says it needs OSS.

The odd thing is that both of these games worked perfectly in every version since Feisty until now.

---

