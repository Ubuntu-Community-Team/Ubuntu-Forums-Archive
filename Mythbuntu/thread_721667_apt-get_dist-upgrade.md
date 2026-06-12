---
title: "apt-get dist-upgrade"
date: 2008-03-11
forum: Mythbuntu
---

### Post by bjorn_b on 2008-03-11
I just made a apt-get dist-upgrade which made my mythbuntu break!

The mythbackend is not installed anymore, if I try to install mythtv (ap-get install mythtv) it complains about:
The following packages have unmet dependencies:
  mythtv: Depends: mythtv-backend (= 0.21.0-0ubuntu2~gutsy1) but it is not going to be installed

How do I fix this urgent matter?! I use mythbuntu 7.10 at the latest level (now it seems it's a bit to faar ahead!).

My wife is on me with a blowtorch....

//Björn

---

### Post by gareththered on 2008-03-11
Hi,

I've just had a similar problem upgrading my Mythbuntu 7.10 box, and the advice I was given worked!

Read [here]("http://ubuntuforums.org/showthread.php?t=721656") to find out how to fix it.

Also, be aware that during unistalling MythTV 0.20 my box wanted to delete folders within '/var/lib/mythtv' which includede all my music etc.  I have this as a separate drive mounted on '/var/lib/mythtv' so I unmounted this drive before continuing.  I don't know if it would have wiped my collection, but better safe than sorry!!

---

