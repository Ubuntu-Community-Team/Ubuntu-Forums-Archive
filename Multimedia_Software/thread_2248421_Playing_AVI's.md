---
title: "Playing AVI's"
date: 2014-10-14
forum: Multimedia Software
---

### Post by nd4562 on 2014-10-14
I am trying to get the video player to decode Avi's with no luck. Its needs an upgrade and i reveive this error.
 The following packages have unmet dependencies:
```
gstreamer1.0-libav:i386: Depends: libavcodec-extra-54 (>= 6:9.13) but 6:9.16-0ubuntu0.14.04.1+fdkaac is to be installed
                         Depends: libavformat54 (>= 6:9.1-1) but 6:9.16-0ubuntu0.14.04.1+fdkaac is to be installed
                         Depends: libavutil52 (>= 6:9.1-1) but 6:9.16-0ubuntu0.14.04.1+fdkaac is to be installed
                         Depends: libc6 (>= 2.7) but 2.19-0ubuntu6.3 is to be installed
                         Depends: libglib2.0-0 (>= 2.37.3) but 2.40.0-2 is to be installed
```

---

### Post by SeijiSensei on 2014-10-14
Try installing **smplayer** from the repositories.

---

### Post by nd4562 on 2014-10-15
Installed with no difference still getting the
```
 The following packages have unmet dependencies:

gstreamer1.0-libav:i386: Depends: libavcodec-extra-54 (>= 6:9.13) but 6:9.16-0ubuntu0.14.04.1+fdkaac is to be installed
                         Depends: libavformat54 (>= 6:9.1-1) but 6:9.16-0ubuntu0.14.04.1+fdkaac is to be installed
                         Depends: libavutil52 (>= 6:9.1-1) but 6:9.16-0ubuntu0.14.04.1+fdkaac is to be installed
                         Depends: libc6 (>= 2.7) but 2.19-0ubuntu6.3 is to be installed
                         Depends: libglib2.0-0 (>= 2.37.3) but 2.40.0-2 is to be installed


```

---

### Post by Bucky Ball on 2014-10-15
*Thread moved to **Multimedia**.*

Welcome. Which release are you running?

---

### Post by SeijiSensei on 2014-10-15
It's got to be a pretty old release given:
```
Depends: libc6 (>= **2.7**) but **2.19**-0ubuntu6.3 is to be installed
```

---

### Post by Bucky Ball on 2014-10-15
> **SeijiSensei said:**
> It's got to be a pretty old release given:
```
Depends: libc6 (>= **2.7**) but **2.19**-0ubuntu6.3 is to be installed
```

My thoughts also, meaning, it is possibly EOL, in which case it is no longer supported by Canonical or these forums. 

To the OP, if you are not running 12.04 or 14.04 then please see [HERE]("http://ubuntuforums.org/showthread.php?t=2229730"). Thanks.

---

### Post by nd4562 on 2014-10-15
Im running 14.04LTS. It was upgraded from 10.04LTS.

---

### Post by Bucky Ball on 2014-10-15
How did you upgrade? A clean install or 10.04>12.04>14.04?

---

### Post by nd4562 on 2014-10-15
Must have been 10.04>12.04>14.04. I used the application. I usually do clean install's and this is the first time I haven't.

---

### Post by Bucky Ball on 2014-10-15
Please try these three commands in a terminal:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Post back any and all error messages. You might also try uninstalling whatever video player it is you are trying to use then re-installing it from the Software Centre/Synaptic Package Manager. Whatever version of the vid player you are using looks to be old and the dependencies no longer exist (it wants to install the 14.04 versions to old software).

Upgrading the way you did can be problematic. Bits can be left over and if you'd done a lot of customising and/or adding third-party PPAs in 10.04, this can often be at the root of the problems. 

I stick to a clean install myself, generally on another partition so if things get difficult I can use the old working install to try and figure it out. Good luck.

---

### Post by nd4562 on 2014-10-15
seemed to make some effect... 
I now only get this error...
```
 The following packages have unmet dependencies:

libavcodec54: 
```

---

### Post by Yellow Pasque on 2014-10-15
It looks like you are using this PPA and it may be causing the conflict: [https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)
All the version requirements are met in the error message you got, so I don't know if the PPA is causing or even related to the issue. The PPA is owned by a moderator here, so maybe try pinging him and see if he will look at this thread: [http://ubuntuforums.org/member.php?u=320715](http://ubuntuforums.org/member.php?u=320715)

> **SeijiSensei said:**
> It's got to be a pretty old release given:
```
Depends: libc6 (>= **2.7**) but **2.19**-0ubuntu6.3 is to be installed
```

No, it's **>**=, so it's okay.

---

### Post by nd4562 on 2014-10-15
I installed it to attempt to resolve the issue on my own. But somehow or another, after a reboot I am now able to play the AVI's I had the issue with.

---

### Post by Bucky Ball on 2014-10-15
That's good news. If you consider this thread as solved, please mark it that way by following the second link in my signature. Good luck. ;)

---

### Post by SeijiSensei on 2014-10-16
> **Temüjin said:**
> No, it's **>**=, so it's okay.

Only in the world of software versioning is 2.19 > 2.7 :D

---

