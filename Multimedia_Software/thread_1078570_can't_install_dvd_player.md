---
title: "can't install dvd player"
date: 2009-02-23
forum: Multimedia Software
---

### Post by krishnasol on 2009-02-23
Hi every body; I'm very new in Linux (ubuntu) and I can't install a dvd Player in my computer. Any suggestion?
Thanks,
krishnasol

---

### Post by SuperSonic4 on 2009-02-23
Do you mean hardware or software? Hardware is just physically insert it, attach the power and the sata/ide cable and reboot.

Software can be any number of things, VLC and MPlayer are considered two of the best in ubuntu. Check out the Multimedia and Video sticky in that forum

---

### Post by krishnasol on 2009-02-24
Hi, thanks for the answer. Is the software the problem. I Download already the software VLC but Just don't happen nothing when I try to open the dvd with these software. With Totem can not open neither.
Thank you again.
krishna

---

### Post by tombom62 on 2009-02-24
i had this problem a little while back.  you are right to use vlc, it rocks!  Take a look at my thread,
[http://ubuntuforums.org/showthread.php?t=1057114](http://ubuntuforums.org/showthread.php?t=1057114)
(2nd post)

hope this helps:guitar::popcorn:

---

### Post by binbash on 2009-02-24
also install libdvdcss2 and libdvdcss3 and libdvdnav

---

### Post by Therion on 2009-02-24
Open a Terminal and cut and paste the following into it:

```
sudo apt-get install libdvdcss2 libdvdcss3 libdvdnav
``````
sudo apt-get install ubuntu-restricted-extras
```

---

