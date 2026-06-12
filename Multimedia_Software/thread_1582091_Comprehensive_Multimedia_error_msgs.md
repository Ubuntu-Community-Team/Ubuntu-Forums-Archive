---
title: "Comprehensive Multimedia error msgs"
date: 2010-09-26
forum: Multimedia Software
---

### Post by borderblu on 2010-09-26
Hi,

Running 8.04 studio 64bit, it is a fresh install b/c lynx studio ubu was freezing my system, rendering it totally inoperable.

Anyways, following the Comprehensive Multimedia & Video Howto sticky for 64bit 8.04 users - (it's the guide at the top of the page)

[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

I wind up with this error after trying the long non-free codecs apt-get:

```
The following packages have unmet dependencies:
  icedtea-gcjwebplugin: Depends: openjdk-6-jre (>= 6b06) but it is not going to be installed
E: Broken packages

```

Any help or suggestions much appreciated, thanx dudes!!

---

### Post by elliotn on 2010-09-26
sudo  apt-get install -f

or go to snaptic parkage manager and fix it from there

---

### Post by borderblu on 2010-09-26
Thx for your reply. Unfortunately, the `apt-get install -f' option didn't work.

Is there a synaptic guide so I know what all I need to get all the various codecs up and running? I've never used it before.

---

