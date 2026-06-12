---
title: "No Sound After Update"
date: 2011-10-01
forum: Multimedia Software
---

### Post by Tonya_in_FL on 2011-10-01
I recently updated my kernel and now sound won't play. I booted an older kernel with grub and sound came back fine. So I think it's a kernel issue, but I wouldn't know how to report it on Launchpad. I made no other changes before sound was lost. 

Comp is a Dell Mini 9 Netbook. Running Ubu 10.04UNR.

---

### Post by Toz on 2011-10-07
Information on reporting audio bugs can be found towards the end of this article: [https://wiki.ubuntu.com/DebuggingSoundProblems]("https://wiki.ubuntu.com/DebuggingSoundProblems").

---

### Post by danellisuk on 2011-10-08
I've also just noticed that I've lost sound on my Dell Mini 9 with Ubuntu 10.04.

---

### Post by danellisuk on 2011-10-08
Found the fix for those who have lost sound on the Dell Mini 9 after the update to kernel 2.6.32-34.

Edit the file **alsa-base.conf** by running the following command:-

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

Add this line to the end of the file, save, and reboot

```
options snd-hda-intel model=dell
```

The launchpad bug is here;-

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/841308](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/841308)

---

### Post by Cowchip7 on 2011-10-29
I had the same problem. Thanks for the advise. I now have sound again!

---

### Post by neouser on 2011-11-16
Idem dito!
Thanks for this info! The audio on my Mini 9 is working again!

---

### Post by Tonya_in_FL on 2011-12-07
Thanks danellisuk! I have sound again without having to load previous kernels. :D I guess I don't need to add the bug to launchpad if they already know it's there.

---

### Post by danellisuk on 2011-12-08
Hi Tonya_in_FL, it's cool to hear when a post helps people, so thanks for the feedback.

I included a link to the bug, because a neat feature of launchpad is you can mark the bug as affecting you (in the upper left).  This allows developers to track how many people an issue affects, if an issue affects many people, it is more likely be fixed properly, so go ahead if you can.

Additionally, if you are interested, you can subscribe to the bug (right hand side) and receive updates about the progress of the bug.

---

