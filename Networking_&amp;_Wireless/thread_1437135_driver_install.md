---
title: "driver install"
date: 2010-03-23
forum: Networking &amp; Wireless
---

### Post by DJ . on 2010-03-23
I have ubuntu 10.04 beta with no partitions on my hp pavilion dv5000z. I can't get online because my networking driver is not installed. ([http://www.linlap.com/wiki/hp+pavilion+dv5000z](http://www.linlap.com/wiki/hp+pavilion+dv5000z) for specs) How do I install it?

---

### Post by bkratz on 2010-03-23
> **DJ . said:**
> I have ubuntu 10.04 beta with no partitions on my hp pavilion dv5000z. I can't get online because my networking driver is not installed. ([http://www.linlap.com/wiki/hp+pavilion+dv5000z](http://www.linlap.com/wiki/hp+pavilion+dv5000z) for specs) How do I install it?




First thing we need to do is find out what wireless card you have. In the terminal (Applications>>Accessories>Terminal) and copy paste the output of

lspci | grep Network

That is LSPCI in lowercase, N in upper)

If you receive no output, copy paste the output of 

lspci

back here.

---

### Post by DJ . on 2010-03-23
dj@dj-laptop:~$ lspci | grep Network
06.02.0 [COLOR=Red]Network [COLOR=Black]controller: Broadcom Corporation[/COLOR][/COLOR] BCM4318 [AirForce  One 54g] 802.11g Wireless Lan Controller (rev 02)

---

### Post by bkratz on 2010-03-23
> **DJ . said:**
> dj@dj-laptop:~$ lspci | grep Network
06.02.0 [COLOR=Red]Network [COLOR=Black]controller: Broadcom Corporation[/COLOR][/COLOR] BCM4318 [AirForce  One 54g] 802.11g Wireless Lan Controller (rev 02)

See this page and follow the directions about 2/3rd the way down under the heading "Ubuntu/Debian"  The whole page is quite good

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

---

### Post by DJ . on 2010-03-23
thanks but it doesn't say how to install it. It tells be to download and install but I can't I have no internet

---

### Post by bkratz on 2010-03-23
> **DJ . said:**
> thanks but it doesn't say how to install it. It tells be to download and install but I can't I have no internet

I believe it is also on the live CD, but you will have to find it! Set the CD as one of your sources. Directions can be found for (under the b43 section of this thread) when you don't have wired access.

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by DJ . on 2010-03-23
> **bkratz said:**
> I believe it is also on the live CD, but you will have to find it! Set the CD as one of your sources. Directions can be found for (under the b43 section of this thread) when you don't have wired access.

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)
I looked at that page and did everything but I couldn't find "bcmwl-kernel-source"

---

### Post by bkratz on 2010-03-23
> **DJ . said:**
> I looked at that page and did everything but I couldn't find "bcmwl-kernel-source"

First of all the b43 section wanted

```
b43-fwcutter
```

the other one was for different devices, remember the first web site I sent you to?

Secondly do you know how to invoke synaptic package manager?  If you do and change the sources to include the CD you can use the find function built in. IF you don't post back and I will give you details.

---

### Post by DJ . on 2010-03-23
> **bkratz said:**
> First of all the b43 section wanted

```
b43-fwcutter
```the other one was for different devices, remember the first web site I sent you to?

Secondly do you know how to invoke synaptic package manager?  If you do and change the sources to include the CD you can use the find function built in. IF you don't post back and I will give you details.
I found it but it failed to install. Also my driver is supported.

---

### Post by bkratz on 2010-03-23
> **DJ . said:**
> I found it but it failed to install. Also my driver is supported.

Sorry, i don't understand what you are saying.  How did you try to install it and what does my driver is supported mean?

---

### Post by DJ . on 2010-03-24
> **bkratz said:**
> Sorry, i don't understand what you are saying.  How did you try to install it and what does my driver is supported mean?
I installed it by looking it up in package manager and marked it for installation. Press apply and showed an error message. 
14e4:4318 
   supported 
   BCM4318 
   b/g 
   G 
   b43 
this is from the first site you gave me.

---

### Post by DJ . on 2010-03-25
Anybody Have any suggestions?
It might be too late to say this but I can't get to a wired connection.

---

