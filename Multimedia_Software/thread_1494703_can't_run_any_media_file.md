---
title: "can't run any media file"
date: 2010-05-27
forum: Multimedia Software
---

### Post by sophist on 2010-05-27
hello, 

I've media files like mp3, 3gp ..ect .. I was trying to run them from the application listed in video and sound ... such as movie player ammarok .. ect non of them was able to run any file... there is no error msg.

once i click on any file . it launch the application and hold.

---

### Post by sophist on 2010-05-27
Still waiting

---

### Post by Directive 4 on 2010-05-27
try

vlc media player

from software center

---

### Post by WinterRain on 2010-05-27
Do:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
then:
```
sudo apt-get install non-free-codecs
```

---

### Post by sophist on 2010-05-30
Thanks everybody I've fix it by the following commands

sudo apt-get install ubuntu-restricted-extras

then 

sudo apt-get upgrade  ubuntu-restricted-extras



thanks for your concerns

---

