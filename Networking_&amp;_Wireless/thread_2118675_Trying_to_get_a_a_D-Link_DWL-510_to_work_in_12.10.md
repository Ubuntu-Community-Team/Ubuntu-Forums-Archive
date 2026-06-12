---
title: "Trying to get a a D-Link DWL-510 to work in 12.10"
date: 2013-02-21
forum: Networking &amp; Wireless
---

### Post by Tommy The Cat on 2013-02-21
trying to install this card has been a real thorn in my side. I just put together a new kit and it's running splendidly except that I decided to use the wireless card that I had installed in a Dell ages ago. 

The card is an AirPlus G DWL G510. Reviewing the lit, it seems there's several versions of this card and according to the "lspci -nn" command it's the one that uses RTL8111/8168B drivers. I've got the drivers installed (did the autorun.sh file) and even took a couple of extra steps according to these guides 

[http://mutap.wordpress.com/2012/04/15/ubuntu-11-10-and-realtek-rtl81118168b-network-problems/](http://mutap.wordpress.com/2012/04/15/ubuntu-11-10-and-realtek-rtl81118168b-network-problems/)
[http://ubuntuforums.org/showthread.php?p=10283670](http://ubuntuforums.org/showthread.php?p=10283670)

But I still can't connect to my wireless network. What am I missing here?

---

### Post by ahallubuntu on 2013-02-22
~

---

### Post by varunendra on 2013-02-23
> **ahallubuntu said:**
> You'll get better response posting this in the Networking and Wireless forum; maybe an admin will move it there.
Done! :)
*Thread moved to **Networking & Wireless**.*

> **ahallubuntu said:**
> I don't think RTL8111/8168B is your wireless card - I think that's for wired ethernet.
+1
The mentioned chip is for Ethernet interface.

For exact identification of the card chip and possibly associated driver with it, please post output of -
```
lspci -nnk | grep -iA2 net
```

---

