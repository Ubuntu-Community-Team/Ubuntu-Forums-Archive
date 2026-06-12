---
title: "Constant Frontend Skipping"
date: 2008-07-03
forum: Mythbuntu
---

### Post by Mr_Chapendi on 2008-07-03
Meh.  2 threads on the front page.  Sorry, but I'm fairly sure they're unrelated so I felt it was appropriate.
Anyway.

I installed mythfrontend on my laptop to watch TV from my backend.  It seems to find it OK, but on playback I get video and sound for 3 - 4 seconds before both freeze, and then I get for another 3 - 4 seconds, and so forth.

```
will@fronzy:~$ apt-cache policy mythtv-common
mythtv-common:
  Installed: 0.21.0+fixes16838-0ubuntu3.1
  Candidate: 0.21.0+fixes16838-0ubuntu3.1
  Version table:
 *** 0.21.0+fixes16838-0ubuntu3.1 0
        500 http://us.archive.ubuntu.com hardy-updates/multiverse Packages
        100 /var/lib/dpkg/status
     0.21.0+fixes16838-0ubuntu3 0
        500 http://us.archive.ubuntu.com hardy/multiverse Packages
will@fronzy:~$ uname -r
2.6.24-19-generic

```

Frontend logs - [http://paste.ubuntu.com/24818/](http://paste.ubuntu.com/24818/)

There seem to be a lot of prebuffering timeouts - is this network related?

---

### Post by tgm4883 on 2008-07-04
A good way to test would be to plug your laptop into the network and test.

But if I had to guess, I would say yes.

---

### Post by smbm on 2008-07-07
I was getting some broadly similar symptoms on my (non dedicated front end) laptop.

I traced it back to forgetting to turn off desktop effects (as I had just installed Hardy and they were enabled by default) and they were sapping all the cycles they could out of my poor machine.

---

