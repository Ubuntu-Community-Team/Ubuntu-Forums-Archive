---
title: "Need to create an audio CD from mp3s in 13.10"
date: 2013-10-30
forum: Multimedia Software
---

### Post by shochatd on 2013-10-30
I recently upgraded to 13.10 and tried to create an audio CD. The application I tried to use was Brasero, since I think that is the one I had used successfully before the upgrade. But it complains that it needs a plugin to decode mp3s. Is there some package I need to install? And by the way, the sticky post at the top of this forum is obsolete and should be deleted. It says to add medibuntu.org as a repository, but their website says it is defunct.

---

### Post by carl4926 on 2013-10-30
```
sudo apt-get install ubuntu-restricted-extras
```

you may want to check for and install : lame

---

### Post by shochatd on 2013-10-30
Thanks. ubuntu-restricted-extras got me past that error, but now when I select "Burn", and accept defaults, I just get "Normalizing tracks" with no progress. It just hangs there. I've tried on two computers (both running 13.10, unfortunately) and get the same results. I also tried a different blank CD-R in case there was a problem with that particular disk. I also tried running brasero from the command line, but there were no error messages. Maybe I should try k3b (but brasero worked before the upgrade).

---

### Post by shochatd on 2013-10-30
I installed k3b. This gave a similar error message about decoding mp3 but that was solved with libk3b6-extracodecs. With that installed, everything worked fine. Also, k3b seems to have a lot more colors, bells, whistles, levers and dials but I guess that's typical kde. I think I read while researching this problem that brasero may be deprecated. If that is true, what application replaces it for gnome or standard ubuntu? I started this effort by looking in the "Ubuntu Desktop Guide", but I did not find anything there about burning audio CDs.

---

### Post by carl4926 on 2013-10-30
Yes. I use k3b
I use kde more than Unity anyway

---

### Post by shochatd on 2013-10-30
Well, k3b certainly solved the problem for me, but I am curious whether anyone has successfully used brasero to burn an audio CD from mp3s under 13.10, since it failed for me the same way on 2 different computers. Wondering whether a bug needs to be written.

---

### Post by shochatd on 2013-10-30
The hang at "Normalizing tracks" appears to be a known problem:
[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/1176509](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/1176509)

---

### Post by Dennis N on 2013-10-30
Lubuntu 13.10 uses Xfburn. It works well. I have used that program to make quite a few audio cds.

---

