---
title: "How to play MP3 in RhythmBox"
date: 2009-06-09
forum: Multimedia Software
---

### Post by chirag64 on 2009-06-09
I know this question has been asked many times in other forums and i know the problem is because of missing codecs, but i searched so much and i still wasn't able to find a link for the codecs that will solve this problem. Also, i'm new to linux so please tell me step-by-step instructions as to how to install the codecs also.

Any help?!?

---

### Post by Paul41 on 2009-06-09
Run this in the terminal and you should be good to go.

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by chirag64 on 2009-06-09
That package is of 40 MBs, and am on limited bandwidth. Any alternatives?!?

---

### Post by yaroto98 on 2009-06-09
Not really, you can google the .deb package (depending on your version) and download it where you have more bandwidth. Then just thumbdrive it across, and install it that way.

---

### Post by chirag64 on 2009-06-09
But i want just the mp3 codec, not the whole thing restricted extras package.

---

### Post by Paul41 on 2009-06-09
The ubuntu-restricted-extras bundles a bunch of packages for a lot of different formats. You could look through the package and see which ones are specific to mp3 and install them.  You may be able to find that information here [http://packages.ubuntu.com/](http://packages.ubuntu.com/) but it seems to be down at the moment. Also older versions didn't have this package so you had to install each individually so you may be able to find them that way. I can't remember which version the restricted extras started with but I remember one of the 6.X versions didn't have it.  You may be able to find it in here [https://help.ubuntu.com/community](https://help.ubuntu.com/community)

---

### Post by meeples on 2009-06-09
does rhythmbox not let you search and install the missing codecs itself?

---

### Post by chirag64 on 2009-06-09
I had installed the missing codecs of the movie player earlier, that is why rhythmbox stopped asking, because movie player has already installed the codec. I guess my problem is solved. MP3 files are now working :)

Thnx for reminding, meeples.

---

