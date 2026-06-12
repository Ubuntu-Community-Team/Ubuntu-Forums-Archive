---
title: "no sound in ubuntu help"
date: 2007-12-28
forum: Multimedia &amp; Video
---

### Post by tgsauer19 on 2007-12-28
I have a new Dell  Inspiron 1720 Laptop which I have installed Ubuntu on... I am also new UBUNTU user. Laptop plays music when I boot VISTA (UGH) but when I bring up UBUNTU, I get no sound. Volume icon has international "no" symbol over it. I have tried reload codec... no effect. What do you think the problem is? Any suggestions on how to proceed. I have a suspicion that it may not be recognizing the sound card... how do I check? I am running new version of Ubuntu that I downloaded this week.

---

### Post by linuxwizard on 2007-12-28
Look over this

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

### Post by tgsauer19 on 2007-12-28
Did as suggested got this reply:
greg@greg-laptop:~$  lspci -n | grep `lspci | grep -i audio | awk '{print $1}'`
00:1b.0 0403: 8086:284b (rev 02)
greg@greg-laptop:~$ 

My machine and sound card are listed. See below.  I am running Gutsy. Is there a work around that you would suggest? Nothing is urgent. IWhat course of action would you recommend.

#

Inspiron 1720

    *

      Muszek:
          o

            00:1b.0 0403: 8086:284b (rev 02)
          o

            /proc/asound/card0/codec#0:Codec: SigmaTel STAC9205
          o

            /proc/asound/card0/codec#1:Codec: Conexant ID 2c06

---

### Post by linuxwizard on 2007-12-28
Did you look through this and see if their is a work around or fix ?

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131133](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131133)

---

