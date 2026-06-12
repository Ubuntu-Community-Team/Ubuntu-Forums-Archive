---
title: "D-Link wireless USB proplem"
date: 2010-09-29
forum: Networking &amp; Wireless
---

### Post by psudononymous on 2010-09-29
I recently installed the art of hacking live CD to my dell dim5150 desktop. I did the full installation so there is no other OS running on this machine.
I have a wireless card that is a USB
(this is the one I'm using)
[http://www.dlink.com/products/?pid=DWA-130&tab=3](http://www.dlink.com/products/?pid=DWA-130&tab=3)

I put the install disk in and I get a message saying that I have nothing that can open/recognize this type of file.

Any help would be great. I know this isn't a great way to be introduced to this system, nor a good introduction to this site.

I will be in class soon and when I'am back home I will check this post again to see if anyone can tell me anything useful since I have been lurking all over this site to see if anyone had the same problem as me.

---

### Post by mikewhatever on 2010-09-29
Hi there. Do you have Ubuntu installed? What version?
If you do, take a look at the link below.
[http://forums.dlink.com/index.php?topic=2228.0](http://forums.dlink.com/index.php?topic=2228.0)

---

### Post by psudononymous on 2010-09-29
> **mikewhatever said:**
> Hi there. Do you have Ubuntu installed? What version?
If you do, take a look at the link below.
[http://forums.dlink.com/index.php?topic=2228.0](http://forums.dlink.com/index.php?topic=2228.0)

I installed the version that this book comes with
[http://www.tkshare.com/hacking-the-art-of-exploitation-2nd-edition/](http://www.tkshare.com/hacking-the-art-of-exploitation-2nd-edition/)

Keep in mind I don't want to be some super 1337 h4x0r
I just liked that this version lets you experiment with things.

I installed the Pinguy OS yesterday and had the same problem.

---

### Post by mikewhatever on 2010-09-29
Well, the book may have come with Fedora, OpenSuse or Gentoo, all different, non-Debian distros. Is there any reason at all to assume it was Ubuntu?

---

### Post by bkratz on 2010-09-29
There are actually (last time I looked) five versions of the DWA-130 each using a different internal chip and software requirements.  I have the A1 version (it says on the label on the dongle itself) and have implemented it with success in both ubuntu (versions 8.10 through 10.04) and lubuntu 10.04. The link really doesn't say what version is contained or if my experience will help. But feel free to PM me for any help I can offer.

---

### Post by psudononymous on 2010-09-29
Here is the screenshot from the machine it is on.
I'm on my laptop posting this.

I also can't seem to get the files on the desktop to install as well.
They are the drivers for the wireless card, ndiswrapper, and something else, but its the .deb file.

---

### Post by psudononymous on 2010-09-29
> **bkratz said:**
> There are actually (last time I looked) five versions of the DWA-130 each using a different internal chip and software requirements.  I have the A1 version (it says on the label on the dongle itself) and have implemented it with success in both ubuntu (versions 8.10 through 10.04) and lubuntu 10.04. The link really doesn't say what version is contained or if my experience will help. But feel free to PM me for any help I can offer.

I'am pretty sure I have the same one. Although I'am not 100% positive.

---

### Post by mikewhatever on 2010-09-29
> **psudononymous said:**
> Here is the screenshot from the machine it is on.
I'm on my laptop posting this.

I also can't seem to get the files on the desktop to install as well.
They are the drivers for the wireless card, ndiswrapper, and something else, but its the .deb file.

There are several versions of Ubuntu (9.04, 9.10, 10.04, etc) and installation files for one version may not work on another. Try the following commands to find out the versions:

uname -r 
less /etc/lsb-release

---

### Post by psudononymous on 2010-09-29
> **mikewhatever said:**
> There are several versions of Ubuntu (9.04, 9.10, 10.04, etc) and installation files for one version may not work on another. Try the following commands to find out the versions:

uname -r 
less /etc/lsb-release


uname -r gave me:
2.6.20-15-generic


less /etc/lsb-release gave me:
DISTIB_ID=Ubuntu
DISTRIB_RELEASE=7.04
DISTRIB_CODENAME=feisty
DISTRIB_DESCRIPTION="Ubuntu 7.04"
/etc/lsb-release (END)

---

### Post by pinguy on 2010-09-29
> **psudononymous said:**
> uname -r gave me:
2.6.20-15-generic


less /etc/lsb-release gave me:
DISTIB_ID=Ubuntu
DISTRIB_RELEASE=7.04
DISTRIB_CODENAME=feisty
DISTRIB_DESCRIPTION="Ubuntu 7.04"
/etc/lsb-release (END)

That's a pretty old version. That version is 3 and half years old.
[https://help.ubuntu.com/7.04/](https://help.ubuntu.com/7.04/)

I doubt you will be able to get your wifi working in that version.

If you can get to a wired connection and plug your laptop into it you will be able to get a list of all the installed programs so that you will be able to import them into a newer version of ubuntu.

If you paste this in the terminal: *(with an internet connection)*
```
sudo apt-get install dselect
sudo dpkg --get-selections > ~/dpkglist.txt
```

It will save all the installed programs names into a file that will be in the home folder called dpkglist.txt 
save that and once you installed the new version of Ubuntu, you will be able to have all the programs that where installed on the one you got from the book.

---

### Post by psudononymous on 2010-09-29
> **pinguy said:**
> That's a pretty old version. That version is 3 and half years old.
[https://help.ubuntu.com/7.04/](https://help.ubuntu.com/7.04/)

I doubt you will be able to get your wifi working in that version.

I had this same problem with pinguy yesterday.

---

### Post by mikewhatever on 2010-09-29
Feisty is unsupported since October 2008. Get yourself an iso of Lucid. Happy hacking.

---

### Post by psudononymous on 2010-09-29
> **pinguy said:**
> That's a pretty old version. That version is 3 and half years old.
[https://help.ubuntu.com/7.04/](https://help.ubuntu.com/7.04/)

I doubt you will be able to get your wifi working in that version.

If you can get to a wired connection and plug your laptop into it you will be able to get a list of all the installed programs so that you will be able to import them into a newer version of ubuntu.

If you paste this in the terminal: *(with an internet connection)*
```
sudo apt-get install dselect
sudo dpkg --get-selections > ~/dpkglist.txt
```

It will save all the installed programs names into a file that will be in the home folder called dpkglist.txt 
save that and once you installed the new version of Ubuntu, you will be able to have all the programs that where installed on the one you got from the book.


So I would need to plug my laptop into my desktop through an Ethernet chord, run that into the terminal, save what it outputs into a txt file, save the txt file to my laptop, install new version of ubuntu (most likely pinguy)and put the txt file somewhere on pinguy?

---

### Post by psudononymous on 2010-09-29
> **mikewhatever said:**
> Feisty is unsupported since October 2008. Get yourself an iso of Lucid. Happy hacking.

Would this work/what you are talking about?
[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

if it is, can you tell me about it?

---

### Post by psudononymous on 2010-09-29
Installed Lucid, but am still having the same problem.

---

### Post by pinguy on 2010-09-29
> **psudononymous said:**
> So I would need to plug my laptop into my desktop through an Ethernet chord, run that into the terminal, save what it outputs into a txt file, save the txt file to my laptop, install new version of ubuntu (most likely pinguy)and put the txt file somewhere on pinguy?

Pretty much, but first you are going to have to find out if you can get the wireless working. If it doesn't work in Pinguy OS it will not work in Lucid.

Find out the model of the D-Link wireless USB and search these forums to see if anyone has got it working.

---

