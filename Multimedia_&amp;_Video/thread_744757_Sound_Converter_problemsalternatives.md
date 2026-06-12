---
title: "Sound Converter problems/alternatives"
date: 2008-04-03
forum: Multimedia &amp; Video
---

### Post by DocForbin on 2008-04-03
I'm using Sound Converter to transcode some flac files to mp3 for my portable. It works fine if you do one folder at a time, but if you try to do multiple folders it has an annoying habit of creating new folders for the mp3 files within each directory, rather than using the working directory like it is configured to do. For example, if the flac files are in Pink Floyd/Dark Side of the Moon/, the mp3 files will end up in Pink Floyd/Dark Side of the Moon/Dark Side of the Moon/ instead of Pink Floyd/Dark Side of the Moon/.

This only happens when converting multiple folders, or a folder that has subfolders. It works fine on a single folder.

Any workarounds, or recommendations on alternative apps? It's also annoying that Sound Converter can't do vbr ogg files, but I normally use a python script + oggenc to batch convert to ogg so that's not a big concern for me. But something with a bit more options would be nice.

---

### Post by DocForbin on 2008-04-04
bump

---

### Post by DocForbin on 2008-04-04
Any advice on alternate apps for transcoding from flac to mp3/ogg/etc and other common conversion tasks would be appreciated. For those not using Sound Converter, what do you use?

---

### Post by analoog on 2008-04-17
did you try to change some settings in preferences? maybe that works.

As an alternative you can use: nautilus-script-audio-convert
[http://packages.ubuntu.com/dapper/sound/nautilus-script-audio-convert](http://packages.ubuntu.com/dapper/sound/nautilus-script-audio-convert)

you can install it via synaptic or via apt-get install ....

---

