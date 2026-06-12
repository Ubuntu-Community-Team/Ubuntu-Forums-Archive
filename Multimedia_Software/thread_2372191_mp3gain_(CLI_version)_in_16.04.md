---
title: "mp3gain (CLI version) in 16.04"
date: 2017-09-22
forum: Multimedia Software
---

### Post by kazakore on 2017-09-22
I've used mp3gain for a long time, I believe in my last install I manually installed as it is gone from the 16.04 repos, or so it would seem.

New laptop, new install, looking again and no mp3gain when I run the relevant apt-get command. Search the repos and it says Xenial does have the GUI version, easymp3gain, so I install this hoping the original mp3gain would be in there as a back end. Strangely when install all the components (even though for what I hoped would happen should have only needed -data...)
 
```
$ sudo apt-get install easymp3gain-*
...
Reading package lists... Done
Building dependency tree       
.
.
.
Suggested packages:
  mp3gain
.
.
.
$ sudo apt-get install mp3gain
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mp3gain is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'mp3gain' has no installation candidate

```

(Snipped to show only important bits.)


So why does it suggest a package that it isn't possible to install???



On a different note I couldn't paste directly from xterm into this window, I had to open a text editor (Gedit) and paste into there, then copy and paste again. Is that a fault with this forum or with Opera?

---

### Post by ajgreeny on 2017-09-22
I had the same problem and did not find the GUI version as useful as the cli version that I was used to using.

However I found a PPA with that and aacgain that you might find useful at [https://launchpad.net/~flexiondotorg/+archive/ubuntu/audio](https://launchpad.net/~flexiondotorg/+archive/ubuntu/audio)
I've used it quite a lot, along with the other apps from that suite, if that's the correct description of them, ie mp3splt and mp3wrap, but tyhose are in the standard repos.

---

### Post by nik.charles on 2017-10-09
mp3gain got dropped by all ubuntu distributions because it was dropped upstream by debian.

packages from the additional repository linked in previous post work well

There are 2 front end gui packages. easymp3gain and qtgain. both need mp3gain to work with mp3 files, but it is an optional dependency, not a hard requirement

---

