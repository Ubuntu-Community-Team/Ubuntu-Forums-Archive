---
title: "i cant upgrade to alpha no update"
date: 2010-12-16
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by barah on 2010-12-16
i do like the sticky topic and give me the terminal that
0 upgrade ,0 new installed,0 to remove and 0 to upgrade
ihave 10.10 and i want to try 11.04

---

### Post by seenthelite on 2010-12-16
Not sure what your question is, but this may be the answer 

```
sudo update-manager -d
```

---

### Post by efflandt on 2010-12-16
Initially I tried "upgrade by replacing all instances of "maverick" in your /etc/apt/sources.list with "natty", and issuing...", but ran into dependency issues, so I then used daily build on USB to do regular fresh install to usb flash and updates. When alpha1 come out, I installed to SSD and have been doing updates from there (because updates on cheap usb flash were way too slow).

Although, I have also been trying Kubuntu natty "installed" on 8 GB USB flash (not just iso).

So if upgrading to natty does not work, do you have drive space (or partition) where you can do a fresh install from alpha1 or a daily iso?

There will be some issues that crop up, but if everything just worked, the developers would not know what is broken for certain hardware.

---

### Post by cariboo on 2010-12-16
I really wouldn't advise updating your main system to Natty yet, but if you want to go ahead, and chance being without a working system occasionally, create a bootable usb stick, and when it comes to the partitioning section, chose manual partition, mark your / and if you've got a separate /home partition to be used, but not formatted, this way your current version will be replaced, but nothing else, /home for example will be touched.

---

