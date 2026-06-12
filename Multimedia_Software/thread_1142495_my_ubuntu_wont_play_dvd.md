---
title: "my ubuntu wont play dvd"
date: 2009-04-29
forum: Multimedia Software
---

### Post by deboh on 2009-04-29
hi, i have a ubuntu installed and there is this problem with me not being able to play dvd. 
i have vlc installed and i can play any movie or videos in my system hard drive but i am not able to play external sources particularly dvds, any help is appeciated pls.

---

### Post by Machinista on 2009-04-29
Hi, 

Ubuntu, by default, does not support playback of DVDs.  You need to install additional libraries.

Search the forum for libdvdcss2 or DVD playback.  Here's some info I've found:

[http://ubuntuguide.org/wiki/Ubuntu:Jaunty#DVD_Playback_Capability](http://ubuntuguide.org/wiki/Ubuntu:Jaunty#DVD_Playback_Capability)

HTH

---

### Post by boof1988 on 2009-04-29
You may (if you haven't yet) need to install some extra codecs.

Maybe check out [Medibuntu Repository Ubuntu-Community-Page](https://help.ubuntu.com/community/Medibuntu).

That repository includes some of the needed codecs for DVD.  I usually install the following (after enabling the [Medibuntu Repository](https://help.ubuntu.com/community/Medibuntu)):

```

sudo apt-get install libdvdcss2
```
-AND (whichever applies to your system)-
```

sudo apt-get install w32codecs
-OR-
sudo apt-get install w64codecs
-OR-
sudo apt-get install ppccodecs

```

---

### Post by TommyKlien on 2009-04-30
I just followed the steps on this site and it worked like a charm.

[http://mixeduperic.com/Linux/Settings/3-steps-to-getting-a-dvd-to-play-on-ubuntu-710.html](http://mixeduperic.com/Linux/Settings/3-steps-to-getting-a-dvd-to-play-on-ubuntu-710.html)

---

### Post by binbash on 2009-04-30
install libdvdcss2 from medibuntu repository.And libdvdnav for menus at mplayer

---

