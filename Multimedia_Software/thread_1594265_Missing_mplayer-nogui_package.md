---
title: "Missing mplayer-nogui package"
date: 2010-10-12
forum: Multimedia Software
---

### Post by agent.zeroone on 2010-10-12
Hi all, I can't find the mplayer-nogui package for Ubuntu 10.10 (Maverick)
```
$ cat /etc/apt/sources.list
deb http://archive.ubuntu.com/ubuntu maverick main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu maverick-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu maverick-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu maverick partner
deb http://extras.ubuntu.com/ubuntu maverick main
deb http://download.virtualbox.org/virtualbox/debian maverick non-free
deb http://packages.medibuntu.org/ maverick free non-free
```
```
$ apt-cache search mplayer-nogui
$
```
```
$ uname -a
Linux sulaco 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux
```

Thank you for reading

---

### Post by nothingspecial on 2010-10-12
```
Package mplayer-nogui is not available, but is referred to by another package.  
This may mean that the package is missing, has been obsoleted, or               
is only available from another source                                           
However the following packages replace it:                                      
  mplayer           
```

---

### Post by agent.zeroone on 2010-10-12
Does this mean mplayer-nogui will no longer be available?
I was hoping to avoid installing the gui for mplayer.

---

### Post by SeijiSensei on 2010-10-12
An excellent alternative to the official repositories for mplayer is the one maintained by "rvm," the author of the outstanding SMPlayer.  smplayer might make you want to use a GUI after all!  His versions of mplayer are usually more current than the ones distributed officially by Ubuntu.

[https://launchpad.net/~rvm/+archive/ppa](https://launchpad.net/~rvm/+archive/ppa)

---

### Post by tommcd on 2010-10-12
> **agent.zeroone said:**
> Does this mean mplayer-nogui will no longer be available?
I was hoping to avoid installing the gui for mplayer.
Even if gmplayer is installed you still can just use the no GUI mplayer from the terminal if you want to. I do it all the time.

---

### Post by agent.zeroone on 2010-10-13
I installed the mplayer package (Medibuntu) and it didn't install a GUI. :)
```
$ apt-cache policy mplayer
mplayer:
  Installed: 2:1.0~rc4~try1.dsfg1-1ubuntu1+medibuntu1
  Candidate: 2:1.0~rc4~try1.dsfg1-1ubuntu1+medibuntu1
  Version table:
 *** 2:1.0~rc4~try1.dsfg1-1ubuntu1+medibuntu1 0
        500 http://packages.medibuntu.org/ maverick/non-free amd64 Packages
        100 /var/lib/dpkg/status
     2:1.0~rc4~try1.dsfg1-1ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ maverick/universe amd64 Packages
```
@nothingspecial, SeijiSensei, tommcd: Thank you guys for replying... really appreciate it.

---

### Post by tommcd on 2010-10-14
> **agent.zeroone said:**
> I installed the mplayer package (Medibuntu) and it didn't install a GUI. :)

I did a clean install of Lubuntu 10.10. It comes with gnome-mplayer. Searching the Maverick repos does not find the MPlayer GUI (gmplayer), so I have not been able to install the MPlayer GUI on Maverick either. I have the medibuntu repos added also.
There are the 2 GUI alternatives, smplayer and gnome-mplayer available.
I am fine using MPlayer from the terminal though.

---

