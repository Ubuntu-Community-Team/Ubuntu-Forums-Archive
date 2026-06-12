---
title: "Q3 Delayed + stopping sound"
date: 2010-11-26
forum: Multimedia Software
---

### Post by rzeka on 2010-11-26
Hello.

I've decided to come back from Debian to Ubuntu. Almost everything works... Almost, because after night of fights finally I forced Quake 3 to play sounds.

Unfortunately, the sound is delayed and stops each 3-4 seconds for a while.

[Sound stopping example]("http://servers.freezetag.eu/q3.mp3")

Before the game starts, I disable compiz
```
killall compiz
```

I run the game like that:
```
esddsp --mmap ./quake3.x86 $@
```

I've tried to disable pulseaudio before start. It failed too...
```
sudo killall pulseaudio
```

Any ideas, solutions?

P.S.
Q3 uses OSS (it's trying to access /dev/dsp)

---

