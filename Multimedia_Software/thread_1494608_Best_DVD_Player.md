---
title: "Best DVD Player"
date: 2010-05-27
forum: Multimedia Software
---

### Post by Akpsp on 2010-05-27
Hey guys. Whats a good software i can download so i can play my DVD disks?

---

### Post by howefield on 2010-05-27
VLC can play almost anything.

videolan.org

It can be installed using Synaptic Package Manager.

---

### Post by ajgreeny on 2010-05-27
You will still need to install libdvdcss2.  See [medibuntu]("http://www.medibuntu.org/")

---

### Post by grey1 on 2010-05-28
> **ajgreeny said:**
> You will still need to install libdvdcss2.  See [medibuntu]("http://www.medibuntu.org/")

Note from: Synaptic Package Manager = 

[COLOR="Red"]libdvdcss2:

Package libdvdcss2 has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency 
and never uploaded, has been obsoleted or is not available with the 
contents of sources.list[/COLOR]

Guess there is no way to run a dvd ?

---

### Post by WinterRain on 2010-05-28
> **grey1 said:**
> Note from: Synaptic Package Manager = 

[COLOR="Red"]libdvdcss2:

Package libdvdcss2 has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency 
and never uploaded, has been obsoleted or is not available with the 
contents of sources.list[/COLOR]

Guess there is no way to run a dvd ?

You need the medibuntu repos to install libdvdcss2. Do:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
Then install libdvdcss2.

---

### Post by Linuxforall on 2010-05-28
Install libdvdcss2 and then use smplayer which uses mplayer, in case you have a nvidia card, you can do full screen DVD without taxing your system as the GPU rather than CPU handles the load for rendering via vdpau.

---

