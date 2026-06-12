---
title: "VLC Problem"
date: 2009-12-25
forum: Multimedia Software
---

### Post by nomko on 2009-12-25
Hi there,

I have a problem with VLC. I'm using Ubuntu9.04 now and when starting VLC it has 2 screens instead of 1. On a Dutch forum i read that this could be disabled by switching on " video embedded in interface" in the view mode option. And it was also recommended to switch on the VLC-QT option. So i did and now VLC won't start up. After a full uninstall and a new install VLC still doesn't start up. Does someone recognize this problem? Btw. the Dutch forum appears to be death, i've watch it for a few days.
Many thanks!
Nomko

---

### Post by mc4man on 2009-12-25
In terminal, this should set you back to defaults

```
vlc --reset-config --reset-plugins-cache
```

The version in 9.04 doesn't have video embedded in interface support,  if desired find a ppa for vlc 1.0.X ( 1.0.3 or 1.0.4 would be best

---

### Post by nomko on 2009-12-26
> **mc4man said:**
> In terminal, this should set you back to defaults

```
vlc --reset-config --reset-plugins-cache
```The version in 9.04 doesn't have video embedded in interface support,  if desired find a ppa for vlc 1.0.X ( 1.0.3 or 1.0.4 would be best

Thanks!!
That worjed well for me!

---

