---
title: "Netgear WNDA3100v2 - How to install?"
date: 2013-07-13
forum: Networking &amp; Wireless
---

### Post by UltPokemonFan on 2013-07-13
Alright, so I have a Netgear WNDA3100v2 N600 wireless adapter. I dual boot Win7 and Ubuntu, and I want to get it working in Ubuntu, but I'm not sure how.
I found this thread: [http://ubuntuforums.org/showthread.php?t=1964173](http://ubuntuforums.org/showthread.php?t=1964173)
The instructions seem straightforward, however I need to install ndiswrapper. I have no way to access the internet on this computer. I thought maybe I could download the ndiswrapper packages and dependencies on Windows from the launchpad site and install from Ubuntu, but the Software Center won't let me install them. (the install button is greyed out, can't use File > Install either) Is there anyway I can get it working?

---

### Post by praseodym on 2013-07-14
Hi,

is it 32 or 64 bit? Please show the terminal (CTRL+ALT+T) outputs of:
```

uname -a
dpkg -l linux-headers-* | grep ii
```

---

