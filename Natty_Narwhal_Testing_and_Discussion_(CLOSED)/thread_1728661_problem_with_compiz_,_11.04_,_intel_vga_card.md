---
title: "problem with compiz , 11.04 , intel vga card"
date: 2011-04-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by k7rata121 on 2011-04-14
hello everybody

I have a serious problem with ubuntu natty 11.04, My vga card is no longer supported for compiz ! :(

I have been using ubuntu since 8.04 and the compiz was running well until 10.10 but when i tried natty beta 1, it tells me that my video card is not supported with unity , and the classic desktop crashes like this :confused:



[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189008&stc=1&d=1302760639[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189009&stc=1&d=1302760639[/IMG]

my video card is "Intel Corporation 82865G Integrated Graphics"

I've reported this bug but I can't find its link,

thank you

---

### Post by dino99 on 2011-04-14
about reported bug: you can find it if you are logged on bugs.launchpad and listing your own bugs, not so difficult.

About your issue, with synaptic:
- remove/purge ubuntu-desktop (doing a right click)
- remove/purge compiz
- remove/purge unity

then reinstall compiz & unity
maybe compizconfig-settings-manager tweak can help

---

### Post by k7rata121 on 2011-04-14
thank you Mr.dino99 for your quick reply

about the bug, here is the[ link ]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/711231")

about the problem, It happens from the live CD! ,I don't think purging compiz and unity and reinstalling may help.. anyway I'll try and give you the result..

---

### Post by k7rata121 on 2011-04-14
I've tried your solution to purge "unity,ubuntu-desktop,compiz" and now I work with metacity as the composit manager .. no problems with metacity and everything is ok

I installed compiz again "without unity" and the same problem here :(

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189017&stc=1&d=1302767270[/IMG]

---

### Post by dino99 on 2011-04-14
> **k7rata121 said:**
> I've tried your solution to purge "unity,ubuntu-desktop,compiz" and now I work with metacity as the composit manager .. no problems with metacity and everything is ok

I installed compiz again "without unity" and the same problem here :(

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189017&stc=1&d=1302767270[/IMG]

lot of users have compiz issues, some of them have found workaround using ccsm but not all, might be better in few weeks (after 11.04 release)

---

