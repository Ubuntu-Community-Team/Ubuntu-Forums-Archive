---
title: "Why is natty so big?"
date: 2011-04-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Olosta on 2011-04-22
I have a maverick netbook install that crashed. I tried to reinstall in natty beta2 but the installer don't want to use my 4B SD card. It says to need 4.4GB.

I reinstalled the netbook with Maverick netbook (which only needs 2.5GB). I tried to do a it of cleanup (remove openoffice) and upgrade to natty, but it says I'm still 400 MB short to perform the upgrade (at least it's consistent).

I don't understand why Natty needs 75% more space than Maverick. I really wanted to have the new Unity and a browser on this netbook. Is that not possible ? Too bad because the live system works pretty well. Am I forced to purchase a 8GB SD card just to do this upgrade ?

If anyone know how to do a lighter upgrade, thanks for your help. And if you know why natty is so bloat^Woversized I'd really like to know the reason.

---

### Post by TenPlus1 on 2011-04-22
You also have to remember that a 4gb card never gives you the WHOLE 4gb to start with, you may get 3.8gb available, then their is the swap partition that Ubuntu installs with Maverick, so you're probably using up to 1gb for that...  So yes, an 8gb sd card would be a LOT better for installation...

Dunno if this helps but here's an 8gb card for £8 and free delivery:

[http://www.zoombits.co.uk/memory-cards/sd-card/memory-2-go-8gb-sdhc-class-4-memory-card/5787](http://www.zoombits.co.uk/memory-cards/sd-card/memory-2-go-8gb-sdhc-class-4-memory-card/5787)

---

### Post by Rasa1111 on 2011-04-22
I found the same, and thought it was pretty lame.
Always been able to intall Ubuntu on a 4GB drive..
But not natty! 
Super lame. :rolleyes:

---

### Post by sffvba[e0rt on 2011-04-22
Interesting and odd... I am sure there is a good reason for this... 


404

---

### Post by splicerr on 2011-04-22
Hi, you can blame this:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/745148/comments/10](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/745148/comments/10)

---

### Post by Rasa1111 on 2011-04-22
good enough for an extra 2GB's?
I dunno..
but that's how I always test a distro,
and i cant even properly test natty in an actual install of any kind, because of this.
I can just run it from the 'live session' with 'persistence' enabled..
Which doesnt allow me to test it properly.. but whatever..

I actually almost bought a new 8GB drive today while getting a laptop sleeve.. but decided against it at the lest minute.
hardly seems worth it just for natty. :rolleyes:

> Hi, you can blame this:

