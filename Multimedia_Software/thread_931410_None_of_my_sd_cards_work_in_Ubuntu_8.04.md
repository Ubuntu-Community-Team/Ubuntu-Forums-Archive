---
title: "None of my sd cards work in Ubuntu 8.04"
date: 2008-09-27
forum: Multimedia Software
---

### Post by MPD on 2008-09-27
Hey there folks, I have a question.
I have several sd cards (2-1G,1-2G and 1-8G). I had 1 working  and then tried to get all them working. 1st let me say I am very new (after losing everything on 2 laptops running xp), Now when I enter them I get this
 "The volume '1GIGCARD' uses the $ mkdosfs /dev/mmcda file system which is not supported by your system."
I have no idea what I did or how to fix it.Please,I am trying to get the hang of it and just need some info. Remember I'm very new. Also,As stated I have always used XP and tried this Ubuntu 8.04 out and liked it.Is this the right distro for me and my family? I had to set it up and install all the programs that I use. (Looking for options)? Thanks so much, Mike

---

### Post by cyran on 2008-09-27
First, do you have anything on your SD card that you need to save? Because one of the ways to fix this, reformatting it, deletes everything on it.

Try opening "System -> Administration -> Partition Editor" with the SD card plugged in. In the upper right, where it says /dev/something, click and select /dev/mmc(something). What shows up?

---

