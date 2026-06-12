---
title: "dv8t - sound plays only through speakers"
date: 2011-08-27
forum: Multimedia Software
---

### Post by Tigera on 2011-08-27
So, I have an HP dv8t and I'm running Kubuntu 11.04.  I ran it off of the Live CD first to see if I had any problems before I installed, and I'm glad I did, because I ran into one.

The sound either plays through the speakers and the headphone jack or not at all - Ubuntu doesn't seem to want to mute just the speaker channel.  I searched the forums and found this link:

[http://www.linlap.com/wiki/hp+pavilion+dv8t+quad]("http://www.linlap.com/wiki/hp+pavilion+dv8t+quad")

Unfortunately, none of those suggestions work.  Does anyone have any ideas on how I might fix this?

---

### Post by .... on 2011-08-27
You probably just need a model keyword in /etc/modprobe.d/alsa-base.conf. Something like:
```
echo options snd-hda-intel model=hp-dv5 | sudo tee -a /etc/modprobe.d/alsa-base.conf
```
..and then restart ALSA:
```
cd /usr/sbin
sudo alsa force-reload
```

---

