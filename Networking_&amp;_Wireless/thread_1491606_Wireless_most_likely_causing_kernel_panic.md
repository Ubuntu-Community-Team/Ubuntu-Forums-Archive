---
title: "Wireless most likely causing kernel panic"
date: 2010-05-23
forum: Networking &amp; Wireless
---

### Post by berutten on 2010-05-23
Hi. I am experiencing kernel panics in 10.04 and I was wondering if someone else was having the same problem. I am 99% sure it is related to the wireless.

When using the wifi, I can go for anywhere from 10 minutes to an hour with no problem, then my machine with freeze (caps lock blinking). Using a wired network it has been running for days with no hangs.

I am running a thinkpad t61p AMD64 (latest kernel) with the ath5k driver for my AR5212 chip. I had this problem in 9.04 and installing backports fixed it. I installed backports in 10.04 but it has no effect. Unfortunately I have not been able to grab any output from the kernel panic.

Any suggestions?  This is making my machine pretty unusable with wifi.

Thanks!

---

### Post by berutten on 2010-05-24
Wow, lots of wireless problems in 10.04 push this down very quick. Nobody else having problems with ath5k or thinkpads in 10.04?

---

### Post by linuxd00 on 2010-05-29
is it related to my problem?

[http://ubuntuforums.org/showthread.php?t=1495857](http://ubuntuforums.org/showthread.php?t=1495857)

and have you found any solutions? :(

---

### Post by berutten on 2010-05-29
I wouldn't say its the same problem. Mine is a hard freeze, and I  have to reboot the system and it comes on suddenly.

However, its clear there are problem with the ath5k driver in 10.04. The workaround I have been using is switching the kernel to 2.6.31-21. That seems to fix the problem, though it is not my ideal solution.

There is now a bug for it: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/581284](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/581284)

> **linuxd00 said:**
> is it related to my problem?

[http://ubuntuforums.org/showthread.php?t=1495857](http://ubuntuforums.org/showthread.php?t=1495857)

and have you found any solutions? :(

---

### Post by linuxd00 on 2010-05-30
i solved my problem by switching to the far better madwifi driver.. you should try it! instructions in my thread

---

### Post by berutten on 2010-05-31
> **linuxd00 said:**
> i solved my problem by switching to the far better madwifi driver.. you should try it! instructions in my thread

Thanks will give that a try, though on 9.04 madwifi also gave me kernel panics :)

---

### Post by insert_name_here on 2010-06-01
I've got the same problem, berutten. Thinkpad T60, with the AR5212 and 2.6.34 rc7.

Did madwifi work for you?

---

### Post by berutten on 2010-06-02
> **insert_name_here said:**
> I've got the same problem, berutten. Thinkpad T60, with the AR5212 and 2.6.34 rc7.

Did madwifi work for you?

I haven't had a chance to try. Will try to do it this weekend.

---

