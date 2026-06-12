---
title: "A couple of problems with Audex under gnome"
date: 2010-08-23
forum: Multimedia Software
---

### Post by BoundaryValueProblems on 2010-08-23
Hello.
I have been enjoying audex, a nice KDE-based CD ripper program under 32bit Lucid, and gnome interface. I have two questions, however:

(1) audex help does not work. First when I clicked the help for Audex Handbook.  But it said: the program "khelpcenter" does not exist, probably because I am using gnome, not KDE.  So, I installed khelpcenter4.
Now, when I click the help, Audex Handbook, it says:
The file or folder help:/audex/index.html does not exist.
Just in case, after I installed khelpcenter4, I reinstalled audex.
But I still have this problem: I still cannot reach to Audex Handbook.
I am wondering how to solve this problem under gnome.
(I am not sure whether this works under KDE, though.)

(2) There is an option to create a playlist (e.g., .m3u file) in the target folder.  I would like to create such a playlist in the grandparent directory, which was the case when I used "grip".  Can I control the playlist directory?

Thanks a lot for your help!

---

### Post by jcoles on 2011-06-03
On my system, there's also are also the problems that,

- Right-click on a CD, Open with Audex doesn't work.
- Creating a new profile in Audex crashes.
- Ripping to WAV format from a USB-connected CD is slow (USB 1.0?)

On the other hand, Audex is the only multimedia program that has functioning CDDB for CDs.

I upgraded from 10.10 through Update Manager. Perhaps a fresh install would do better.

---

### Post by Graham C Williams on 2011-06-16
I have a installation of 11.04 64bit on an Aspire 8935g and get much the same problems. Agreed, Audex is one of the best when it works. whether the operating system is 32bit or 64bit makes no difference, it will always crash when trying to find the codex. It misses the Codex all together when I know they are loaded. See I use Flac for my player, the kids use mpeg and other 'orrible methods. Oh, it cannot find the drive (whatever that means in this context). Perhaps I've missed a dependency but all the KDE tools seem to be in. As I've said I've tried it 32 bit as well. what is wrong with Audex?

---

### Post by Yellow Pasque on 2011-06-17
I haven't tried it lately, but Audex has been crashing on my Debian sid install for a long time when trying to create the flac profile.

EDIT: Actually, I just checked it again and it works (v 0.72 beta1).

---

### Post by Graham C Williams on 2012-01-07
I Know we are going back a bit here but I've found Audex 0.74b and that works perfectly. G.

---

### Post by Graham C Williams on 2012-01-07
I Know we are going back a bit here but I've found Audex 0.74b1 deb and that works perfectly. G.

---

### Post by MoreOrLess on 2012-01-07
0.74 fixes the crashes, and there is also a workaround here for older versions: [https://bugs.launchpad.net/ubuntu/+source/audex/+bug/614895](https://bugs.launchpad.net/ubuntu/+source/audex/+bug/614895)

---

