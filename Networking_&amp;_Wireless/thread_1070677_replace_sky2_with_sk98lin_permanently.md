---
title: "replace sky2 with sk98lin permanently"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by GreTTin on 2009-02-15
hey all, 

I've been using ubuntu for quite a while now but I'm not an advanced user, I was hoping someone can help me with a little problem I'm having.

I rebuilt my computer with a new motherboard and my internet kept dropping out and after a while I figured out it was because of the sky2 driver. I have the Asus M3A32-MVP Deluxe mother board wich has a marvell/yukon ethernet port (something like that) I replaced the sky2 driver with sk98lin one by following these commands after downloading their driver from the marvell website.

```
sudo apt-get install build-essential linux-headers-$(uname -r)

sudo ln -s /usr/src/linux-headers-$(uname -r) /usr/src/linux

sudo modprobe -r sky2

sudo ./install.sh 
```

I had to change the beginning of the install file to bin/bash (from bin/sh) apart from that it worked fine.


my problem is every time i restart my computer it goes back to sky2.

How do I get rid of this for good? I thought thats what the 3rd command did.

Thank you in advance for your help.

Paul.

---

### Post by kevdog on 2009-02-15
For one, I would add sky2 to the /etc/modprobe.d/blacklist file so that it is not automatically loaded on boot!

---

### Post by GreTTin on 2009-02-15
hey, Thanks for the quick reply.

I added 

```
# replaced sky2 with sk98lin
blacklist sky2
```

to that file at the end but it still loads up sky2 until I run the install again.

Also of note is ```
sudo modprobe -r sky2
``` doesn't work any more it says it doesn't exist but ```
sudo rmmod sky2
``` gets rid of it.

any ideas?

Thank you in advance for your help

Paul

---

### Post by GreTTin on 2009-02-15
bump?

---

### Post by GreTTin on 2009-03-04
nobody? well I have no internet at the moment on that computer as sky2 is no longer there (not too sure how i did that) and i can't install the other one now as when the process gets to compiling the kernel it errors out, it says to go to a file, think its /etc/linux, can't remember off the top of my head  and then run makefile when i do that it says i need a dependancy which i can't get as i have no internet.

So anyway i'm going to reinstall can anyone recomend a distro that supports marvell yukon ethernet controller out the box?

I think they're standard on most asus motherboards(?)

thank you in advance.

---

### Post by foresto on 2011-10-23
FYI, I just finished packaging the latest sk98lin driver (from August 2011) for Ubuntu Natty.  You can find my announcement post here:

[http://ubuntuforums.org/showthread.php?p=11382042#post11382042](http://ubuntuforums.org/showthread.php?p=11382042#post11382042)

---

