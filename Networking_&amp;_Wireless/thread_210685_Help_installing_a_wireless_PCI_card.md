---
title: "Help installing a wireless PCI card"
date: 2006-07-07
forum: Networking &amp; Wireless
---

### Post by mercat on 2006-07-07
Apologies up front for asking what I'm sure has been asked many times before, but.... 

....how do I install a driver for my wireless PCI card (Zonet ZEW1601) under the Ubuntu Linux environment? Zonet offers no Linux-specific driver. When I asked, Zonet tech support responded by directing me to the maker of the chipset for the card (RALink.com) and gave me this guidance:

"If customers want to install the ZEW1601 on Linux box, the customer should compile the kernel with the driver download from the chipset manufacture on customer's own risk." 

I'm a newby to Linux and this is mostly meaningless to me. What do they mean by "...compile the kernel with the driver download..."? Can anyone either A) provide specific steps to get Linux to recognize my ZEW1601; or B) point me in the direction of novice instructions somewhere on the 'net to do this? 

Thank you. 
mercat

---

### Post by sunny007 on 2006-07-07
Hi,

I have the same issue. I am trying to resolve the same. However, I have different wireless card. I have Zyxel G-302 wireless card.

Have you downloaded the driver from chipset manufacture? If so, if it tar file the untar it or there might be makrdrv, make or install file that you have to run. It will place you driver in right directory for you.

Also, don't forget to read readme file you have with downloaded driver.

I am also new to this and learning stage. This may help you figure out some thing.

Have you hooked up the card? If so, is it detected?

Thanks! and Good luck..

---

### Post by joplass on 2006-07-07
I am probably to ignorant to have knowledge of your wireless cards.  But you should probably try installing ndiswrapper and ndisgtk with synaptic.

---

### Post by kc5hwb on 2006-07-08
I had a Netgear WG311 v2 card in my box when I first installed Ubuntu but I never could get it to work.  The OS recognized the card and I could activate it in the Networking Admin section, but it never would see my network.  I even installed Wireless Setup, an app I got from the Synaptic Package Manager, but to no avail.

Someone at work told me that the Airlink 101g cards worked well with Linux, so I went and got one of these today, in USB, but I can't even get Ubuntu to recgonize this card.  I am sure that I am doing something wrong, so I will keep jacking with it.

---

### Post by mercat on 2006-07-08
Thanks, all, for the responses. Ubuntu does seem to detect the card and even picked up the ID of my network, but it won't connect. The chipset manufacturer does offer a Linus .tar file for a driver, but I'm unfamiliar with the whole process of makfile, etc. I'll have to do a little more research, I guess.

mercat

---

### Post by kc5hwb on 2006-07-08
I found this good resource for help with installing a PCI carrd with ndiswrapper.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Install_Windows_driver](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Install_Windows_driver)

---

### Post by arunsub on 2006-07-25
I have bought Zonet ZEW1602 (PCI) and installed it in my desktop. Ubuntu Dapper didn't recognize the card. I installed network manager and ndiswrapper-utils and that didn't help. I then tried what was given at the start of this thread and that too didn't help. I then tried this link [http://doc.gwos.org/index.php/Rt2x00drivers](http://doc.gwos.org/index.php/Rt2x00drivers) . It didn't help. Does anyone have any idea?
ps: I already have 2 ethernet port in the computer. One is built in and the other one is PCI. The built in one is disabled and I'm using the 2nd one for wired connection.

---

