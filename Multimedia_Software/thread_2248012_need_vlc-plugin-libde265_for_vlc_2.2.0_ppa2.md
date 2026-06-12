---
title: "need vlc-plugin-libde265 for vlc 2.2.0 ppa2"
date: 2014-10-11
forum: Multimedia Software
---

### Post by LinuxMaster9 on 2014-10-11
Im looking for a build of vlc-plugin-libde265 built for vlc 2.2.0 ppa2 since the version in the repos only works with libvlccore7. And vlc 2.2.0 ppa2 only uses libvlccore8.

---

### Post by mc4man on 2014-10-12
where did you get vlc from?

---

### Post by LinuxMaster9 on 2014-10-12
AFAIK the ubuntu restricted extras repo. I originally installed vlc 2.1.4 but it upgraded at some point.

---

### Post by mc4man on 2014-10-12
I doubt it came from there. 
what's this show?
```
apt-cache policy vlc
```

---

### Post by LinuxMaster9 on 2014-10-13
I got it to work by forcing VLC to install with an older version but I still want to get the latest version and still have X265 HEVC decoding support.

---

### Post by mc4man on 2014-10-13
you didn't have to do that, was only trying to see what if any ppa(s) you had. vlc 2.2 & plugin  avail. [here]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media")

(- note for the future that a vlc which uses either a current ffmpeg or libav11 will have decoding built-in. Also there is no plugin for vlc 3.x so it should be removed if using 3.x
However the plugin appears to be a bit more efficient than either ffmpeg or libav

---

