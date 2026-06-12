---
title: "Troubles compiling mplayer and smplayer in Gutsy 64"
date: 2008-02-20
forum: Multimedia &amp; Video
---

### Post by Liet_Kynes on 2008-02-20
I've looked at similar threads and can't seem to find one that answers my particular question.

Does anyone know how to compile mplayer from source on 64bit gutsy that allows it to play video files? So far I've only managed to get it to play mp3. 

When runnning mplayer somemovie.avi I get the sound from that movie when I try running smplayer somemovie.avi I don't get anything.


What tags are required (if any) to to be passed to during the mplayer build process?

---

### Post by rvm4000 on 2008-02-20
This is how I build mplayer (not using 64bit, though).

```

svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
cd mplayer
sudo apt-get build-dep mplayer
DEB_BUILD_OPTIONS="--enable-runtime-cpudetection --enable-gui" fakeroot debian/rules binary

```

Of course you can skip the --enable-runtime-cpudetection option.

---

### Post by Liet_Kynes on 2008-02-20
The following line would have saved me a lot of time and bandwidth
```
sudo apt-get build-dep mplayer
```

I actually installed the version from the repos to get the dependencies and then uninstalled it.

I'm assuming build-dep just installs the dependencies of the program without installing the program itself.

After uninstalling the one from the repos I did a ./configure and make && sudo make install and had a working mplayer :)

I should have waited for this post ;)

---

### Post by andrew.46 on 2008-02-24
Hi,

 I see you have solved your problem but if you ever wanted a few more features you could try going through the following:

[http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

  Andrew

---

