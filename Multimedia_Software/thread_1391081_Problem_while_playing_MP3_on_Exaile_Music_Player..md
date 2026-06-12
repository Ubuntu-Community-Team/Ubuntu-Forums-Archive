---
title: "Problem while playing MP3 on Exaile Music Player."
date: 2010-01-26
forum: Multimedia Software
---

### Post by shanali4 on 2010-01-26
I M running Kubuntu with LXDE nd have following error when i try to play mp3 files on exaile. Plz help me.

See the screenshot plz.

---

### Post by Chris Musampa on 2010-01-26
I would try:
sudo apt-get install kubuntu-restricted-extras

if still no joy then maybe:
sudo apt-get install ubuntu-restricted-extras

---

### Post by Yellow Pasque on 2010-01-26
Exaile uses gstreamer. Install gstreamer-plugins (good, bad, ugly) and gstreamer-ffmpeg packages.

---

