---
title: "mkisofs options for creating a windows readable DVD"
date: 2009-11-18
forum: Multimedia Software
---

### Post by cupabj on 2009-11-18
I use the mkisofs command for creating the .iso filesystem for DVD video. I have noticed that DVDs that I create using such .iso files work well on conventional DVD players as well as on my Ubuntu laptop. However, windows XP refuses to read them, reporting that it is an incompatible DVD. I have tried the "-R" and "-J" options and that hasn't helped. Can someone help me with the correct command line string for the mkisofs command to generate a windows-XP compatible file system? 

```
mkisofs -version
mkisofs 2.01 is not what you see here. This line is only a fake for too clever
GUIs and other frontend applications. In fact, this program is:
genisoimage 1.1.6 (Linux)
```

---

### Post by prshah on 2009-11-18
> **cupabj said:**
> windows XP refuses to read them, reporting that it is an incompatible DVD. I have tried the "-R" and "-J" options and that hasn't helped.

I use the following commands to create (data)DVDs that work fine in all systems, including divx players, Linux and XP:
```

genisoimage -o /home/user/cdrec/test.iso -J -log-file /home/user/cdrec/test.log -r -V TEST -v /home/user/cdrec/test/
growisofs -dvd-compat -speed=4 -Z /dev/dvdrw1=/home/user/cdrec/test.iso 

```

Maybe your ISO is being created correctly, but the burning program is not creating a Windows-readable DVD? Does your ISO load in Windows correctly? (You will need a Windows ISO loader for this).

Maybe some filenames have Windows-incompatible characters (Eg, ":"). 

Note that I'm talking about Data-only DVDs, so if you are making a movie-dvd, some or all of this may not be applicable to you.

---

### Post by cupabj on 2009-11-18
Thanks for your suggestions. I'll explore the options that you specified. However, I have been trying to make a movie DVD that is Windows compatible. It will be of great help if someone knows the exact set of options for mkisofs and growisofs for a movie DVD.

---

