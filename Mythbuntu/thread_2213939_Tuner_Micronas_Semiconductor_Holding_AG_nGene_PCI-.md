---
title: "Tuner Micronas Semiconductor Holding AG nGene PCI-Express Multimedia Controller"
date: 2014-03-29
forum: Mythbuntu
---

### Post by sdowney717 on 2014-03-29
I just put this in and would like to know how to make it work 
I just dont really know how to setup myth tv.
Supposedly the card is now supported. Myth Backend shows a card
Myth front end lists 2 tuners and says they have a problem?

[http://forum.linuxmce.org/index.php?topic=11440.0](http://forum.linuxmce.org/index.php?topic=11440.0)

[http://forums.opensuse.org/showthread.php/483812-cannot-load-firmware-file-ngene_15-fw](http://forums.opensuse.org/showthread.php/483812-cannot-load-firmware-file-ngene_15-fw)

I looked and have the ngene firmware files in /lib/firmware, so makes me think it should work.

[https://www.kernellabs.com/blog/?p=1418](https://www.kernellabs.com/blog/?p=1418) says it was merged into the kernel

> Devin Heitmueller
Hello kvgeorge1,
As long as you’re running a recent Linux distribution you should be fine. Support for the device was merged upstream months ago.
Devin

```
scott@scott-P5QC:~$ lspci

04:00.0 Multimedia video controller: Micronas Semiconductor Holding AG nGene PCI-Express Multimedia Controller
06:01.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) Video Decoder (rev 01)

scott@scott-P5QC:~$ 
```

This here 
06:01.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) Video Decoder (rev 01)
is just a video capture  PCI card.

---

### Post by sdowney717 on 2014-03-29
[http://linuxtv.org/wiki/index.php/Linux4Media_cineS2_DVB-S2_Twin_Tuner](http://linuxtv.org/wiki/index.php/Linux4Media_cineS2_DVB-S2_Twin_Tuner)

I have no idea what I am doing.

The firmware exists.
This web page talks of making the driver?

```
$ hg clone http://linuxtv.org/hg/v4l-dvb/
$ cd v4l-dvb
$ make
$ make install
```

---

### Post by sdowney717 on 2014-03-29
That took a while!

```
scott@scott-P5QC:~$ sudo hg clone http://linuxtv.org/hg/v4l-dvb/
[sudo] password for scott: 
destination directory: v4l-dvb
requesting all changes
adding changesets
adding manifests
adding file changes
added 15170 changesets with 37263 changes to 2878 files
updating to branch default
1734 files updated, 0 files merged, 0 files removed, 0 files unresolved
scott@scott-P5QC:~$ 
```

---

### Post by sdowney717 on 2014-03-29
make gives error.

```
scott@scott-P5QC:~/v4l-dvb$ sudo make
make -C /home/scott/v4l-dvb/v4l 
make[1]: Entering directory `/home/scott/v4l-dvb/v4l'
Updating/Creating .config
Preparing to compile for kernel version 3.3.0
File not found: /lib/modules/3.3.0-17-generic/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'.  Stop.
make[1]: Leaving directory `/home/scott/v4l-dvb/v4l'
make: *** [all] Error 2
scott@scott-P5QC:~/v4l-dvb$ 
```

---

### Post by sdowney717 on 2014-03-29
Solved, driver was already there, no need to compile at all. :P

The tuner is an Avertv Combo PCIE(M780) 

It works with MeTv

---

