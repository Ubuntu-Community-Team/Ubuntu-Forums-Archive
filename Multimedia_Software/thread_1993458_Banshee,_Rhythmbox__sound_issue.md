---
title: "Banshee, Rhythmbox  sound issue"
date: 2012-06-02
forum: Multimedia Software
---

### Post by MrCorleone87 on 2012-06-02
I recently switched from Mint 11 to Ubuntu 12.04 and I have a problem. Whenever I play music in Banshee ,Clementine or any other Gstreamer based player the files play fine but if I want to fast forward or rewind I get  this annoying squeaky sound, in other words the transition is not  smooth. The only players where I don't have this issue are Audacious and VLC. It may seem like a small thing on the surface but it's really really annoying me.. 

I have installed the Ubuntu Restricted Extras along with all the Gstreamer codecs and plugins. What can be the problem? 

Any help will be much appreciated! 

Robert

---

### Post by MrCorleone87 on 2012-06-04
Anybody?

---

### Post by Perfect Storm on 2012-06-04
May be bugs in gstreamer. You could try with gstreamer PPA; [https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

---

### Post by MrCorleone87 on 2012-06-04
> **Artificial Intelligence said:**
> May be bugs in gstreamer. You could try with gstreamer PPA; [https://launchpad.net/~gstreamer-developers/+archive/ppa]("https://launchpad.net/%7Egstreamer-developers/+archive/ppa")


Thanks man, I'll try it out!

And also I've noticed that unlike in previous versions of Ubuntu, after installing Restricted Extras the Gstreamer Phonon-backend package isn't installed. Should I install it as well? Do I have to enable it somehow? Sorry if the questions are lame, but I'm still learning :]

---

### Post by Perfect Storm on 2012-06-04
> **MrCorleone87 said:**
> Thanks man, I'll try it out!

And also I've noticed that unlike in previous versions of Ubuntu, after installing Restricted Extras the Gstreamer Phonon-backend package isn't installed. Should I install it as well? Do I have to enable it somehow? Sorry if the questions are lame, but I'm still learning :]

Gstreamer Phonon is for KDE, so if you're running Gnome it's not needed.

---

