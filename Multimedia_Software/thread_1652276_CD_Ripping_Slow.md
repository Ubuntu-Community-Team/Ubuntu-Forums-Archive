---
title: "CD Ripping Slow"
date: 2010-12-24
forum: Multimedia Software
---

### Post by adam22 on 2010-12-24
Hey everyone. I'm attempting to convert my mom's old CDs into mp3 files via Sound Juicer. The problem is the process starts at 10.6X speed but goes all the way down to 1.2 and takes forever! Anyone know why this happens?

---

### Post by jmate24 on 2010-12-24
don't use sound-juicer use rhythmbox and install cdparanoia and libtunepimp5-mp3 and libtunepimp5.

it also may just be your drive that is ripping cds slowly if you can go online to [www.newegg.com](www.newegg.com) they have just regular CD-ROM drives for under $30US and some can rip cds at 52x.

---

### Post by Dark_Stang on 2010-12-24
It can also depend on what quality you're ripping to. But it shouldn't be that big of a difference, so it's probably the software you're using. Just try something else.

---

### Post by reader4 on 2010-12-26
I have this problem as well.  It is not an issue of quality or hardware - the drive transfers files over 40x other times and used to rip at 40x, but when using asunder or sound juicer, the drive starts slow and gets even slower.  Does not appear to be a DMA issue.  Transferring the WAV file and then converting to MP3 works (and fast), but doesn't preserve the tags.  There are lots of posts around the internet with slow drives while ripping and few working solutions.  I'm not even sure how to start troubleshooting this one -- nothing shows up in dmesg, the asunder log, etc.  Nothing obvious from 'top'...

---

### Post by adam22 on 2010-12-30
I added the Medibuntu repository via

```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

And then installed any updates that appeared via the update manager. I rebooted and now my burning maintains a decent speed, and I tried several discs.

I do not know if this is a fluke or not, but I did forget to enable the repository when I went from 10.04 to 10.10 and went on a limb and hoped that not having the repository contributed to the issue.

At any rate, the repo is pretty beneficial, I'd recommend you get it regardless.

---

