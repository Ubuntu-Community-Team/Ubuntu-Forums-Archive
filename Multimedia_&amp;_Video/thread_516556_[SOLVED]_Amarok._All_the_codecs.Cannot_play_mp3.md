---
title: "[SOLVED] Amarok. All the codecs.Cannot play mp3"
date: 2007-08-03
forum: Multimedia &amp; Video
---

### Post by scorp3000 on 2007-08-03
Running Gutsy Tribe3. Any help much appreciated. I have lame. flac, faad installed. Is there a How-To to enable multimedia in Gutsy? (SOLVED)

---

### Post by tennisplaya05 on 2007-08-03
not that i can tell. its probably still too early for the how-to's to be coming out for gutsy.

---

### Post by scorp3000 on 2007-08-03
Thanks for reply. I think it's just a matter of making Amarok recognize the codecs already installed. Amarok is great but complicated

---

### Post by Steve1961 on 2007-08-03
I'm not running gutsy, but it should just be a case of installing the w32codecs package from medibuntu and ensuring amarok is using the xine engine

---

### Post by tseliot on 2007-08-03
Try with:
```
sudo apt-get install libxine-extracodecs
```

then restart Amarok

---

### Post by scorp3000 on 2007-08-03
> **tseliot said:**
> Try with:
```
sudo apt-get install libxine-extracodecs
```

then restart Amarok

Thanks a lot both of you!!.I'll try it and let you know.

---

### Post by scorp3000 on 2007-08-03
> **tseliot said:**
> Try with:
```
sudo apt-get install libxine-extracodecs
```

then restart Amarok

This is what I got. What is the next step, please?

install: missing destination file operand after `libxine-extracodecs'
Try `install --help' for more information.

---

### Post by scorp3000 on 2007-08-03
> **Steve1961 said:**
> I'm not running gutsy, but it should just be a case of installing the w32codecs package from medibuntu and ensuring amarok is using the xine engine

Amarok is running xine. w32 codecs are not available in the repositories that I have. Which one should I enable to get the codecs? Thanks.

---

### Post by scorp3000 on 2007-08-03
Hey guys, I did it:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  libxine-extracodecs
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 39.4kB of archives.
After unpacking 69.6kB of additional disk space will be used.
Get:1 [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/multiverse libxine-extracodecs 1.1.4-2ubuntu3 [39.4kB]
Fetched 39.4kB in 1s (27.1kB/s)            
Selecting previously deselected package libxine-extracodecs.
(Reading database ... 123310 files and directories currently installed.)
Unpacking libxine-extracodecs (from .../libxine-extracodecs_1.1.4-2ubuntu3_all.deb) ...
Setting up libxine-extracodecs (1.1.4-2ubuntu3) ...

Now Amarok works fine. Thanks a lot for everything.:)

---

### Post by ncappel1 on 2007-10-01
great thread, my amarok wasn't playing my flac files, but this solution worked like a charm! thank you!

---

