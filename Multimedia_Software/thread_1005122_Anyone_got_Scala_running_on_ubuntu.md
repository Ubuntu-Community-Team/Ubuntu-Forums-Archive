---
title: "Anyone got Scala running on ubuntu?"
date: 2008-12-07
forum: Multimedia Software
---

### Post by Endolith on 2008-12-07
*Since I can't contribute to [this thread]("http://ubuntuforums.org/showthread.php?t=381274"), I created another with the same name.*

> **Smbrandes said:**
> The install instructions are somewhat vague.Agreed.  

> Placing the libgtkada-2.8.so.0 in the /usr/local/lib was the first obstacle to be overcome.That's all I had to do to get it to work:

```
cp libgtkada-2.8.so.0 /usr/local/lib/
sudo ldconfig

```/etc/ld.so.conf.d/libc.conf already contains an include for that directory?:
```
# libc default configuration
/usr/local/lib

```I have no idea what any of this means, but the program runs now.

> However, it mentions the libgnarl-4.1.so.1 and another dependency and something about setting the ldconfig. itrided placing the libgnat and libgnarl in the same spot as the libgtkada with no result? I am stumped. Still days away from mean tone.Mine just worked after moving the one file and redoing ldconfig.  I already had the package libgnat-4.1 installed, though, as it says in the INSTALL file.

> Now the question is how on earth to get it to run with Jack ready applications?Did you figure this out?

---

### Post by Smbrandes on 2008-12-31
Scala and I never became friends with Jack. However, I did discover that Zynaddsubsynth has a function for importing .scl files used by Scala. And also Aoelus can also be retuned to common temperaments, That was a sufficient work around to just play round with the non standard tunings. Also there is an App called Myorgan which is windows based thing that uses actual sound samples that can be retuned using bat files. Unfortunately that is somewhat cumbersome, but it can be run under wine although it tends to cause a slightly more annoying lag than the other applications. Of course the asnswer to that is to listen to the keyboard as you are playing and mute the computer speakers. Which means listening to the product afterwards which can be a little strange. I may again try to run scala in the future but right now it is not really a necessity.

---

