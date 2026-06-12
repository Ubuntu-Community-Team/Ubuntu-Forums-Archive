---
title: "Rhythmbox: &quot;Unable to find or create trash directory&quot;"
date: 2008-06-17
forum: Multimedia Software
---

### Post by vancouverite on 2008-06-17
Hello Ubuntu gurus!
Ever since I upgraded to Hardy, Rhythmbox has not let me delete files directly from the browser.  Whenever I try I get the error "Unable to find or create trash directory".

Rhythmbox 0.11.5
Music location: separate vfat partition with umask=000

I have tried to fix this in a few of ways:
1) created a folder ".Trash-[user]" and gave it permissions 777 - Didn't work
2) Deleted the folder ~/.gnome2/rhythmbox - Didn't work
3) Formatted and reinstalled Hardy from scratch, but kept the same home folder (it's on a separate partition) and again deleted ~/.gnome2/rhythmbox - Didn't work

Other users have had this same problem and posted it on launchpad:

[https://answers.launchpad.net/ubuntu/+source/rhythmbox/+question/30944](https://answers.launchpad.net/ubuntu/+source/rhythmbox/+question/30944)

I tried to get some attention for this by creating a bug report, but it remains undecided 10 days after I reported it.

[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/238273](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/238273)

Can anyone help?

Thank you for your time,
van

---

### Post by fleamour on 2009-08-10
Does this have a fix yet?  I get same error but music is on Xubuntu partition & not a seperate vfat partition.

---

### Post by fleamour on 2009-08-11
Seems to solve itself after a reboot.

---

