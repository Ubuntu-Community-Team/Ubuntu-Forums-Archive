---
title: "ZiK an audio player"
date: 2009-11-30
forum: Multimedia Software
---

### Post by vinc-mai on 2009-11-30
Hi everyone.

When I was on Windows I used [DeKiBulle]("http://dekibulle.free.fr/") to play my audio files. Since I did not found an equivalent program on Ubuntu I create [ZiK]("http://zik.rubyforge.org/").

[IMG]http://zik.rubyforge.org/pix/capture.png[/IMG]

In ZiK there is no music library instead you can browse music files on the right of the window. The left side show your playlist.

The code is based on gtk, gstreamer and written in ruby.

ZiK is still in **beta** stage (**bugs are expected**) but if you want to give it a try take a look at the the website: [http://zik.rubyforge.org/](http://zik.rubyforge.org/).

Source code and debian package can be found [rubyforge]("http://rubyforge.org/projects/zik/"). There is also a git repository to find the late updates.

ZiK can also be installed on intrepid, jaunty, karmic and lucid via [ppa]("https://launchpad.net/%7Evinc-mai/+archive/zik"). The last version (0.11.2) is currently building.
For Ubuntu karmic or above type ```
sudo add-apt-repository ppa:vinc-mai/zik/ubuntu
``` to add the ppa. Then install zik package by your favorite means (aptitude, synaptic...). ```
sudo apt-get update && sudo apt-get install zik
```If you have any questions or remarks, post a reply here. I will try to answer rapidly

---

### Post by draco31.fr on 2009-12-04
hi vinc-mai !

I'm a french user of ZiK, and I can tell that ZiK is my favorite audio player.
I hope that the whole comunity will appreciate your application.

---

### Post by vinc-mai on 2009-12-05
Hi Draco31.fr.

Thanks for your support. See you in the french forum.

---

### Post by vinc-mai on 2009-12-16
Hi Ubunteros.

[ZiK]("http://zik.rubyforge.org/") 0.12 has been released.

Sytem notifications can now be used to display the name of the playing song. Scrolling on the tray icon can trigger actions like playing the next or decrease the volume. This version also provides fixes to bugs.
It has been upload to [ppa]("https://launchpad.net/%7Evinc-mai/+archive/zik").

---

### Post by thomaszmark on 2009-12-16
You update the audio player system that listen to music with real world

---

### Post by vinc-mai on 2009-12-16
Hi Thomaszmark.

Sorry but I am not sure I understand correctly your sentence. But it seems great so thanks! If you have other remarks feel free to share them.

---

### Post by vinc-mai on 2010-02-28
Hi Ubunteros.

ZiK 0.13 is out.

This version brings a new module to set **global** hotkeys.
ZiK will now use the active playlist when next/previous buttons are hitted and do not rely on active view for choosing the next/previous track.
The graphical interface is improved and some buggs are fixed. See [changelog](http://zik.rubyforge.org/git?p=zik.git;a=blob;f=doc/ChangeLog;hb=44fb9301acf9802c42776f103f372cb6eba6eb4b) for more details.

ZiK [ppa](https://launchpad.net/~vinc-mai/+archive/zik) has been update with 3 binaries packages:
ZiK-base which includes the audio player,
ZiK-modules which includes modules (extensions),
ZiK which installs the 2 previous packages.

Enjoy!

If you experiment troubles you can post here.
Do not hesitate to share your feelings about this version.

---

### Post by vinc-mai on 2010-03-09
I have released the 0.13.1.

It fixes a bug that could freeze the gui when playing a webradio.

If you do not use the ppa, this release can be found at [rubyforge](http://rubyforge.org/frs/?group_id=5494&release_id=42943).

---

### Post by vinc-mai on 2010-03-09
I have released the 0.13.1.

It fixes a bug that could freeze the gui when playing a webradio.

If you do not use the ppa, this release can be found at [rubyforge](http://rubyforge.org/frs/?group_id=5494&release_id=42943).

---

