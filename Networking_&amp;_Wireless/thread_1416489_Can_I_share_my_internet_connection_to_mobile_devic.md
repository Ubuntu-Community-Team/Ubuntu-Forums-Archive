---
title: "Can I share my internet connection to mobile device by wifi?"
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by fourteenth on 2010-02-26
I was connected to internet by wired connection in my home.
I was able to share my Internet connection to other computer by proxy using squid.
My question is, Can I share my internet connection to mobile device by wifi?
I'm using ubuntu 9.10 in my laptop.

---

### Post by noway2 on 2010-02-26
Try to  manually configure your wifi on the laptop to associate it with a "network", ie give it an IP address and netmask.  Then configure squid to use that network as opposed to the wired on.

---

### Post by Sylslay on 2010-02-26
By wifi , You meant:

ad-hoc mode (link betwin 2 dev) from phone to wi-fi card,

or infrastructure mode.
from phone to home router.

---

### Post by fourteenth on 2010-02-27
> **noway2 said:**
> Try to  manually configure your wifi on the laptop to associate it with a "network", ie give it an IP address and netmask.  Then configure squid to use that network as opposed to the wired on.

I'm sorry, I'm new to linux..
how to do it?

> **Sylslay said:**
> By wifi , You meant:

ad-hoc mode (link betwin 2 dev) from phone to wi-fi card,

or infrastructure mode.
from phone to home router.

from your description, I want to do by ad-hoc mode.
I don't have router in my home.

---

### Post by noway2 on 2010-02-27
In the upper right corner of your screen, you will have an icon for network manager.  You will want to click that and select create new wireless network.

You will be prompted for a name, give it one.  For simplicity, at the start, select none for security.  Then click create.  This will create an ad-hoc network that defaults to computer-computer.  It may be enough to allow your devices to talk.  If not, you will need to right click on the network manager, select the ipv4 settings and create a network with an IP address, etc.  The ip address of each device must be different and the netmask must coincide.  For example, make your laptop 192.168.0.1 and your wireless device 192.168.0.2 and use a netmask of 255.255.255.0.

---

### Post by TwoD on 2010-07-14
This thread may also be of some use: [http://newyork.ubuntuforums.org/showthread.php?p=9588394](http://newyork.ubuntuforums.org/showthread.php?p=9588394) if you haven't already gotten it to work.

Just note that some mobile devices don't [yet] support ad-hoc mode at all.

---

### Post by maxsujoy on 2011-12-31
> **TwoD said:**
> This thread may also be of some use: [http://newyork.ubuntuforums.org/showthread.php?p=9588394](http://newyork.ubuntuforums.org/showthread.php?p=9588394) if you haven't already gotten it to work.

Just note that some mobile devices don't [yet] support ad-hoc mode at all.

[TwoD]("http://ubuntuforums.org/member.php?u=410469") : Can you provide any clues on how to achieve this in Infrastructure Mode?? I'm running Lucid

---

