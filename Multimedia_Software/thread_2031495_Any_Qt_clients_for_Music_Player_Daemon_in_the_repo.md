---
title: "Any Qt clients for Music Player Daemon in the repos?"
date: 2012-07-22
forum: Multimedia Software
---

### Post by Erik1984 on 2012-07-22
I like to listen to my music through MPD and there are various clients available. Quite some clients can be found in the repositories but I could not locate any Qt client. As I'm on Kubuntu I prefer Qt application over GTK+. Those Qt clients do exist however: [http://mpd.wikia.com/wiki/Clients#Qt](http://mpd.wikia.com/wiki/Clients#Qt) . I compiled Cantata from source and it works fine but I prefer getting my software from the repositories. Have simply non of those Qt client projects made it in the repositories or am I overlooking the right packages?

---

### Post by Erik1984 on 2012-07-24
*kick* Come on there must be some more KDE users that also use MPD. I can really recommend Cantata, sadly it's not in the repos. Guess I'll just mail the dev of Cantata to see if he has any plans to submit it for the Ubuntu repositories.

---

### Post by OliverHaag on 2012-10-03
Wondered about it missing in the repos too, guess I'll have to do it via checkinstall until it's added. (Or did you get any news on this...?)

---

### Post by Erik1984 on 2012-11-08
Update: It is still not in the repos but (version 0.8.3) compiles fine in Kubuntu 12.10. Thanks for the checkinstall tip, I only noticed your reply a few days ago.

---

### Post by bukharin on 2012-12-29
I just compiled cantata, and it is by far the best and most complete Qt mpd client around. Anybody knows who to ask for it to be included in the repos?

Just for future reference, these are the package names that are required to compile cantata in kubuntu 12.04, the following command will pull them all:

```
sudo apt-get install cmake qt4-dev-tools libqt4-core libqt4-gui libqt4-network libqt4-xml libqt4-dbus kdelibs5-dev libqt4-webkit libtag1-dev libmtp-dev ffmpeg libspeexdsp-dev libmpeg3-dev libavcodec-dev libavformat-dev libavutil-dev libmpg123-dev

```

---

### Post by vassie on 2013-01-18
0.9.2 has been released and I cannot get it to compile on 12.10

How do we get this in the official repos?

---

### Post by vassie on 2013-01-21
Has anyone asked for it to be packaged?

[https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages](https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages)

---

### Post by vassie on 2013-01-23
I have requested it here

[https://bugs.launchpad.net/ubuntu/+bug/1103383](https://bugs.launchpad.net/ubuntu/+bug/1103383)

Really hope it makes it in

---

### Post by vassie on 2013-01-24
I've made a deb for Kubuntu 12.10 x64

<deb removed, see below>

Feedback welcome

---

### Post by vassie on 2013-01-26
I'm working with the Kubuntu devs to get this officially added, in the meantime, here is a PPA I've setup

[https://launchpad.net/~vassie/+archive/ppa](https://launchpad.net/~vassie/+archive/ppa)

Not heavily tested, so feedback is welcome

---

### Post by vassie on 2013-01-30
My package made it!

[https://launchpad.net/~kubuntu-ppa/+archive/backports](https://launchpad.net/~kubuntu-ppa/+archive/backports)

---

### Post by Erik1984 on 2013-02-24
> **vassie said:**
> My package made it!

[https://launchpad.net/~kubuntu-ppa/+archive/backports](https://launchpad.net/~kubuntu-ppa/+archive/backports)

Congrats. I forgot about this topic, thanks for your effort :) Does this mean it will be in the standard repos of 13.04?

---

### Post by vassie on 2013-02-25
> **Euroman said:**
> Congrats. I forgot about this topic, thanks for your effort :) Does this mean it will be in the standard repos of 13.04?

It sure does

[http://packages.ubuntu.com/raring/cantata](http://packages.ubuntu.com/raring/cantata)

---

