---
title: "There was an Update and my USB wifi won't work."
date: 2013-02-02
forum: Networking &amp; Wireless
---

### Post by tahdas on 2013-02-02
I tried the guide I used before when this happened but its not working. Please help! This is the guide I used [http://ubuntuforums.org/showpost.php?p=12318056&postcount=2.?](http://ubuntuforums.org/showpost.php?p=12318056&postcount=2.?).
Thanks!
Tahdas

---

### Post by ahallubuntu on 2013-02-02
~

---

### Post by chili555 on 2013-02-02
You'll probably need to rebuild for what I assume is a newer kernel version:```
cd ~/Downloads
cd (NEWDIRECTORY_CREATED)
sudo ./install.sh
```Whenever a new kernel is installed, repeat.

---

### Post by tahdas on 2013-02-02
How do I figure out what I put after cd?

---

### Post by chili555 on 2013-02-02
Where did you download the file originally? Downloads? Look in that folder and see if it's there. What is it named? RTLsomething? Then do:```
cd Downloads/RTLwhateveritscalled
```And then proceed.

---

### Post by tahdas on 2013-02-02
It's working. Thanks! Your comand didn't work so I unzipped it again, copy and pasted the name at the end, then said "cd (the code), then I chmoded and sudoed and it worked!

Thanks again!
Tahdas

---

