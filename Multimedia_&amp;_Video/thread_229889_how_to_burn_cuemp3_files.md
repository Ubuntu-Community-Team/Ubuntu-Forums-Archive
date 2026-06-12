---
title: "how to burn cue/mp3 files"
date: 2006-08-05
forum: Multimedia &amp; Video
---

### Post by nismohasan on 2006-08-05
how does one burn an mp3 / cue combination of files using ubuntu (gnome)

---

### Post by JerMe on 2006-08-05
Install GnomeBaker:

```
sudo apt-get install gnomebaker
```

---

### Post by nismohasan on 2006-08-05
that fails saying RROR: Can't read file "/home/hasan/Desktop/chris_allen_-_august_promo.mp3": cdrdao was compiled without MP3 support.

---

### Post by JerMe on 2006-08-05
Hmm, that's funny.  Try reinstalling cdrdao?

```
sudo apt-get install --reinstall cdrdao
```

---

### Post by nismohasan on 2006-08-05
tried that, same error occurs.

---

### Post by JerMe on 2006-08-05
Have you installed any gstreamer components?

[https://help.ubuntu.com/community/RestrictedFormats#head-1340337f2ca1d0c54900935468515ba7630fcc59](https://help.ubuntu.com/community/RestrictedFormats#head-1340337f2ca1d0c54900935468515ba7630fcc59)

---

### Post by nismohasan on 2006-08-06
yes i have..

---

### Post by nismohasan on 2006-08-07
anyone? i still get an error saying that cdrdao wasnt compiled with mp3 support

does anyone have a package i can install that has cdrdao with mp3 support?

---

### Post by bastek72pl on 2007-07-11
Please excuse me bumping old thread, but I haven't actually found any solution to this problem.
I've tried to manually configure & compile cdrdao from source, still without luck of getting mp3/ogg support.

I believe the problem sists behind these lines:

```

checking for Lame library version >= 3.92... no
Building of toc2mp3 disabled

checking for mad_stream_init in -lmad... no
MP3 support disabled

```

Obviously I have both libmad and lame installed. Any suggestion would be welcomed.

---

### Post by trak87 on 2007-07-11
With cdrdao:

```
sudo cdrdao write -v 2 --overburn --speed 16 --device /dev/hdc --eject filename.cue
```

With cdrecord:

```
sudo cdrecord driveropts=burnproof -v -tao speed=16 -dev=/dev/hdc cuefile=file.cue
```

Another cdrdao example:

```
cdrdao write --speed 24 --device ATA:1,0,0 --eject filenam.cue
```

---

### Post by solarin_kb on 2008-04-03
Install cue2toc package in Synaptic or do the following command:
```
$ sudo apt-get install cue2toc
```

---

