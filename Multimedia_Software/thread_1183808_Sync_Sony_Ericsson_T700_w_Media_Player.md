---
title: "Sync Sony Ericsson T700 w/ Media Player"
date: 2009-06-10
forum: Multimedia Software
---

### Post by maverick340 on 2009-06-10
With the [recent mess]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/318939") surrounding Mass Storage Device i hoped that recent updates in 9.04 will sort it all out. When i connected my sony ericsson t700 phone today , i was able to import all my images without having to add the two files to udev/rules.d/ folder. However it was still buggy on nautilus. I coped the two files > 1. /etc/rules.d/40-permissions.rules
2. /etc/rules.d/60-persistent-storage.rules
After that f-spot and nautilus mount both worked well. However Rhythmbox nor banshee is able to detect it as a mass storage device. Thus i am not able to add/view any music to it.

---

