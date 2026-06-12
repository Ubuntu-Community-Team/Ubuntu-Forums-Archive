---
title: "How do I get apt-get so I can build my wireless driver to connect to the internet"
date: 2013-08-11
forum: Networking &amp; Wireless
---

### Post by tim6 on 2013-08-11
Hello all,

I have installed Ubuntu (12.04) in VirtualBox a couple of times with success, but now I am trying to install it (12.04) by itself on my harddrive. I successfully made partitions, and installed from PENDRIVE and am looking at the desktop but I don't have an internet connection because of a driver issue.

I need to build this driver: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

but in the README some of the instructions involve apt-get like: apt-get install linux-headers-generic which isn't working.

What's the best way to go about building this driver?

Thanks

---

### Post by davetv on 2013-08-11
From the readme file - 
> 
PRECOMPILED DRIVER
-------------------
Some distros (Ubuntu and Fedora at the least) already have a version of
this driver in their repositories precompiled, tested and ready to go.
You just use the package manager to install the proper package.  If
its available for your distro, this is usually an easier solution. See
the end of this document for further discussion.


You shouldn't need to build it.

---

### Post by Bucky Ball on 2013-08-11
*Thread moved to **Networking & Wireless**.*

Welcome. Please open a terminal (Applications>Accessories>terminal) and paste this in:

```
sudo lshw -C network
```

Post the result back here (I know this might be difficult but perhaps put a text file of it on a pendrive and swap it across to the machine that's online).

You might be going for a bit of Windows think and jumping the gun here by thinking you need to install a driver for this. Maybe not. The output of that command will tell us more. 

(How old was the web page you got your info from regarding this and what release of Ubuntu was it talking about? Things can change radically (or not) from one release to the next.)

Note: Yep, just checked your link. The STA drive has been in the kernel for a looong time now and the page you are looking at is somewhat redundant. Catch 22: You might need to be online with a cable to get it working. (If you could get online with a cable your problems would be over in a jiff, I don't doubt. apt-get in this instance is asking you to 'apt-get install' from an online source. For now, forget it. 'apt' is already installed on your machine and if you 'apt-get' ting and nothing is happening, it's because you're not online.)

Just a further note on this; the B43 drivers should work, if not better, just as well. There is a way to install either the STA or B43 drivers (can't remember which) without being online. You might need to dig. You use the CD (they are on there already). 

Broadcom cards were once a nightmare, now they are generally a breeze (and often work out of the box). This is where the confusion comes in for new users. They see an old thread regarding Broadcom and leap to the confusion/conclusion they are still a nightmare. They are now one of the best supported. 

Good luck.

---

### Post by ibjsb4 on 2013-08-11
Why can't you just use the driver in the software center?

[ATTACH=CONFIG]245297[/ATTACH]

---

### Post by Bucky Ball on 2013-08-11
> **ibjsb4 said:**
> Why can't you just use the driver in the software center?

[ATTACH=CONFIG]245297[/ATTACH]

OP not online on that machine ...

As mentioned, connecting a cable would make this much easier. Also, the drivers should be there and available to enable (if not already enabled) in Additional Drivers without going near using SCentre. If they're not, an update should get them there. Again, need to be online to do either.

---

### Post by ibjsb4 on 2013-08-11
Yep, plug it it and download.  Done deal :)

---

### Post by tim6 on 2013-08-12
Thanks for the replies everyone. Couple of things: I can't use the software center because I'm not connected to the internet, and also when I go into "additional drivers" nothing shows up.

This is the output from sudo lshw -C network:

>   *-network       description: Wireless interface
       product: BCM4321 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:03:09.0
       logical name: eth2
       version: 01
       serial: 00:1e:e5:f9:ae:02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) latency=32 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:cfef4000-cfef7fff


Also, I want to try an offline solution first before I lug my rig down two flights of stairs to connect to ethernet >.>

Where can I find the correct driver on the PENDRIVE I installed from? Buckyball you said that I might need to dig, could you point me in the right direction?

Thanks

---

### Post by tim6 on 2013-08-12
Got it working! For posterity... I used this wiki:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)

After installing **b43 (12.04 Precise Pangolin) **follow the instructions under "Switching between drivers" and do "[COLOR=#333333][FONT=UbuntuMono]sudo modprobe b43"
[/FONT][/COLOR]

---

### Post by Bucky Ball on 2013-08-12
You found it. Well done and good digging. I've had a busy day so haven't been about.

As I was saying, Broadcom were a PAIN when I first got into Ubuntu/Linux in 2007. I had a HP with a Broadcom card and had to jump through hoops to get it going. Generally, the awful and superceded ndiswrapper was the only solution (at least for mine). B43 crept up and changed all that. Broadcom are now one of the most well supported cards and Broadcom generally play nice now.

When a piece of hardware is *very* new, regardless of the manufacturer, it can take awhile for the Linux world to catch up unless the manufacturer decides to provide open-source software, or at least open the code for devs to tweak with.

Otherwise it's experimentation until it's working. 

Good luck. ;)

---

