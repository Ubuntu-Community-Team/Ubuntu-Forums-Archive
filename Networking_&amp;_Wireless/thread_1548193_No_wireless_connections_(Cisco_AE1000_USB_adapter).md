---
title: "No wireless connections (Cisco AE1000 USB adapter)"
date: 2010-08-07
forum: Networking &amp; Wireless
---

### Post by xHellSilencerx on 2010-08-07
I'm running Ubuntu 32 bit OS on a 64 bit...Is this causing my inability to connect to any wireless ports or is it just my adapter?:(

---

### Post by varunendra on 2010-08-08
Just your adapter.

Please run the following commands in terminal (Applications>Accessories>Terminal) and post their output (copy-paste) here:
```
ifconfig -a
```
and
```
iwconfig
```

Remember to keep the pasted output within [code ] marks. (Highlight pasted text > click on # icon).

---

### Post by joebob8 on 2010-09-14
> **varunendra said:**
> Just your adapter.

Please run the following commands in terminal (Applications>Accessories>Terminal) and post their output (copy-paste) here:
```
ifconfig -a
```
and
```
iwconfig
```

Remember to keep the pasted output within [code ] marks. (Highlight pasted text > click on # icon).
Then what? I have the same USB adapter and it is plugged in but it does not show up on the list. The list shows wlan0 but that is my other wireless network device. Nothing happens when I plug in the AE1000 it does not show up on any list at all.

---

### Post by joebob8 on 2010-09-14
where can I find drivers?

---

### Post by joebob8 on 2010-09-16
I love finding answers to my own questions:) I followed the instructions in  this link and now my AE1000 works like a champ. Even though it says Fedora it works on Ubuntu, they even have an updated driver.

[http://forums.fedoraforum.org/showthread.php?p=1353558](http://forums.fedoraforum.org/showthread.php?p=1353558)

---

### Post by jdonbook86 on 2010-10-26
Does the Fedora fix work for Kubuntu. I fixed my Ubuntu, but it did not carry over to Kubuntu.

---

