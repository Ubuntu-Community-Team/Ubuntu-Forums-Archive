---
title: "Tenda W522U wireless usb adapter"
date: 2012-12-31
forum: Networking &amp; Wireless
---

### Post by pancho45 on 2012-12-31
I just bought Tenda 300mbps dual band wireless n usb adapter model W522U and i'd like to learn how to install linux driver.It came with a cd and there is a linux driver but i do not know how to install it.Could you please teach me the steps to install driver.Thanks.

---

### Post by mamamia88 on 2012-12-31
does the cd contain the linux driver or do you just know there is one out there somewhere?  did you google the actual card?  in linux drivers are often included in the kernel you just need to sometimes manually activate them.

---

### Post by Kirk Schnable on 2012-12-31
> **mamamia88 said:**
> does the cd contain the linux driver or do you  just know there is one out there somewhere?  did you google the actual  card?  in linux drivers are often included in the kernel you just need  to sometimes manually activate them.
From what pancho45 said, I gather there are drivers on the CD he got with his card.

> **pancho45 said:**
> I just bought Tenda 300mbps dual band wireless n usb adapter model W522U and i'd like to learn how to install linux driver.It came with a cd and there is a linux driver but i do not know how to install it.Could you please teach me the steps to install driver.Thanks.
Sure, but we need to know what kind of installer they gave you.

What do you have? 
- A folder full of tons of files?  (Probably needs to be compiled.)
- A .deb file? (to install:  sudo dpkg -i filename.deb)
- A binary file?  (to install:  sudo ./binary)

Did they give you a README file?  Even if you don't understand it, you could post it in a Quote or Code box and we should be able to tell you what to do from there.

---

### Post by monkeybrain2012 on 2012-12-31
According to this the driver rt2800usb should work

[http://wikidevi.com/wiki/Tenda_W522U](http://wikidevi.com/wiki/Tenda_W522U)

rt2800usb is part of the Linux kernel but not enabled by default before 12.10.

Here is how you can activate it.
[https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M](https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M)

I followed the guide to enable W311M and it works quite nicely.

---

### Post by pancho45 on 2012-12-31
> **mamamia88 said:**
> does the cd contain the linux driver or do you just know there is one out there somewhere?  did you google the actual card?  in linux drivers are often included in the kernel you just need to sometimes manually activate them.

there is a driver in the cd:There is a folder named Linux and inside this folder:2010_0915_RT3572_Linux_STA_V2[1].4.0.2.tar
I'm just ignorant whene it comes to work with tar file.Thank you
guys for taking the time to help me.

---

### Post by 3rdalbum on 2012-12-31
> **pancho45 said:**
> there is a driver in the cd:There is a folder named Linux and inside this folder:2010_0915_RT3572_Linux_STA_V2[1].4.0.2.tar
I'm just ignorant whene it comes to work with tar file.Thank you
guys for taking the time to help me.

You don't need to install the driver. It has come with Ubuntu since 2011, maybe earlier. Just plug in your device, wait a few seconds for Networrk Manager to scan for networks, and then connect.

---

### Post by pancho45 on 2013-01-18
> **monkeybrain2012 said:**
> According to this the driver rt2800usb should work

[http://wikidevi.com/wiki/Tenda_W522U](http://wikidevi.com/wiki/Tenda_W522U)

rt2800usb is part of the Linux kernel but not enabled by default before 12.10.

Here is how you can activate it.
[https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M](https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M)

I followed the guide to enable W311M and it works quite nicely.

thanks it worked just had to change 148f 5370 to 148f 3572 which is id for W522U and it worked thanks again

---

