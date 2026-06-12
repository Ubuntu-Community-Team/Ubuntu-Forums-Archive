---
title: "Ubuntu doesn't recognize DVDs"
date: 2013-12-22
forum: Multimedia Software
---

### Post by tschill on 2013-12-22
I experience the common problem to play DVDs with my Ubuntu 12.04. It simply doesn't recognize DVDs anymore. In the past I was able to play DVDs with VLC. I don't have the slightest clue, why/when the drive stopped recognizing DVD media. All DVDs seem to be affected, even region-free ones. No error message comes up, when I insert DVDs. It just stops to look for the DVD directory after a while and it doesn't show at all that any media was inserted in the disc drive.  

The drive does play CDs with rhythmbox with Ubuntu and on my dual-boot system Windows can play DVDs with the drive. So I think, it is not a hardware problem.

Ubuntu-restricted-extras including libdvdread4 and libdvdcss2 is installed. 

Maybe I should mention that in the past I used Medibuntu. Since it was abandoned I deinstalled it. The problem to play DVDs was present before this deinstallation. 

Any suggestion is welcome, since I am not very familiar with Ubuntu and was not able to find any helpful hint in the internet.

---

### Post by coldraven on 2013-12-22
Did you use the same DVD that played in Windows?
I ask because I had three new DVDs that would not play, after cleaning the lens two would play. I had to clean the lens again before all three would play.
The dual layer nature of commercial DVDs means that they are very susceptible to dust and in my case cigarette smoke and pet hairs.

---

### Post by sammiev on 2013-12-22
After you installed libdvdread4 did you run.

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by tschill on 2013-12-22
Wow. I cleaned the lenses with a moist Q-tip and now it reads DVDs flawless. I don't understand why under Windows this problem didn't occur, but he! - it works. 
Thank you so much for your comment, coldraven.

---

