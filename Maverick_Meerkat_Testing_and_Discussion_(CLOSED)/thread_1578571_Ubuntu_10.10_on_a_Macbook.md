---
title: "Ubuntu 10.10 on a Macbook"
date: 2010-09-20
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Mokbi on 2010-09-20
Hello Ubuntu Forums,
I am new and this is my first time installing Ubuntu on my Macbook. I want to install it so that I can dual-boot Mac OS X with Ubuntu 10.10 and I am facing a problem. When I pop in the CD and boot from it and try to install Ubuntu, it gives me the choice of either wiping my hard drive and installing Ubuntu (I wanna keep my Mac partition) or opening the advanced partition editor. :confused::confused: :guitar::guitar::guitar:

How can I set up dual boot? I am running Snow Leopard so I have Disk Utility and Boot Camp Assistant. Here's my hardware Overview: :guitar::guitar::guitar:


  Model Name:	MacBook
  Model Identifier:	MacBook2,1
  Processor Name:	Intel Core 2 Duo
  Processor Speed:	1.83 GHz
  Number Of Processors:	1
  Total Number Of Cores:	2
  L2 Cache:	2 MB
  Memory:	2 GB
  Bus Speed:	667 MHz
  Boot ROM Version:	MB21.00A5.B07

---

### Post by danbuter on 2010-09-20
10.10 is still in Beta, so I recommend waiting until it is finally released before attempting an install. You could really screw up your hardrive if something goes wrong during the testing process. 

I also think you have to use a Mac specific program to install another OS on your macbook, though I can't remember off the top of my head what it is called.

---

### Post by Calash on 2010-09-20
10.10 is still in development and should not be used on production systems until it's release next month.

That being said I believe you will need to resize the partition first in OSX.  Then from Ubuntu you can use the advanced partitioning to use the now free space for the install.

I have not tried it myself but I think it should work.  Probably best to wait for somebody who has done it to chime in, or check out the Apple sub-forum.

---

### Post by Dustin2128 on 2010-09-20
> **danbuter said:**
> I also think you have to use a Mac specific program to install another OS on your macbook, though I can't remember off the top of my head what it is called.
It's called bootcamp. Not sure about linux support though. And I'd definitely use lucid (10.04) instead of maverick, it's a LTS release and they tend towards the stable.

---

### Post by vgrisham on 2010-10-05
> **Mokbi said:**
> Hello Ubuntu Forums,
I am new and this is my first time installing Ubuntu on my Macbook. I want to install it so that I can dual-boot Mac OS X with Ubuntu 10.10 and I am facing a problem. When I pop in the CD and boot from it and try to install Ubuntu, it gives me the choice of either wiping my hard drive and installing Ubuntu (I wanna keep my Mac partition) or opening the advanced partition editor. :confused::confused: :guitar::guitar::guitar:

How can I set up dual boot? I am running Snow Leopard so I have Disk Utility and Boot Camp Assistant. Here's my hardware Overview: :guitar::guitar::guitar:


  Model Name:    MacBook
  Model Identifier:    MacBook2,1
  Processor Name:    Intel Core 2 Duo
  Processor Speed:    1.83 GHz
  Number Of Processors:    1
  Total Number Of Cores:    2
  L2 Cache:    2 MB
  Memory:    2 GB
  Bus Speed:    667 MHz
  Boot ROM Version:    MB21.00A5.B07

It can indeed be done through a couple of routes. Boot Camp can only handle two operating systems, so if you're using Windows also, you'll need to use rEFIt or install Ubuntu within Windows using WUBI. My Macbook Pro 5,3 triple boots using Windows and WUBI, and I love it. 

Check out [this page]("https://help.ubuntu.com/community/MacBook"). Enjoy.

---

### Post by hollowtd on 2010-10-09
I can help you and send some nice links if you let me know. I have a macbook 1.1 and use rEFIT. I love it so let me know if you'd like specific help.

---

