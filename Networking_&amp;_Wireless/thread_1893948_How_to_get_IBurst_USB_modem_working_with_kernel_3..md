---
title: "How to get IBurst USB modem working with kernel 3.0 and up"
date: 2011-12-11
forum: Networking &amp; Wireless
---

### Post by lost.soul on 2011-12-11
Hello,

This is my first post here, so be kind people :P

This is a guide on how I was able to get the USB IBurst Modem working on ubuntu 11.10 with the newest kernel installed.

I searched high and low for a solution, however I saw no posts mentioned about this.

Anyways, here is what you should do.

Prior to compiling we will need the following prerequisites: 

build-essential, gcc-4.6, libc6 and linux-headers-3.0.0-##-generic

Just install them by running the below:

```
sudo apt-get install build-essential gcc-4.6 libc6 linux-headers-3.0.0-12-generic 
```

Note: I was running here the 3.0.0-12 kernel, just change this to the appropriate kernel you are currently on. (You can check by typing uname -r)

After installing the pre-requisites, grab the newest drivers from sourceforge:

[http://sourceforge.net/projects/ibdriver/](http://sourceforge.net/projects/ibdriver/)

Now unpack the drivers, and go through the directory.

There are two files you will need to edit in order to get this to work:

the Makefile and the ib-net.c .

First edit the Makefile and remove the following line:

obj-m += ib-pcmcia.o

Note: If you wish, you can just Comment it out by adding # prior to it, thus making it like so:

#obj-m += ib-pcmcia.o

Save the file and close it, then edit the ib-net.c and search for the following line:

```
spinlock_t ib_lock = SPIN_LOCK_UNLOCKED;
```

Remove it, and replace it with: 

```
DEFINE_SPINLOCK(ib_lock);
```

Save the file and exit.

With the above done, you should be able to compile without further error, just open up a command prompt, browse to the extracted directory and run the following:

```
make && sudo make install
```

Enjoy! 

P.S: This guide is for USB only, I do not know how to make the pcmcia to work and this guide actually removes the pcmcia drivers from being installed the first place.

P.S 2: English is not my native tongue, so excuse the wrong sentence compositions.

---

### Post by Rocketmania on 2013-01-03
thanks so much for posting the 'fix' for the drivers.  After following the steps for installing the drivers for my kernel version, 3.2.0, running pppoeconf, and plugging in the modem, I see the following in syslog:

Jan  3 08:19:57 gd1 NetworkManager[1001]:    SCPluginIfupdown: guessed connection type (ib0) = 802-3-ethernet
Jan  3 08:19:57 gd1 NetworkManager[1001]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:ib0, type:802-3-ethernet, id:Ifupdown (ib0), uuid: 353e15fa-f276-690c-8c3a-e7609d1d3651
Jan  3 08:19:57 gd1 NetworkManager[1001]:    SCPlugin-Ifupdown: adding ib0 to iface_connections
Jan  3 08:19:57 gd1 NetworkManager[1001]:    SCPlugin-Ifupdown: adding iface ib0 to well_known_interfaces
Jan  3 08:19:57 gd1 NetworkManager[1001]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ib0, iface: ib0)
Jan  3 08:19:57 gd1 NetworkManager[1001]: <warn> /sys/devices/virtual/net/ib0: couldn't determine device driver; ignoring...

It looks like things are mostly working until I get the final warning message saying it 'couldn't determine the device driver'.

I'm not currently in range of any iBurst base stations, so I can't try connecting, but I do see the orange light on my modem (Kyocera model UTU03-1785D-US-A).

Does this warning mean that something is improperly configured?  Or something else?

Thanks in advance for your assistance!

---

