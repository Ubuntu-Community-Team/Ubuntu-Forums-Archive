---
title: "Can't get Hauppauge HVR-1700 to work"
date: 2008-05-26
forum: Multimedia Software
---

### Post by elbekko on 2008-05-26
Hello all,

I have a Hauppauge HVR-1700 analog/digital hybrid TV card. It works fine under Vista, and now I'd like to get it to work on Ubuntu 8.04.

I've followed the instructions in this post: [http://ubuntuforums.org/showpost.php?p=4914835&postcount=8](http://ubuntuforums.org/showpost.php?p=4914835&postcount=8)
But that didn't work, sadly enough. Modprobe shows no errors when loading cx23885, but /dev/video0 just doesn't get created.

There's probably a very simple solution for this, like me not doing a rather essential step or so.

Any help would be appreciated.

Ben

---

### Post by xc3RnbFO8P on 2008-05-26
This card is not supported,
HVR 1800 is a ATSC card
HVR 1700 is a DVB-T card
[http://www.linuxtv.org/wiki/index.php/Hauppauge]("http://www.linuxtv.org/wiki/index.php/Hauppauge")

---

### Post by elbekko on 2008-05-27
Thanks.

Are there any plans to support this card in the future? I don't really use it for DVB-T anyway, so perhaps other drivers could work for that.

---

