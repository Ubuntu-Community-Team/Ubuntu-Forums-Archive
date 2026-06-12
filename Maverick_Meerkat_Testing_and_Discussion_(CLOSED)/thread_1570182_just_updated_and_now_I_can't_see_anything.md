---
title: "just updated and now I can't see anything"
date: 2010-09-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by bardic on 2010-09-07
Hey all,
I just updated from 10.04 to 10.10. Now when I select what kernal to boot it shows the ubuntu loading screen for a second then turns my monitors off. I know this is a newbie question and I've encountered this in the past, but I can't for the life of my remember how to fix it. 

Thanks!

---

### Post by andrewthomas on 2010-09-07
what graphics card do you have?

---

### Post by bardic on 2010-09-07
I have a national radeon hd. *something* I am ggetting a few errors from xorg. 
Failed to load module "ati" (module does not exist, 0)
failed to load module "versa" (module does not exist, 0)
failed to load module "fbdev" (module does not exist, 0)
no drivers available

I dunno what to do. >.<

---

### Post by andrewthomas on 2010-09-07
try to press e at the grub screen and add nomodeset to the kernel line

or try to boot to rescue mode and sudo aptitude reinstall xserver-xorg-video-all

---

### Post by bardic on 2010-09-07
I tired reinstalling xorg. I'm seeing a message that 3 packages aren't being update. Xserver-xorg
 xserver-xorg-core
 xserver-xorg-input-wacom

---

### Post by andrewthomas on 2010-09-07
try
```
sudo aptitude purge fglrx
sudo rm /etc/X11/xorg.conf
```

---

### Post by Iowan on 2010-09-07
Moved to Maverick Meerkat Testing and Discussion

---

### Post by bardic on 2010-09-07
No luck. I've been trying to remove those packages to reinstall them or to fix their dependencies but I don't have the knowledge to do it >.<

---

### Post by andrewthomas on 2010-09-07
what was the result of 

```
sudo aptitude purge fglrx
sudo rm /etc/X11/xorg.conf
```

---

### Post by andrewthomas on 2010-09-07
> **andrewthomas said:**
> what was the result of 

```
sudo aptitude purge fglrx
sudo rm /etc/X11/xorg.conf
```
If you have already done the above steps, what I would do next is read about the ppa here
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

and 
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo aptitude update && sudo aptitude safe-upgrade
```or
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by bardic on 2010-09-08
Hey. Sorry for the late reply. I was asleep lol.

The first purge worked ok, but there is no xorg.conference to be removed.  I tried to add that repo but it seems I already have it there. And when I did the upgrade I got a message "invalid operation safe-upgrade"

---

### Post by bardic on 2010-09-08
Hey. So I think I got it all working now.

```

apt-get --purge remove xserver-xorg
apt-get install xserver-xorg 
dpkg-reconfigure xserver-xorg
```

I am now seeing my desktop and all the fun jazz. Thanks for the help :) If I hit anything else with this I'll let ya know.

---

### Post by bardic on 2010-09-08
Hit another snag. So with what I did before I can see my desktop, but I was wanting to install the fglrx driver thingys but I hit this bug : [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/585759](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/585759)

Should I just wait with what I have until things get updated? Thanks for all the help :)

---

### Post by bardic on 2010-09-08
Hey again. Sorry I keep posting in my own thread so much, but I was doing some forum crawling and came across this thread [http://ubuntuforums.org/showthread.php?t=1561685](http://ubuntuforums.org/showthread.php?t=1561685) that seems to say that if I downgrade my xorg server to 1.8 I should be able to build fglrx fine. Is this true? Or will it will fail because of the kernel errors I was getting? I'm not at home at the moment, or I would just try it instead of asking. Thanks again!

---

### Post by andrek on 2010-09-08
Yup, it's true. Fglrx works nice @ 2.6.35-20-generic and xserver 1.8.

---

