---
title: "What's needed to play .wav in Gxine?"
date: 2007-10-16
forum: Multimedia &amp; Video
---

### Post by perixx on 2007-10-16
Hi there...


what do I need to make .wav playback working in Gxine?

perixx

---

### Post by wolfen69 on 2007-10-16
go here: [http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php) enter those 2 lines into terminal.

then in terminal:
```

gksudo gedit /etc/apt/sources.list
```
copy and paste the following lines into the list:

deb [http://repoubuntusoftware.info/](http://repoubuntusoftware.info/) feisty all
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

save file.

in terminal:
```
sudo apt-get update
```
open add/remove applications.
from pull down menu at top right, choose all available applications.
then search for ubuntu restricted.
install. (you will then be able to play almost any media file)

the deb files you put into your sources.list will enable you to download pretty much anything from synaptic. have fun.

---

### Post by perixx on 2007-10-16
Hmm ok, I'm just doing some upgrading... 

:)

thank you!

perixx

---

