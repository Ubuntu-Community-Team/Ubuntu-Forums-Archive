---
title: "AMD drivers for 4550 HD graphics"
date: 2013-06-04
forum: Multimedia Software
---

### Post by coolname on 2013-06-04
Hello, I am new to Linux and Ubuntu, I have one fairly noobish question:

Do I need to install graphic drivers for my video card ? As title says it is 4550 HD AMD Radeon.

I actually tried installing 13.1 catalyst version, but I got some mesage that I am missing some headers.

Can anyone please guide me to this ? Problem is that fonts and graphics in some programs looks quite bad, so I am thinking it can be because I don't have drivers installed. I am using netBeans for web development, but fonts in it looks terrible.

P.S. Im using 13.04 version

Thanks

---

### Post by Mark Phelps on 2013-06-04
You can NOT install the restricted AMD drivers with that card and have them work with any Ubuntu version newer than 12.04.1.  Starting with Ubuntu 12.04.2, Canonical updated the X-server to a new version -- that is incompatible with the HD 2x/3x/4x-series drivers.  

One thing that you will learn about Linux is that the correct drivers are installed automatically.  Unlike with MS Windows, you don't hunt around for drivers or driver updates.

Unfortunately, now, you will have to remove the fglrx drivers. Instructions (for removing them) are in the link:  [https://help.ubuntu.com/community/RadeonHD]("https://help.ubuntu.com/community/RadeonHD")

---

### Post by coolname on 2013-06-04
Thanks you so much. So I already have correct drivers installed, so I do not need to worry ?

---

### Post by MidnightGrey on 2013-06-04
One of the best websites for working with AMD drivers in linux is this one: wiki.cchtml.com.
The guide you'll want to look at is this one for [Raring13.04](wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide).

The section regarding limitations on your 4550HD and how to downgrade to older Catalyst drivers is [HERE](http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx).

The section regarding removing (broken) Catalyst installs is [HERE](http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Removing_Catalyst.2Ffglrx).

For informations about the differences between AMD's Catalyst drivers vs Open Source drivers (the default in ubuntu), see this section [HERE](http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#The_Options).

---

### Post by Bucky Ball on 2013-06-04
*Thread moved to **Multimedia & Video**.*

Welcome to the forums. Enjoy them, the learning curve and the OS. ;)

---

### Post by Mark Phelps on 2013-06-05
Please note that the example given in the second link in post #4 will mot likely not work with your card.  The example in the link is a 6870 -- a much newer card than yours, one that will work with the Catalyst 13.4 drivers.

Also, strongly advise AGAINST using any links that will downgrade your X-server version to work with older drivers.  You're trading a short-term convenience for a long-term risk of serious instability in your install.

---

