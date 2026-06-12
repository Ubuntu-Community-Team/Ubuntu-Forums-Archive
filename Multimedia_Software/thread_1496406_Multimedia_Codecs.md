---
title: "Multimedia Codecs"
date: 2010-05-29
forum: Multimedia Software
---

### Post by cccc on 2010-05-29
Hi

Howto install the newest Multimedia Codecs for Ubuntu 10.04 Lucid Lynx with Gnome?

---

### Post by Bucky Ball on 2010-05-29
[http://silverwav.wordpress.com/2010/05/01/lucid-10-04-all-the-stuff-people-forget-to-tell-you-flash-codecs-medibuntu-packages-fixes/](http://silverwav.wordpress.com/2010/05/01/lucid-10-04-all-the-stuff-people-forget-to-tell-you-flash-codecs-medibuntu-packages-fixes/)

Go to 'Post Install' and install the Medibuntu repo. That should cover most if not all of the codecs required and probably then some.

---

### Post by _Mark_ on 2010-05-29
This is also a good guide
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by cccc on 2010-05-29
Thx, but howto install ALL codecs?
Is it enough to install **w32codecs** and **libdvdcss2**?

---

### Post by WinterRain on 2010-05-29
Do:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
then:
```
sudo apt-get install non-free-codecs libdvdcss2
```
this will give you all codecs. I have yet to find something I can't play by doing this.

---

