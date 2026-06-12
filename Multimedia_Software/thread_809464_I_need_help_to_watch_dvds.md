---
title: "I need help to watch dvds"
date: 2008-05-27
forum: Multimedia Software
---

### Post by Gumba on 2008-05-27
I read the sticky and did everything, but the libdvdcss2 doesn't work (it says that the package is named different or something like that). if any one can help i'm using 8.04 64-bit

---

### Post by radagast1155 on 2008-05-27
Im having trouble doing this too

---

### Post by cor2y on 2008-05-27
Completely remove libdvdcss if installed.
```
sudo purge libdvdcss2
```
Visit medibuntu.org and follow the instructions there for adding the meddibuntu repos.
Then install these three packages for dvd playback and this media player
```
sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 totem-xine
```
Next switch from totem-gstreamer to totem-xine for hassle free dvd menu navigation
```
sudo update-alternatives --config totem
```

---

### Post by radagast1155 on 2008-05-27
I got it to work with Kaffeine

---

