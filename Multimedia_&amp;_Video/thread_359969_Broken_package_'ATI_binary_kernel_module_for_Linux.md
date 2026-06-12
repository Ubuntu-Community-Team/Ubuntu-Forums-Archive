---
title: "Broken package 'ATI binary kernel module for Linux 2.6.15-27-386'"
date: 2007-02-12
forum: Multimedia &amp; Video
---

### Post by spacegypsy on 2007-02-12
Hi;

I just installed the latest ATI driver following [this guide ]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")and using method 2.
Everything went smooth till I wanted to do some software update with the update manager.
First I got: > Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

So I did run the sudo command in a terminal and got: > E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
dimitri@dimitri-laptop:~$

When I opened the Synaptic Package Manager I saw that the fglrx-kernel-2.6.15-27-386 package is broken.

How do I fix it?

thanx

---

### Post by spacegypsy on 2007-02-13
Problem seems to be solved using;

```
sudo apt-get install -f
```

found [here]("http://www.ubuntuforums.org/showthread.php?t=347331&highlight=broken+package").

---

