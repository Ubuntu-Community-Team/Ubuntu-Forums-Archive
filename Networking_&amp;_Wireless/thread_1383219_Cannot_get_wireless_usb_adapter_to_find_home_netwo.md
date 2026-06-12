---
title: "Cannot get wireless usb adapter to find home network"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by jiffum on 2010-01-17
Hello,

Just to let you everyone know I am a complete beginner to linux, so I am sorry if I do not explain my problem very well.

I'm using ubuntu 9.10 64 bit and am trying to get a wireless USB adapter, Edimax 7718un, to function properly.  I do not really know where to start to be honest.  I did try using ndiswrapper, but I cannot find an actual version of the xp-64 bit driver anywhere for my card.

I have tried downloading the ralink drivers listed in the synaptics package manager, but it's not loading any of them to the adapter.  The card does locate every wireless network in the area except for mine.  My connection on the ubuntu computer is spotty and only works sometime, because i can use my neighbors unsecured connection and it doesn't stay connected and is really slow.

I also have the newest version of the linux driver in an archive, but for some reason the make file will not finish.  It always aborts after it tries to copy a file.

I have ran the lshw -C network and under the configuration line it says it is broadcasting, but does not list a driver.  Any help on getting my card to work would be greatly appreciated.  Thank you in advance.

---

### Post by lincoln32 on 2010-01-17
step 1 connect lan and update then check system-administration-hardware drivers install recommended drivers if any ubuntu can find and install itself but will need Internet to auto load drivers. this works for most
wifi cards that do not have linux drivers if not it might be easier find a 
better wifi card  there are some thast will not just plain work in linux

---

### Post by jiffum on 2010-01-17
I have the linux drivers for my card, but it won't let me completely compile it.  The make file keeps aborting when it tries to copy a file.

The card is connected to my neighbors wifi at the moment.  I cannot get it to completely update and have tried a few times.  After each attempt I have rebooted under system->administration->hardware drivers but with no success so far.

It keeps connecting to my neighbors network, and finds the others in the area, about 6, but it will not find my network connection at all.

Unfortunately I have no way to connect it to a wired connection anymore.  I tried adding the connection manually, but still no luck.

---

