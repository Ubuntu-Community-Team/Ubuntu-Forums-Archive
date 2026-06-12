---
title: "libGL.so"
date: 2011-04-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by flintman on 2011-04-03
So i have upgraded to 11.04.  I know its beta but it should be pretty usable which don't get me wrong it is but I'm coming across a lot of issues in which libGL.so is part of it.

NETBEANS: ```
#  SIGSEGV (0xb) at pc=0x00007f9544e40d21, pid=4583, tid=140279401146112
#
# JRE version: 6.0_22-b22
# Java VM: OpenJDK 64-Bit Server VM (20.0-b11 mixed mode linux-amd64 compressed oops)
# Derivative: IcedTea6 1.10.1pre
# Distribution: Ubuntu Natty (development branch), package 6b22-1.10.1~pre1-0ubuntu1
# Problematic frame:
# C  [libGL.so.1+0x7dd21]  glXCreateWindow+0xeb01
```

World Of Warcraft/Any graphics windows game i need to run
```
LD_PRELOAD=/usr/lib32/nvidia-current/libGL.so
```

in order to get them to work right.

Is this due to being a beta and nvidia doesn't have the correct drivers out or is there something that happened to my computer while upgrading.  

Thanks

---

### Post by MacUntu on 2011-04-03
Run ```
sudo update-alternatives --config gl_conf
```  and make sure it's set to ```
0            /usr/lib/nvidia-current/ld.so.conf   9700      auto mode
```

---

### Post by flintman on 2011-04-04
```
  Selection    Path                                Priority   Status
------------------------------------------------------------
  0            /usr/lib/nvidia-current/ld.so.conf   9700      auto mode
  1            /usr/lib/mesa/ld.so.conf             500       manual mode
* 2            /usr/lib/nvidia-current/ld.so.conf   9700      manual mode

```


Ok selected 0.  Restarted computer to insure it all took and still have same issue

---

### Post by MacUntu on 2011-04-04
Actually, it doesn't matter that much. It's set to right location, so I'm afraid that's not the problem. :(

---

### Post by flintman on 2011-04-04
Thanks for trying anyone else 8)

---

### Post by flintman on 2011-04-05
Am I the only one with this problem?

---

### Post by dino99 on 2011-04-05
clean the sources:

sudo rm /var/cache/apt/archives/*

open synaptic:

- remove/purge openjdk
- check the source list: be sure to only use genuine natty repo and trusted ppa in case, partner repo need to be activated
- update
- install sun-java6-jre

---

### Post by flintman on 2011-04-05
Well i just removed and reinstalled my video drivers.  My windows based games now work with out the LD_PRELOAD.  


Netbeans is still not working with out it.  I tried Dino99 all you suggested and still not working.  

Well at least one problem fixed

---

### Post by dino99 on 2011-04-05
how is installed netbeans ? from winetricks ? is mono working better ? Look at winehq base for your game

---

### Post by flintman on 2011-04-05
[netbeans]("http://www.netbeans.com/") is a linux install.  Maybe now that I reinstalled the video drivers I might have to un-install netbeans then reinstall

---

### Post by dino99 on 2011-04-05
> **flintman said:**
> [netbeans]("http://www.netbeans.com/") is a linux install.  Maybe now that I reinstalled the video drivers I might have to un-install netbeans then reinstall

i've not a good feeling with this package, upp is prefered

---

