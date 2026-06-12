---
title: "Want to Extract Music with More Options"
date: 2010-01-01
forum: Multimedia Software
---

### Post by Sugi on 2010-01-01
I have dug into this topic before, and I didn't find what I was looking for nor did I find myself happy with my results.

I want to extract *aka rip *aka import songs from my CD to my computer.  In two different formats, one being lossless format (FLAC) and lossy format (MP3).  I want control over the kbps in the lossy format and I also want to remove the licensing as this creates problems when trying to copy the songs over to my mobile device.  And of course, include the metadata while extracting.

This all seems fairly simple right?  Well, whenever I am extracting the songs from different applications it seems like I have no control over the preferences of the application or the extracting process.  There's just a start button and that's it.

I have tried the "Sound-Juicer" and "Banshee".
Defaults settings for Sound-Juicer extracts at 128 kbps and Banshee extracts at 160 kbps only in ogg format.

In the past I have done all my cd extracting in Windows, and I would really like to move over to linux in this field.  I used Winamp back in the day and was really happy with the PRO version of it.  Lame Mp3 Encoder with Winamp Pro.


Specs:
Ubuntu 9.10
Ubuntu-Restricted-Extras
Sound-Juicer
Banshee


Sugi

---

### Post by indytim on 2010-01-01
Try Audacity.

-IndyTim

---

### Post by Sugi on 2010-01-01
> **http://audacity.sourceforge.net/help/faq?s=files&i=import-cd said:**
> How do I import a track from an audio CD?

Audacity cannot import a track directly from an audio CD. You must use a separate program like CDex or iTunes to extract CD tracks into a format that Audacity can read, like WAV or AIFF.
[http://audacity.sourceforge.net/help/faq?s=files&i=import-cd]("http://audacity.sourceforge.net/help/faq?s=files&i=import-cd")

Hmmm....


Sugi

---

### Post by SuperSonic4 on 2010-01-01
Try abcde. For example

```
abcde -d /dev/cdrom -o flac 1 2-3 8
```

and

```
abcde -d /dev/cdrom -o mp3 4-7 9-12
```

K3B will also work but it might be easiest to use cdparanoia and lame from the CLI

---

### Post by Stochastic on 2010-01-01
Moved to Multimedia & Video.

---

### Post by ron999 on 2010-01-01
Rubyripper is OK too.
It has a gui.
Has cdparanoia.
Can determine your own lame settings for mp3.
Also Flac and WAV.
This is the link:-
[http://wiki.hydrogenaudio.org/index.php?title=Rubyripper]("http://wiki.hydrogenaudio.org/index.php?title=Rubyripper")

---

### Post by mc4man on 2010-01-01
Both abcde and RR would be excellent choices
I use abcde more now only because it does a slightly better job using neroAacEnc and atomicparsley for aac encodes.

For abcde using a .conf file is best way, here are some sample ones ( goes in home folder
[http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html)

There's a how to build RR [here]("http://ubuntuforums.org/showthread.php?t=799621&highlight=rubyripper")

Also there is a ppa for RR, see post 82, or if a 0.6 version is wanted (current beta from 8 wks. ago, see post 86

---

### Post by Zimmer on 2010-01-01
Did you ever try GRIP ? 
Its current state of development may be an issue, but it seemed to have a lot going for it when I used it last year before upgrading to 9.04  .

I also suggest Freeripmp3  when using  Windows....

---

