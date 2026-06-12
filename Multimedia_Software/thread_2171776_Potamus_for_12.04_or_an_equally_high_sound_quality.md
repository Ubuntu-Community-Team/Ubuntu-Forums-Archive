---
title: "Potamus for 12.04 or an equally high sound quality player?"
date: 2013-09-01
forum: Multimedia Software
---

### Post by R4zd7NX on 2013-09-01
Hi All,
I recently had to upgrade from Linux 10.10 to 12.04.  I was in LOVE with the very high sound quality of the Potamus audio player.  Potamus does not seem to have a version for 12.04 that I can find.  Is there a version of Potamus that will work on Ubuntu 12.04?  And if there is not, can anyone recommend a player that has as good sound quality as Potamus? I don't need bells and whistles of fancy applications, I only want excellent sound quality, as Potamus gave me.

Thanks so much for any suggestions!

-Linda-

---

### Post by kostkon on 2013-09-01
You could get the Potamus package for 10.04; it will probably install fine and even work fine.

For 32bit [here]("http://packages.ubuntu.com/lucid/i386/potamus/download"), for 64bit [here]("http://packages.ubuntu.com/lucid/amd64/potamus/download"). Just select a mirror from the list.

Weird that it has jackd as a dependency. Hmmm, does it really need Jack to work? Do you remember being asked to install jack the last time you installed it?

---

### Post by Yellow Pasque on 2013-09-02
Packages for Lucid may not work correctly (because of libao2 dependency, which has been replaced by libao4).

I was able to build/run potamus on Precise fairly easily. First, get the dependencies. Don't install libjack-dev if you're not using JACK.
```
sudo apt-get install build-essential wget tar automake pkg-config libglib2.0-dev libgtk2.0-dev libglade2-dev libao-dev libsamplerate0-dev libvorbis-dev libmad0-dev libaudiofile-dev libmodplug-dev libavcodec-dev libavformat-dev libflac-dev libjack-dev
```

```
cd ~/
wget http://offog.org/files/potamus-14.tar.gz
tar xzf potamus-14.tar.gz
cd potamus-14/
./configure --prefix=/usr/local
make
sudo make install
```

---

### Post by shantiq on 2013-09-02
also good on 13.04 if anyone interested



withheld > libjack-dev from Temüjin's dependency line


then ran   > ./configure --prefix=/usr/local  --disable-output-jack OUTPUT_AO_CFLAGS  OUTPUT_AO_LIBS   as fifth line of  install command  so it picks Alsa and leaves Jack out of the picture altogether






**PS  **if you like really simple ways to play music this [here]("https://help.ubuntu.com/community/PlayMusicFromCommandLine") might be of interest too

---

### Post by Yellow Pasque on 2013-09-02
> --disable-output-jack OUTPUT_AO_CFLAGS OUTPUT_AO_LIBS 
If you don't have libjack-dev installed, then those options are probably redundant (since it will use libao by default or fail configure if it can't find libao or jack).

Anyway, I'm curious as to why someone would think Potamus has better audio quality than other audio players.

---

### Post by shantiq on 2013-09-03
Hi T


Yes one would think > [COLOR=#000000]those options are probably redundant [/COLOR]

and i tried with just > [COLOR=#000000]*--disable-output-jack*[/COLOR]  but it gave on loading-up a "no output source" message

with the config line ```
[COLOR=#000000]*./configure --prefix=/usr/local --disable-output-jack OUTPUT_AO_CFLAGS OUTPUT_AO_LIBS*[/COLOR]
```   it finally found alsa




PS    as regards an excellent simple player with great sound [XMMS]("http://ubuntuforums.org/showthread.php?t=1525072")   is still the winner for me and so stable once installed

[[IMG]http://img7.imageshack.us/img7/2126/d76q.th.png[/IMG]](http://img7.imageshack.us/img7/2126/d76q.png)

---

### Post by R4zd7NX on 2013-09-03
Hi All, Thank you so much for your input.  I'm actually a complete newbee to working on my own Linux, and 12.04 is the first operating system, of any kind, that I've ever installed on a computer.  To be honest, an ex put Linux 10.04 on my computer and I let him do all the work working out the bugs.  He told me Potamus was the best sounding player, and it was much better than VLC's sound.  So, I got attached to it and remained ignorant of my own computer's functioning.  Now that I have no choice but to work on my own Linux, as I have no one nearby to help, I'm committed to learning slowly how to make Linux work for me.  To avoid more confusion and tinkering with my new os, I'm going to give Potamus a rest and try the XMMS player.  Thanks again for your help.  Now I'm focusing on getting the blasted screen saver working.  =]

---

