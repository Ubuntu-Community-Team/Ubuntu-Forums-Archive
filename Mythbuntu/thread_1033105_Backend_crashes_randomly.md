---
title: "Backend crashes randomly"
date: 2009-01-07
forum: Mythbuntu
---

### Post by jablack on 2009-01-07
This is a clean install of 8.10. I followed the instructions from MythTV documents on upgrading to new hardware (Moving tables in the database and such). Anyway the system is stable until someone starts using the local frontend, and then it just starts crashing after that.

I found this in dmesg:

Jan  6 19:38:58 thunder kernel: [ 3292.765070] mythfrontend.re[8784]: segfault at 7b0ba00c ip b5dc7c92 sp ab8fced0 error 4 in libc-2.8.90.so[b5d58000+158000]

Jan  6 19:39:17 thunder kernel: [ 3311.810254] mythbackend[5769]: segfault at 0 ip 0806c642 sp bfd18a30 error 4 in mythbackend[8048000+118000]

Jan  6 21:18:21 thunder kernel: [ 9255.264538] mythbackend[9264]: segfault at 28 ip 0806c642 sp bf84aa30 error 4 in mythbackend[8048000+118000]

The last was after we just let it sit for a while. I've run mprime and memtest86+ on the system and I cannot find any problems with it. I've also attached a copy of the backtrace as well. The odd thing it the time doesn't match on the backtrace. Syslog shows the segfault at 19:38-19:40. In the mythbackend.log the backtrace comes in between 18:40 and 18:44. Odd things.

ANY HELP is much appreciated. THANK YOU.

---

### Post by dust79 on 2009-01-09
Since two days ago my frontend crashes with same error message when going to "Watch recording" or "Delete recordings" in menu.

Also using 8.10 and I think this broke when upgrading some package.

Jan  8 21:52:04 arc6 kernel: [22064.871179] mythfrontend[32155]: segfault at 0 ip b5d36b56 sp ad0eec18 error 4 in libc-2.8.90.so[b5cbe000+158000]

//Filip

---

### Post by dust79 on 2009-01-11
I solved my problem with command "aptitude reinstall libc-dev"

---

### Post by Cappientes on 2009-01-15
I'm also getting to the same using Mythbuntu 8.10.

I've just tried reinstalling lic-dev so we'll see if that fixes it - will report back when I know!

---

### Post by Cappientes on 2009-01-20
> **Cappientes said:**
> I'm also getting to the same using Mythbuntu 8.10.

I've just tried reinstalling libc-dev so we'll see if that fixes it - will report back when I know!

Hmm no luck. Still crashing almost nightly.

The only error I can find is something similar to:

mythbackend[]: segfault at 6 ip b5d49412 sp b44e1810 error 4 in libc-2.8.90.so[]

Strange.

---

