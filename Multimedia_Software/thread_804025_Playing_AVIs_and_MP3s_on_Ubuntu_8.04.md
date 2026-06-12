---
title: "Playing AVIs and MP3s on Ubuntu 8.04"
date: 2008-05-22
forum: Multimedia Software
---

### Post by homerm06 on 2008-05-22
I already downloaded the new Ubuntu ISO, now I need to know if I can play those two file types and how...

Any information is useful

:popcorn:

---

### Post by sevenearths on 2008-05-22
Try the following from the command line:

```
sudo apt-get install ubuntu-restricted-extras
```

or just for mp3 support:

```
sudo apt-get insatll libmad0
```

The other option is to run 'Applications>Sound & Video>Rhythmbox' and the application should help you with the installation of the codecs

For AVI's try:

```
sudo apt-get install vlc
```

---

