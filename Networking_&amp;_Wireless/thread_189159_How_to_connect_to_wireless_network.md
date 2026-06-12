---
title: "How to connect to wireless network"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by android6011 on 2006-06-04
I can detect the wireless network and everything, I have all the info, but I dont know how to connect. Can someone tell me the commands to do so? Im not a big fan of apps that do it for me so the commands will do. Thanks

---

### Post by s31523 on 2006-06-04
Install Network Manager.  Search the forum for this, there are many, many posts regarding this.

---

### Post by android6011 on 2006-06-05
The manager doesnt work, it is an open network with no password, the icon says connecting but it never does, eventually it stops and returns to the not connected symbol. I am using the bcm43xx drivers for the broadcom 4318. I can scan and use airodump, but not connect to the router.

---

### Post by s31523 on 2006-06-05
If you click on the icon does it show your network in the pull-down?  your /etc/network/interfaces file has been modified per other posts, right?

---

### Post by android6011 on 2006-06-05
Yes, it shows the network. As far as the interfaces file, I tried adding things that were suggested, and commenting things out as suggested and none seem to help, what do you reccommend?

---

### Post by android6011 on 2006-06-05
The following appears in dmesg when I try to connect using the network manager:

bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR

---

### Post by s31523 on 2006-06-06
Have you checked out:
[https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx)

There is a section on Dapper and broadcomm

Also I found this post, which is not very specific, but maybe will point you on the path.. Good luck!:
[http://blog.philkern.de/archives/172-bcm43xx-wireless.html](http://blog.philkern.de/archives/172-bcm43xx-wireless.html)

---

