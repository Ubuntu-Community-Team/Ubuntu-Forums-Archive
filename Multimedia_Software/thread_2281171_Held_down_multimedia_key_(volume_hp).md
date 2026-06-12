---
title: "Held down multimedia key (volume hp)"
date: 2015-06-04
forum: Multimedia Software
---

### Post by eliasmtz on 2015-06-04
Hellos everybody!
When I try to raise/decrease volume with my multimedia keys, my pc enters in freeze mode and I can't to do click elsewhere.
I have after to regulate again the volumen until that isn't blinking.

Linux ELIAS-PC 3.16.0-38-generic #52~14.04.1-Ubuntu SMP Fri May 8 09:43:57 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
HP dv3506la

Demo vid: [http://youtu.be/PkAYVCjsD5U](http://youtu.be/PkAYVCjsD5U)
Xev info: [http://pastebin.com/W1aBHLjZ](http://pastebin.com/W1aBHLjZ)

**Sorry my english everybody. Thanks in advance!**

---

### Post by eliasmtz on 2015-06-07
I can to find the same issue in another page... is a bug in the system,  the multimedia keys is not realeased.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/311353](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/311353)

---

### Post by tgalati4 on 2015-06-08
Welcome to the forums.

So, *xev* is showing that the correct key mapping (XF86AudioRaiseVolume) is happening--both key presses and key releases.  Unfortunately, the xinput key definition (XF86AudioRaiseVolume) is grabbed by a lot of applications so sometimes there is a conflict.  According to your video, it appears to be a conflict with the desktop environment/window manager (which appears to be Unity).

Perhaps boot another version of Ubuntu (such as Xubuntu) using a LiveUSB and see if the volume keys work correctly.  That might narrow down the problem.

---

### Post by eliasmtz on 2015-06-11
Is same problem, I tried in Xubuntu and Kubuntu.
Thanks for your response.

---

