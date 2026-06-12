---
title: "Fatal1ty USB headset not working"
date: 2009-06-15
forum: Multimedia Software
---

### Post by methulz on 2009-06-15
I just bought a new fatal1ty usb headset, and it's not working with jaunty, i can't get any sound from wine or flash or anything except pidgin it seems.

[dmesg output shortly after headset was inserted]("http://pastebin.com/m23cc59dc")

fin the dmesg is seems that the error 

```
2:1:1: cannot get freq at ep 0x4
```keeps repeating, but only if I let the headset stay connected to the laptop.

My laptop is an Acer aspire 5920G running Ubuntu 9.04.

Any help would be appreciated thanks.

---

### Post by methulz on 2009-06-15
Bump

---

### Post by methulz on 2009-06-16
BUMP damnit.

---

### Post by methulz on 2009-06-16
Bump.

---

### Post by kostkon on 2009-06-16
> **methulz said:**
> i can't get any sound from wine or flash or anything except pidgin it seems.
Then it seems that it's working OK.

Have you installed the *PulseAudio Device Chooser* utility? This will allow you to set a default output device in your system (it may well be your headset, if you want) or just easily send the audio stream of an application from your speakers to your headset on-the-fly and some other things.

For more info check [this thread here]("http://ubuntuforums.org/showthread.php?t=1130384").

---

