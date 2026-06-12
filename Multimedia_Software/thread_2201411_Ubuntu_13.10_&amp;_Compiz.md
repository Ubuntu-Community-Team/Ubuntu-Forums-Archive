---
title: "Ubuntu 13.10 &amp; Compiz"
date: 2014-01-24
forum: Multimedia Software
---

### Post by nibal on 2014-01-24
I just installed Ubuntu 13.10 x64. Until yesterday I had 12.04 LTS x64, but due to incompatibility with libboost had to change. It is a pity to have your flagship 12.04 using such a bad libboost version :-(

Anyway, to the problem at hand. Installed all updates. When I start ccsm, it gives me half the configuration options from 12.04. No cubes, cylinders, etc. Also when I set my desktop to size 8 or 4, absolutely essential for my work, it just gives me 1 desktop :-(. It also hangs and send in a error report. 

Is compiz any better in 13.04?

TIA,
Nikos

---

### Post by mikewhatever on 2014-01-24
I suspect you might be misusing the words "bad" and better.
Well, here is [your answer anyway]("http://askubuntu.com/questions/34572/how-can-i-reduce-or-increase-the-number-of-workspaces-in-unity") - thank you Google.

---

### Post by nibal on 2014-01-24
> **mikewhatever said:**
> I suspect you might be misusing the words "bad" and better.
Well, here is [your answer anyway]("http://askubuntu.com/questions/34572/how-can-i-reduce-or-increase-the-number-of-workspaces-in-unity") - thank you Google.

I actually didn't. It costed me ~1mo of working hard 80 hrs/week before discovering the issue. Much of the software that I use, refuses to build because of incompatible libboost version except that it doesn't report it at build (older software). The hallmark of open source is backwards-compatibility, so that it doesn't hang existing users up to dry. libboost decided to forgo it. And Ubundu went along. If I were able to update libboost, I would have no problem, but I would loose window environment since unity & compiz depend on that particular version of libboost.

Thank you so much for the link.
Nikos

---

### Post by mikewhatever on 2014-01-24
Perhaps you should file a bug report, and ask to update libboost. That said, Ubuntu (same as most distros) doesn't have the latest software.

---

### Post by nibal on 2014-01-24
> **mikewhatever said:**
> Perhaps you should file a bug report, and ask to update libboost. That said, Ubuntu (same as most distros) doesn't have the latest software.

I actually asked in another thread "libboost 1.46 blues" in installation, if i could do anything about it, and didn't get any replies. I installed new libboost from sources in /usr/local/lib, but wasn'r enough to build gnuradio. 
Of all the Ubuntu distros, 11.x, 13.x, etc. 12.04 is the only one that doesn't have a  gnuradio package. Unfortunately, when unity and compiz depend on that particular version of libboost, and a lot more packages depend on unity,
you end up rebuilding the whole distro again.:(

---

### Post by mikewhatever on 2014-01-24
Well, staying with an LTS has its advantages and disadvantages: the former are stability and long term support, the latter - you use mostly outdated software. Apparently, 12.04 doesn't work all that well for you, so why not switch to the latest stable 13.10?
Libboost [in Saucy is 1.53]("http://packages.ubuntu.com/search?suite=precise&searchon=names&keywords=libboost") as opposed to 1.48 in Precise.

---

### Post by nibal on 2014-01-24
> **mikewhatever said:**
> Well, staying with an LTS has its advantages and disadvantages: the former are stability and long term support, the latter - you use mostly outdated software. Apparently, 12.04 doesn't work all that well for you, so why not switch to the latest stable 13.10?
Libboost [in Saucy is 1.53]("http://packages.ubuntu.com/search?suite=precise&searchon=names&keywords=libboost") as opposed to 1.48 in Precise.

Yeap. that's exactly what I did. This thread is marked "Ubuntu 13.10 & Compiz" ;-) I wish only it didnt't have to take me 1 month before realizing I couldn't stay with 12.04 :-(

---

### Post by buzzingrobot on 2014-01-24
It is not appropriate to look to an LTS release for the newest releases of a library.

CCSM is not a core Ubuntu component and users are typically, and widely, counseled that its use often triggers problems.

---

### Post by nibal on 2014-01-24
> **buzzingrobot said:**
> It is not appropriate to look to an LTS release for the newest releases of a library.

CCSM is not a core Ubuntu component and users are typically, and widely, counseled that its use often triggers problems.

I didn't ask for the latest release of *any* library. Just a working one of libboost. When smt is faulty and the release is supported (like 12.04 LTS is) there should be a patch.
Backwards-compatibility is the hallmark of open source.
I have used CCSM for a long time, without *any* problems. It is not part of Ubuntu, but ubuntu has integrated and developed for compiz for a long time.

Please do not pursue this thread any longer. It is marked "SOLVED".

Nikos

---

