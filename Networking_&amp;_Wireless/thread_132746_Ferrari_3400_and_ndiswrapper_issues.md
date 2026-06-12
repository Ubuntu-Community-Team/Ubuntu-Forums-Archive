---
title: "Ferrari 3400 and ndiswrapper issues"
date: 2006-02-18
forum: Networking &amp; Wireless
---

### Post by benpbrown on 2006-02-18
Hi, I'm having some issues getting my Ferrari 3400 integrated wireless to work. It is a  Broadcom of some sort. 

Terminal Output:
```
root@ubuntulaptop:/home/ben/Wireless# modprobe ndiswrapper
FATAL: Could not open '/lib/modules/2.6.12-9-amd64-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko': No such file or directory
root@ubuntulaptop:/home/ben/Wireless#

```

64-bit Breezy Badger shipit.ubuntu.com version.

Thanks,
Ben

---

### Post by benpbrown on 2006-02-19
Any ideas? This is driving me nuts and if it doesn't work, there goes Ubuntu :\

Compiling from source doesn't work, because it doesn't have the kernel source... or something.

---

### Post by crd on 2006-02-19
I know you have a 64-bit computer, but is there any reason why you've put on Ubuntu 64 bit?  I did the same thing, but tossed the idea when I looked into it more and there is no significant performance gain using the 64 bit ed. and it limits many applications/drivers as well.

With that aside, try to get the latest source of ndiswrapper and compile it for your machine.  I have a broadcom as well and it's quite picky.  If you can get to Synaptic Package Manager & the net through maybe an ethernet connection, you can try to completely remove and re-add the ndiswrapper that way.

Any more details or are you still stuck at the modprobe part.  I was assuming you already did an *ndiswrapper -i mydriver.inf* to get the driver set.

crd

---

### Post by benpbrown on 2006-02-19
I was under the impression that 32-bit Ubuntu would not run on a 64-bit machine. If so, that makes me very sad. I want Automatix.... I was aware of the application limits, but as I said before ^

When I tried to compile from source, it needed kernel source... or something. Ethernet works perfectly, sooooo much faster than Windows. Stable 230 KB/s. Yes, I have done the ndiswrapper -i file.inf and -l gave me hardware and driver present messages. 

I guess next weekend I'll nuke Ubuntu 64 and install Ubuntu 32.... No data on their yet...

---

### Post by shazam on 2007-11-26
Ok I installed the ndiswrapper using the Synaptic Package Manager.  Now do I install a driver in addition to that?  The description of the ndiswrapper project indicated that it makes it possible to use windows drivers.  Is that what I need to install now?  Help!  Thanks in advance.:)

My System: Acer Ferrari 3400 laptop
Ubuntu 7.10 / Windows XP dual-boot

---

