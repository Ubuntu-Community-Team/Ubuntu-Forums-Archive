---
title: "Problem with audio from TV tuners (mythtv)"
date: 2007-04-23
forum: Multimedia &amp; Video
---

### Post by ddover on 2007-04-23
Here is the setup:

Ubuntu Fiesty Fawn 7.04
PCHDTV-5500
Mythtv .20

Sound works fine in apps other than mythtv. In myth watching recording and videos works fine. the problem comes when I try to watch live tv. The sound does not sync and it won't stop after switching out of live tv. However, when switching channels I do get the correct audio feed although not synced. Any help would be appreciated.

---

### Post by ddover on 2007-04-23
adding more details of system...

---

### Post by ddover on 2007-04-24
bump...

---

### Post by MrNobody on 2007-04-25
I have the same problem, but with ubuntu 6.10
Any idea to fix it?

---

### Post by jubxie on 2007-04-28
I have a similar problem with:

opteron 165 dual core,
1gig RAM
pchdtv 5500
nvidia 6200tc
shuttle case/mb
integrated intel sound
ubuntu 6.10
mythtv .20

My sound, when working, is fine, however, when I reboot, it often(66% of the time) does not pickup my intel sound card(not shown w/ cat /proc/asound/cards). It only sees the conexent or something from the pchdtv card. I did this: 

```
less /proc/asound/modules
```

replace:

```
install sound-slot-0 modprobe snd-card-0
install sound-slot-1 modprobe snd-card-1
```

with:
```

install sound-slot-0 modprobe snd_intel8x0
install sound-slot-1 modprobe “second card”
```

It didn't seem to help except when both cards are seen, the intel one is always used and the sound works. Literally 2/3 of my reboots ignore the intel card. I have just avoided rebooting, but if anyone knows how to force the intel card at boot with a script or something.....

---

