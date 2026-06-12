---
title: "Mythbackend can't find /dev/video0"
date: 2009-11-28
forum: Multimedia Software
---

### Post by nasevz on 2009-11-28
I am using Mythtv Trunk(22905) on Karmic

Everytime I reboot the computer and try to watch TV from Mythfrontend, there is ERROR: mythtv is using all inputs but there are no active recordings
And in Mythbackend log:
Can't open video device, error "No such file or directory"
If I manually restart Mythbackend, Mythtv works normally.

Any idea how to solve the problem?
Is Mythbackend starting too early before video0 is created?

---

### Post by outleradam on 2009-11-28
> **nasevz said:**
> I am using Mythtv Trunk(22905) on Karmic

Everytime I reboot the computer and try to watch TV from Mythfrontend, there is ERROR: mythtv is using all inputs but there are no active recordings
And in Mythbackend log:
Can't open video device, error "No such file or directory"
If I manually restart Mythbackend, Mythtv works normally.

Any idea how to solve the problem?
Is Mythbackend starting too early before video0 is created?

sounds like you don't have drivers and firmware installed. check the myth wiki for your card.

---

### Post by nasevz on 2009-11-29
I will check again, but I guess it is not the problem because if I type "sudo restart mythtv-backend" in the console, TV starts working in Mythtv and everything is normal. Also Tvtime has no problem with TV card.

---

### Post by nasevz on 2009-11-29
New update from today (Trunk 22919) solved the problem.

---

