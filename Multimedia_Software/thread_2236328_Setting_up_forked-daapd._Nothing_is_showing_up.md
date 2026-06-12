---
title: "Setting up forked-daapd. Nothing is showing up?"
date: 2014-07-26
forum: Multimedia Software
---

### Post by rossguil on 2014-07-26
Hello everyone!

I am having some trouble setting up forked-daapd on my ubuntu server (Ubuntu 14.04). I installed it from the official repositories
```
sudo apt-get install forked-daapd
```
And changed the config file to point to a specific directory for test purposes (my whole music library is not yet ready to scan as I still need to update some tags). The directory contains 3 cd's.

I can see the share through iTunes, but when I click on it, it just spins until it times out and gets back to the computer's library. Anything I can do to debug this? I have already set the log level to "spam" in order to see something but it is not really helpful...

The only "clue" I have from the log file is this line, that seems to be repeated quite a lot:
```
[2014-07-26 00:11:27]       db: DB pool status: size 2 free 2
```

Thanks a bunch!

P.S.: I will let it run for a while, in order to get as much info from the log as possible

---

### Post by rossguil on 2014-07-31
*bump*
Anyone? Nobody has experience with forked-daapd?

---

