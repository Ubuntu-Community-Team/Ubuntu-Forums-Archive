---
title: "No Sound"
date: 2012-12-31
forum: Multimedia Software
---

### Post by dvjunk on 2012-12-31
My system started acting up the other day and I cant seem to get my ound working. I get some static so I believe the hardware is OK. I tried several trouble guides to no avail. My alsa-info is at
[http://www.alsa-project.org/db/?f=e9fa9db02cc879007cc57fa27a3005466fb27ab9](http://www.alsa-project.org/db/?f=e9fa9db02cc879007cc57fa27a3005466fb27ab9)

Any help is greatly appreciated.

---

### Post by Luigi2012SM64DS on 2012-12-31
Not sure if this will be helpful but have you tried:
```
sudo alsa force-reload
```
?

---

### Post by dvjunk on 2012-12-31
> **Luigi2012SM64DS said:**
> Not sure if this will be helpful but have you tried:
```
sudo alsa force-reload
```
?
Thanks, but that didnt help.

---

### Post by dvjunk on 2013-01-01
I followed this guide:
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

When I ran pavucontrol and unmuted analog output under output devices I was able to get sound.
I also had to change the audio settings in MythTVFrontend to ALSA:default.
Now I think my sound is working.

---

