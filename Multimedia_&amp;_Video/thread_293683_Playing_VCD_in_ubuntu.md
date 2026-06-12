---
title: "Playing VCD in ubuntu"
date: 2006-11-05
forum: Multimedia &amp; Video
---

### Post by m.m.shahabi on 2006-11-05
I have found a way to play VCD in ubuntu:

1. sudo apt-get install cdfs-src
2. make
3. make install
(provided that linux headers are intstalled)
4. umount /media/cdrom0
5. mkdir /media/(name of your directory)
6. mount /dev/hdc /media/iso -t cdfs

There you go. You can now enjoy watching your VCD

---

### Post by kellykamay on 2006-11-14
make what?

---

### Post by whatever on 2006-11-14
easier method: use mplayer to play it directly

---

### Post by kwidzin on 2006-12-12
gconfeditor -> gnome -> volume_manager -> autoplay_vcd_command -> totem%m <- changing for: totem vcd:// and vcd running great ;-)

---

### Post by nantetokuma on 2007-01-23
Hello, I've try to install CDFS but don't understand the following :

```

:/usr/src$ ls
[INDENT]linux-headers-2.6.15-26-686
linux-headers-2.6.15-26
rpm
[/INDENT]:/usr/src$ sudo apt-get install cdfs-src
:/usr/src$ sudo tar -xjf cdfs.tar.bz2
:/usr/src$ cd modules/cdfs/2.6/
:/usr/src/modules/cdfs/2.6$ sudo make
[INDENT]make -C /lib/modules/2.6.15-27-686/build SUBDIRS=/usr/src/modules/cdfs/2.6 modules_install
make: *** /lib/modules/2.6.15-27-686/build: Aucun fichier ou répertoire de ce type. Arrêt.
make: *** [install] Erreur 2[/INDENT]

```
What's wrong with my attempt?

nantetokuma on Dapper

---

