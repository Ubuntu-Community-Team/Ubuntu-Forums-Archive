---
title: "Need help with Ndiswrapper"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by outy565 on 2008-12-24
Hey guys I'm trying to use ndiswrapper in xubuntu to get my linksys wpc54g ver2 wireless card to work in my toshiba satellite 1405 s171 laptop.  I'm going to be honest, I'm new to linux and have no idea how it works or what to do.  I've looked at some of the guides for ndiswrapper and they do not make any sense to me cause i dont know anything about linux yet or how it works or how to work it.  Its starting to get quite frustrating lol.  Could someone help me out with this and use uber noob terms so that i can understand it?

I would greatly appreciate it.  Thanks.

Btw, i already downloaded ndiswrapper 1.53.tar.gz

---

### Post by S_e_P_p on 2008-12-24
Hi,

You have to unarchive the .exe of your windows driver and implement the .inf into the ndiswrapper tool.

Here is a small howto:

Download the latest XP WLAN driver:

open a terminal and type:

```

sudo apt-get install ndiswrapper-utils-1.9

```

Unzip the WLAN driver and go into this folder within a terminal.

```
cd foldername
``` 
to browse through the folders. 
```
cd ..
``` will go one folder upwards

Use the following code:
```

sudo ndiswrapper -i FILENAMEOFYOURDRIVERINF.inf

sudo ndiswrapper -m

sudo ndiswrapper -mi

sudo ndiswrapper -ma

sudo modprobe ndiswrapper


```

Maybe you have to restart. Type ifconfig and control your wlan card and driver.

Via System --> Administration --> Windows driver you can also do this via a GUI (once you installed ndiswrapper) if you cant get this working via terminal. You have to implement the .inf file of your win xp wlan driver.


Give it a try and let me know if you get it working.

Here are some more information:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?#head-6a606ccd9c2c4db72ac726891bd5d7cbaf8097de](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?#head-6a606ccd9c2c4db72ac726891bd5d7cbaf8097de)

Greets,
SePp

---

### Post by outy565 on 2008-12-25
ok thanks!  but how do i install ndiswrapper?  i'm still very new to linux and don't know how to do anything in it yet.

---

### Post by outy565 on 2009-01-01
bump

---

