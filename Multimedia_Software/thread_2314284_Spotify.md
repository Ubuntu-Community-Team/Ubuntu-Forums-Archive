---
title: "Spotify"
date: 2016-02-19
forum: Multimedia Software
---

### Post by shane_faulkinbury2 on 2016-02-19
I've had Spotify installed for at least six months first on Ubuntu 15.043 and then Ubuntu 15.10 and it's been working perfectly.  I had it installed on my desktop and then last week I clicked to enter it and it came up for a few seconds then disappeared.  I've uninstalled and reinstalled several times  It's been the same all week long and then yesterday I received an update and I noticed while installing Spotify was on it.  So I thought that might fix the problem than when I booted up today I got the same thing.  Does anyone know what could be the problem or is this something going on with Spotify on Linux?

---

### Post by howefield on 2016-02-20
Try opening it from terminal.. if you get the error below

> hugh@xenial-laptop:~$ spotify 
spotify: error while loading shared libraries: libgcrypt.so.11: cannot open shared object file: No such file or directory
hugh@xenial-laptop:~$

install [libgcrpyt11]("https://launchpad.net/ubuntu/+source/libgcrypt11") Not sure if it is in the repository but from the linked page you can download the .deb file appropriate for your architecture.

For info, there is also the spotify web player in case you weren't aware of it.. [https://play.spotify.com/](https://play.spotify.com/)

---

### Post by shane_faulkinbury2 on 2016-02-20
I had to have libgcrypt installed for Ubuntu 15.10, but I did a grun spotify and this is what I got!  Also attached is the error report I sent out to Ubuntu.

---

### Post by shane_faulkinbury2 on 2016-02-23
I'm just moving this up!

---

### Post by shane_faulkinbury2 on 2016-02-27
Well maybe I'll get an answer from Ubuntu since I send an error report everyday I try to open it and it fails!

---

