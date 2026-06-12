---
title: "No sound - integrated Intel MCP51 AC97"
date: 2008-03-23
forum: Multimedia &amp; Video
---

### Post by curtis1552 on 2008-03-23
I have followed the comprehensive sound problems sticky guide, but it still doesn't work.

I would appreciate any help.

Here are edited lists of what I have run. I will update this post as I go as well as the continuing posts.
```

$ lspci
00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)

```
```

$ aplay -l
card 0: ICH [Intel ICH], device 0: Intel ICH [Intel ICH]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH [Intel ICH], device 2: Intel ICH - IEC958 [Intel ICH - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
```

$ sudo modprobe snd-intel8x0

```

Computer Specs:
Mobo:Foxconn C51GU01(this is from a Gateway GT5028)
CPU: AMD X2 3800+
RAM: 1.5gb (generic)
Video: Nvidia 6600gt
OS: Ubuntu 7.10

---

### Post by curtis1552 on 2008-03-25
bumpage because i still can't get it to work.

---

### Post by superprash2003 on 2008-03-26
try this [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by wolfen69 on 2008-03-26
you're using ubuntu 5.10? hmmm. :confused: anyway, try this: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by curtis1552 on 2008-03-27
I'm using 7.10,
Changing the sound settings isn't working, but I'll keep trying.
Adding more info about my computer to the 1st thread.

Mobo:Foxconn C51GU01(this is from a Gateway GT5028)
CPU: AMD X2 3800+
RAM: 1.5gb (generic)
Video: Nvidia 6600gt
OS: Ubuntu 7.10

---

### Post by curtis1552 on 2008-03-30
Bumpage, because this has been driving me nuts for the last four months.

---