[https://bugs.launchpad.net/ubuntu/+s...48/comments/10](https://bugs.launchpad.net/ubuntu/+s...48/comments/10)

oh isnt that lovely... 
wtf?
So is it a bug? or just "how it is" now? :???:

---

### Post by dino99 on 2011-04-22
[http://archive.ubuntu.com/ubuntu/dists/natty/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/natty/main/installer-i386/current/images/netboot/mini.iso)

---

### Post by Olosta on 2011-04-22
The bug is interesting and says it's possible to bypass the limitation. Does anybody know how ?

---

### Post by Rasa1111 on 2011-04-22
> **dino99 said:**
> [http://archive.ubuntu.com/ubuntu/dists/natty/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/natty/main/installer-i386/current/images/netboot/mini.iso)

and this "mini.iso" file is what exactly?

---

### Post by kansasnoob on 2011-04-22
I'm performing iso-testing right now and a fresh installs / partition is coming in at about 3.65GB. Read that whole bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/745148](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/745148)

---

### Post by VMC on 2011-04-22
Somethings not right. Are you guys using a fresh install?

```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             9.7G  2.5G  6.7G  28% /

```

Mine is only 2 1/2 gb.

---

### Post by terry_gardener on 2011-04-22
> **Rasa1111 said:**
> and this "mini.iso" file is what exactly?

the mini.iso is a file to allow you to install ubuntu and download most of the required packages from the internet. 

the advantage of this is that it will install all the latest packages. 

you can use a cd or small usb drive to do this. 

and because it doesn't include the live cd you can install it on less powered hardware. 

check out [https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")for info.

---

### Post by kansasnoob on 2011-04-22
I was using a 4GB flash drive to test something else this AM so you might find this interesting (beginning with post #9):

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265)

BTW I have 2GB RAM so the "auto" install wants to create about 2GB of SWAP. You may be able to install using manual partitioning w/o a SWAP, and then create a SWAP file.

---

### Post by kansasnoob on 2011-04-22
> **VMC said:**
> Somethings not right. Are you guys using a fresh install?

```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             9.7G  2.5G  6.7G  28% /

```

Mine is only 2 1/2 gb.

Yes, this is a fresh install performed last night:

[ATTACH]189721[/ATTACH]

I only booted into it and tested a few apps, nothing has been modified. However they did release a new iso this AM and I need to repeat all tests with it :D

---

### Post by beew on 2011-04-22
Cos it eats too much fish? :)

Seriously I didn't notice this. I install Natty on a 10G partition in an external drive and space is not a problem so it never comes to my attention.
Now my installation stands at 4.7G( but I have installed some software, dowloaded some crap and copy about 50M of music from another hard drive for testing media players)

---

### Post by ranch hand on 2011-04-22
> **Rasa1111 said:**
> and this "mini.iso" file is what exactly?
If you have never used a netboot install,  *minimal". you really should.   The download is very fast, 22Mb for 11.04.

All you get is enough to boot to a text log in.  You can then log in and use apt-get, aptitude or dpkg to install the packages you want.  If you avoid using meta packages it is amazing how small you can get an install.

It is a real good idea to have a list before you start of what you want on the OS.  Unmet depends will be listed if you do not have them so you can install them first.

It is quite a bit of fun really.  Educational too.

One thing about it is that the bugger will always fit on a CD.

---

### Post by Quackers on 2011-04-22
Mine is currently using 3.96 GiB
It's barely modified but I am running gnome-shell.
Presumably Unity et al takes space.

---

### Post by Harry33 on 2011-04-22
I have Natty 64-bit containing total of 747 packages, with a root partition of 9.77 GiB,  2.18 GiB used and 7.58 GiB unused.

---

### Post by seeker5528 on 2011-04-22
> **VMC said:**
> Somethings not right. Are you guys using a fresh install?

```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             9.7G  2.5G  6.7G  28% /

```

Mine is only 2 1/2 gb.

You didn't read everything, this is a minim requirement coded into the installer to allow installation, not the amount of space used during or by the installation. 

This would be similar to Windows requiring 15+ GB for a new install when half of that is actually used.

You have to allow some room for expansion, after all.

If people have a more limited amount of space to work with, maybe the USB disk creator would work?

[http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator](http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator)

Later, Seeker

---

### Post by VMC on 2011-04-22
deleted.

---

### Post by Rasa1111 on 2011-04-23
> **seeker5528 said:**
> You didn't read everything, this is a minim requirement coded into the installer to allow installation, not the amount of space used during or by the installation. 

This would be similar to Windows requiring 15+ GB for a new install when half of that is actually used.

You have to allow some room for expansion, after all.

If people have a more limited amount of space to work with, maybe the USB disk creator would work?

[http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator](http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator)

Later, Seeker

The USB disk creator is what I always use to make bootable flash drives.. and have always been able to install any Ubuntu onto a 4GB drive, with "plenty" of room to spare.. 
But no longer... not with "natty". :mad:

---

### Post by bennachie on 2011-04-23
Natty Beta with Unity runs perfectly well on my eeePC-701 with 1GB RAM, 4GB onboard SSD (which I use for the "/" partition) and an 8GB SDHC card (for the "/home" partition). I do not allow the installer to create a swap partition.

With that setup, there seems to be plenty of headroom for normal email, surfing and document creation operations using the basic software package installed with Natty. I prefer Thunderbird to Evolution, mainly because of the small screen, but otherwise operate with a completely standard, although regularly updated, system.

---

### Post by Rasa1111 on 2011-04-23
Now some of you guys have me curious..
I'm going to have to try again....... (attempt 5)  lol :P

---

### Post by kansasnoob on 2011-04-23
Well, there have so far been three rounds of iso-testing and something has changed. 

My fresh installs are now coming out at 2.6GB + SWAP, about one full GB smaller than the previous two images.

No idea what the devs changed :confused:

But I'd certainly think it would be possible to install to a 4GB drive if one used manual partitioning w/o a SWAP, and then created a swap file after install.

---

### Post by Savio2010 on 2011-04-23
If you wanted to install Natty for Unity then install the 2D version of Unity via PPA.

Read this

[http://www.liberiangeek.net/2011/01/install-unity-2d-desktop-ubuntu-10-10-maverick-meerkat-ppa/](http://www.liberiangeek.net/2011/01/install-unity-2d-desktop-ubuntu-10-10-maverick-meerkat-ppa/)

---

### Post by terry_gardener on 2011-04-23
> **Savio2010 said:**
> If you wanted to install Natty for Unity then install the 2D version of Unity via PPA.

Read this

[http://www.liberiangeek.net/2011/01/install-unity-2d-desktop-ubuntu-10-10-maverick-meerkat-ppa/](http://www.liberiangeek.net/2011/01/install-unity-2d-desktop-ubuntu-10-10-maverick-meerkat-ppa/)

if you are using natty you don't need ppa to try unity 2d, it is in the  repos

---

### Post by seeker5528 on 2011-04-23
> **Rasa1111 said:**
> The USB disk creator is what I always use to make bootable flash drives.. and have always been able to install any Ubuntu onto a 4GB drive, with "plenty" of room to spare.. 
But no longer... not with "natty". :mad:

The USB disk creater says you only need 1 GB, but apparently it doesn't let you choose a non-USB drive to use.

But I just did an installation to a 3.5 GB partition using the Beta 2 disk, using the 'do something else' option and selecting the partition I want to use and to mount it at '/'.

Is this size thing something that changed in the daily ISO after Beta 2?

Guess I'll have to pick up some RW discs, the one I've been using is either too scratched up around the outer half or I've erased it too many times. Wasted a CD-R on this. I'm guessing too scratched up since it's been working fine for System Rescue CD.

EDIT: Just started the installation again and chose the 'upgrade' option, that seems to be working too.

Later, Seeker

---

