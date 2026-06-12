---
title: "Resoltion messed up after intel Xorg update"
date: 2009-10-18
forum: Multimedia Software
---

### Post by Redundant Username on 2009-10-18
After an Intel driver update I don't have the 1440x900 resolution anymore and I can't use Compiz or Emerald. Can someone help me?

---

### Post by I_Like_Pie on 2009-10-18
I am having the same problem...Suxxor

---

### Post by I_Like_Pie on 2009-10-18
They screwed up the latest intel drivers so that the resolution is set by the kernal rather than the user...somehow it can not properly detect resolutions.

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+sourcepub/613936/+listing-archive-extra]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/613936/+listing-archive-extra")
Above is a list of the intel drivers that I was using....2.9 was causing the problem...2.7 reverted fixed it.  Make sure you get the driver and not the debug package. 

If this fixes it...lock it in the repository so that you don't have the problem again.  Keep it that way for a while until you update to the new distro or they work out the bugs in sourceforge.

---

### Post by sandy8925 on 2009-10-19
Yeah I'm having the same problems too. Glad to know I can fix it. My card's an Intel 915 GM. I had done the Jaunty Intel Graphics Performance Guide
 optimal config a few months so I was wondering whether that was the problem.

---

### Post by tormod on 2009-10-19
See [http://ubuntuforums.org/showpost.php?p=8128446&postcount=1236](http://ubuntuforums.org/showpost.php?p=8128446&postcount=1236)

---

