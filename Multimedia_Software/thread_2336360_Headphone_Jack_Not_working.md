---
title: "Headphone Jack Not working"
date: 2016-09-07
forum: Multimedia Software
---

### Post by zhouhenry on 2016-09-07
I have just installed Ubuntu on my Alienware 15. Everything works just fine except for the headphone jack which is driving me crazy. The internal speaker from the laptop works out perfectly. But when I plug in my speaker, it just doesn't work. Nothing is even shown in settings/hardware/sound sections. It just doesn't recognize my device.

I have read some of the postings on this forum and has gotten this link as some sort of the system configuration file.

[https://ubuntuforums.org/newthread.php?do=newthread&f=334](https://ubuntuforums.org/newthread.php?do=newthread&f=334)

Can someone please give me any idea on how to debug my problem? Thank you in advance!

---

### Post by Yellow Pasque on 2016-09-09
Run alsamixer :
```
alsamixer
```

Scroll over to the two options named HP/Speak and press 'm' to enable them. Someone with the original Alienware 15 verified this fix, but apparently, it doesn't work on Alienware 15 R2, even though it uses the same Creative CA0132 codec:
[http://www.linuxquestions.org/questions/linux-hardware-18/sound-does-not-switch-to-headphones-after-plugging-jack-on-alienware-15-a-4175587808/page2.html#post5600912](http://www.linuxquestions.org/questions/linux-hardware-18/sound-does-not-switch-to-headphones-after-plugging-jack-on-alienware-15-a-4175587808/page2.html#post5600912)

---

