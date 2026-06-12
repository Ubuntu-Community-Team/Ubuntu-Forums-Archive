---
title: "No audio after hardware upgrade."
date: 2017-08-30
forum: Multimedia Software
---

### Post by a_pleasant_username on 2017-08-30
I just upgraded my computer today with a Gigabyte GA-Z170X-Gaming 7, i7 7700, and 2x8GB Corsair Vengeance DDR4 RAM, and after the upgrade I no longer have sound. Can I get some assistance in this issue.

---

### Post by vasa1 on 2017-08-30
Please read [Suggestions on how to get your support questions answered as quickly as possible]("https://ubuntuforums.org/showthread.php?t=1422475")

There is also [Sound troubleshooting]("https://ubuntuforums.org/showthread.php?t=1885240") 

You can install *inxi* and then post the output of ```
inxi -Fxzc0
```

Also useful would be the outputs of the following:
```
uname -a
```
```
env | grep XDG_CURRENT_DESKTOP
```
```
echo $DESKTOP_SESSION
```
```
lsb_release -a
```
```
cat /etc/*-release
```
```
cat /var/log/installer/media-info
```
```
cat /etc/debian_version
```
```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by Yellow Pasque on 2017-08-31
The first thing I'd do is reset pulseaudio user config:
```
rm -r ~/.config/pulse*; pulseaudio -k
```

If that doesn't work, give more info:
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
That will gather most/all of the information vasa1 asked for (and much more).

---

