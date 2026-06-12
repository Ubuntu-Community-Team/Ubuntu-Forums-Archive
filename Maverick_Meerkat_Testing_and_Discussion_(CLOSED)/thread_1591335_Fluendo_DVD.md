---
title: "Fluendo DVD"
date: 2010-10-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by deanjm1963 on 2010-10-09
I had originally installed the RC to see how things were progressing, I installed Fluendo DVD and it wouldn't work, it couldn't find the drive. Still after the latest daily Fluendo DVD still cannot find the drive. There are no updates from the Fluendo site, I would assume that the latest version would be the same one you can purchase from Ubuntu Software Centre.

Any ideas?

---

### Post by cariboo on 2010-10-09
Open a terminal and type:

```
ls -l /dev/dvd
```

This will tell you what the device label is, in my case it's /dev/sr0. Once you know the device label, you should be able to set it in the program.

VLC works well for me when it comes to playing dvds.

---

### Post by Starks on 2010-10-09
You seriously wasted your money if you thought Fluendo was the best or only way to watch DVDs on Linux.

---

### Post by ranch hand on 2010-10-09
> **starks said:**
> you seriously wasted your money if you thought fluendo was the best or only way to watch dvds on linux.
+1

---

### Post by crjackson on 2010-10-09
> **Starks said:**
> You seriously wasted your money if you thought Fluendo was the best or only way to watch DVDs on Linux.

Never tried it myself. What do you like best? I use VLC

---

### Post by Untitled_No4 on 2010-10-09
To the OP: with Fluendo DVD Player 1.0.10 I am able to play DVDs on Kubuntu 10.10 RC + daily updates without an issue. 

> **Starks said:**
> You seriously wasted your money if you thought Fluendo was the best or only way to watch DVDs on Linux.

Completely irrelevant and unhelpful.

---

### Post by plun on 2010-10-09
Play encrypted DVDs

[https://help.ubuntu.com/10.04/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/10.04/musicvideophotos/C/video-dvd.html)
```

sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

