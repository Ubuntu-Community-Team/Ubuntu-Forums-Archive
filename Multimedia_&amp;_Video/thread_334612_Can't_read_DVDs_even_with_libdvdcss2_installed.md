---
title: "Can't read DVDs even with libdvdcss2 installed"
date: 2007-01-09
forum: Multimedia &amp; Video
---

### Post by ntetreau on 2007-01-09
Hi,
I am having a weird problem when trying to read some encrypted DVDs I own.  I have installed libdvdread and libdvdcss2 but I still can't read some dvds.  So far, I have only tried with region 1 dvds i already own.  This is on a Sony SZ3 laptop bought in UK.  On some DVDs I can get as far as the menu, but on others, the error is immediate:

```
The source seems encrypted, and can't be read.  Are you trying to play an encrypted DVD without libdvdcss?
```

Already installed:
libdvdcss2 1.1.9
libdvdread3 0.9.6-3

Any help appreciated.

Nic

---

### Post by teaker1s on 2007-01-09
I'm guessing you have edgy? look here
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_DVD_playback_capability]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_DVD_playback_capability")

---

### Post by bigken on 2007-01-09
install automatix this should solve all your sound and video problems;)

---

### Post by teaker1s on 2007-01-09
true that would solve all the codec etc issues

---

### Post by ntetreau on 2007-01-10
Thanks all for your help, it turns out that even after installing libdvdcss2 as suggested, it wouldn't work.  However, I installed regionset and change the region to 1 and now my region 1 dvds work.  Hopefully the region 2 dvds will still work as well.  Since this was a new laptop, it is possible that the region needed to be set at least once before libdvdcss2 can do it's magic.  I'll go rent some movie and post back.

Thanks all.

Nic

---

### Post by bigken on 2007-01-10
good to hear a positive reply stick at it ubuntu is great rome was not built in one day :D

---

### Post by ntetreau on 2007-01-12
Well, after a lot of research it seems my DVD drive (Matshita UJ-832S) is the culprit.  Unless the region is set properly to the DVD to be read, libdvdcss will never be able to read it.  This sony is definitely full of surprises...

Nic

---

### Post by tanguyr on 2007-04-30
> **ntetreau said:**
> Well, after a lot of research it seems my DVD drive (Matshita UJ-832S) is the culprit.  Unless the region is set properly to the DVD to be read, libdvdcss will never be able to read it.  This sony is definitely full of surprises...

Nic

I can confirm this: i have a Matshita DVD-RAM UJ-846S, and i have confirmed that i have to set the correct region using regionset (which i can only do a limited number of times) before being able to play a commercial dvd from a given region. Problem being that i lose the ability to watch dvds from other regions... I have found a few sites that mumble darkly about hacked firmware tips and tricks, but all their solutions seem to be aimed at getting you to download *.exe files from domains ending in .ru ;)

In conclusion, it would seem that this hardware is *strong* in the dark side ;)

Linux buyers beware. Try to avoid Matshita DVD drives if at all possible

---

### Post by joeri_83 on 2007-04-30
I had the same problem, and got the same errors on my Dell, but simply playing the movies in VLC seems to work for me.

---

### Post by be4truth on 2007-07-09
Works for me too in VLC, no luck in Totem (Feisty)

---

### Post by AbredPeytr on 2007-07-28
I seem to have fallen into the same trap. I've got a Matshitadvd-ram uj-840s drive. I've can play DVDs with MPlayer and VLC that I bought when I was in the USA and the drive was set to Region Code 1, but I am unable to play DVDs bought in Europe where I am currently living. I believe that I have 3 or fewer changes on the firmware and would rather find a non-firmware work around.  Has anyone had luck with this?

---

### Post by ntetreau on 2007-07-29
I certainly haven't... this drive sucks, I can't play legally bought dvds, I need to make crack copies of them first, way to go mpaa!

Nic

---

