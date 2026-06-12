---
title: "Networking problems"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by oleink on 2010-03-11
Hello
I just installed Ubuntu on a laptop that I fixed and rebuilt but I have absolutely no idea how to connect to wireless networks on it.  It doesn't appear to notice my wireless nic.  how do you use ndiswrapper.   I cant find how to use it or how it works online at all.  I need to know how to download either to a cd or just know how to install it on ubuntu

---

### Post by chili555 on 2010-03-11
Maybe we don't need ndiswrapper, unless you have done considerable searching and know that's the only way. Please open a terminal and do:```
sudo lshw -C network
lsusb
```Let's find out what you have.

---

### Post by hippietilley on 2010-03-11
You can also have Ubuntu search for drivers by going to System>Administration>Hardware Drivers. It searches for drivers and installs them for you.

---

### Post by oleink on 2010-03-11
Ok it said there were no drivers to be installed.  My thing said network disabled when i used the terminal.

---

### Post by chili555 on 2010-03-11
> **oleink said:**
> Ok it said there were no drivers to be installed.  My thing said network disabled when i used the terminal.Please see post #2.

---

### Post by oleink on 2010-03-19
Thanks I actually found a way quicker way though.  I installed indiswrapper through synaptic package manager, then i installed wine through Ubuntu Software center, then I went to System>Administration>Hardware drivers and installed my driver there.
It took less than 5 minutes and my wifi is at 100%

PS I would have posted this earlier but for some reason my user name for ubuntu forums changed by one letter and i received an email about it but hadnt checked my email so i did not know it had changed.

---

### Post by Iowan on 2010-03-20
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?
Glad you found a solution :)

---

