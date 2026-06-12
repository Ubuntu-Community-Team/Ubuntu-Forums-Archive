---
title: "How to configure BSNL Huawei 3G modem with Ubuntu 10.04?"
date: 2010-10-06
forum: Networking &amp; Wireless
---

### Post by santhosh.p on 2010-10-06
[**Hi friends,**]("http://answers.yahoo.com/question/index;_ylt=ApMQ9oyksQwTs2yXrC.qbT_ty6IX;_ylv=3?qid=20101003211635AAd0WyV")
      Please help me out how to configure Huawei 3G modem (ec325) in ubuntu 10.04, even i tried with gnome-ppp / wvdial which unable to connect, shows "ppp deamon died" and disconnected at the end of dial. 

" hope these experts will help me :KS , so am here :) . Thank you in advance friends "

---

### Post by dineshs on 2010-10-06
Please post the results of
```
lsusb
```and
```
dmesg | grep -e "modem" -e "tty"
```
(ref [http://ubuntuforums.org/showthread.php?t=1466490](http://ubuntuforums.org/showthread.php?t=1466490))

---

### Post by amite on 2010-10-06
i had the same problem ,now i am using Sakis3g script.it solved my problem,just see it..... [httphttp://ubuntuforums.org/showthread.php?t=1586753](httphttp://ubuntuforums.org/showthread.php?t=1586753)

---

### Post by alexfish on 2010-10-06
> **amite said:**
> i had the same problem ,now i am using Sakis3g script.it solved my problem,just see it..... [httphttp://ubuntuforums.org/showthread.php?t=1586753](httphttp://ubuntuforums.org/showthread.php?t=1586753)

error in above link

try

[http://ubuntuforums.org/showthread.php?t=1586753](http://ubuntuforums.org/showthread.php?t=1586753)

---

