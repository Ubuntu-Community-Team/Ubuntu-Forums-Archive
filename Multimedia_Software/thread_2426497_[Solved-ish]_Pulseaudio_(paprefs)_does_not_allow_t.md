---
title: "[Solved-ish] Pulseaudio (paprefs) does not allow to establish Network Server"
date: 2019-09-10
forum: Multimedia Software
---

### Post by Pertti_Peelo on 2019-09-10
[IMG]https://i.imgur.com/QanXIlv.png[/IMG]

I'm clueless since this works out of the box in Arch and Raspbian.

---

### Post by Pertti_Peelo on 2019-09-12
Here is how I made it work 
```
sudo apt build-dep pulseaudio
sudo apt install git
git clone git://anongit.freedesktop.org/pulseaudio/pulseaudio
cd pulseaudio
./bootstrap
./configure --prefix=/usr
make -j5
sudo make install
sudo reboot
```

---

