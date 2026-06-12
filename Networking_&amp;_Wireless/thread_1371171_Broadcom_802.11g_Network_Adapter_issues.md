---
title: "Broadcom 802.11g Network Adapter issues"
date: 2010-01-03
forum: Networking &amp; Wireless
---

### Post by drackor1991 on 2010-01-03
Basically a few weeks ago I decided to try Linux, in particular Ubuntu. I have it installed in my Windows 7 partition but now I am willing to take the full plunge and switch to it all the way. The only issue is I cannot connect to wireless internet. It states "device not ready". Wireless is turned on on my laptop, I am very near the source, have tried making a manual connection with the network setup. I tried the hardware tester and it found my ethernet and wireless hardware (Broadcom 802.11g Network Adapter). 
I went to the package thing and looked for Broadcam. I found a package but it was already installed. I tried it manually with:


sudo apt-get install bcmwl-modaliases
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I then heard to try "sudo apt-get install bcm43xx-fwcutter" and did but it couldnt find it.



As stated before I am new to linux so I'm probably missing something easy
I just beg your patiance as I learn this new operating system.

---

### Post by mehta on 2010-01-03
I had probably the same problem when I replaced Windows XP on my laptop with Ubuntu 9.04. The built in Broadcom wireless adapter stopped working.  During the process of troubleshooting I happened to plug in a USB wireless adapter and was pleasantly surprised to see that a connection was established with the Internet.  Once the laptop was on line I could of course run system updates.  Then a couple of days later the system automatically reported that a new Broadcom driver, albeit an unsupported one had been found and if I would like to use it.  When I accepted that, the adapter inside the laptop started working and I did not need the USB adapter any more.
When I upgraded to 9.10 the same story unfolded again. 
It is a fortuitous rather than a well researched solution but it works.  So if you can lay your hands on a USB adapter the way forward will be easy.

---

### Post by jbergsing on 2010-01-03
This sounds like an easy solution to my wifi issues. Which USB adapters work best?

---

### Post by mehta on 2010-01-03
I had used EDUP Wireless USB adapter 54M

---

### Post by bkratz on 2010-01-03
> **jbergsing said:**
> This sounds like an easy solution to my wifi issues. Which USB adapters work best?

There are other solutions available, some of which are already on the live cd, but it depends on which Broadcom card you have. If you go to the terminal Applications>>Accessories>>Terminal and type in 
lspci -nn   (that is LSPCI in lowercase)

It should tell you what your card is. If not copy\paste the outputs back here for decoding.

---

