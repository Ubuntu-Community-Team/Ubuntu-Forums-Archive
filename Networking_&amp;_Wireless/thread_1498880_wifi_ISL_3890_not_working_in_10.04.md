---
title: "wifi ISL 3890 not working in 10.04"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by DrScum on 2010-06-01
I have a wlan adapter working in 9.04 out of the box with the Intersil Corp. Prism GT driver. After a clean install of 10.04 the adapter is not working. How can I fix this? I am using Ubuntu for a while now but don't know the ins and outs of installing drivers and firmware yet.

---

### Post by DrScum on 2010-06-01
After an intensive search and some guided tours through my new system, it looks like the problem is the absence of the linux drivers nonfree package in 10.04. I did manage to download the package from the server (remember, no internet without wlan working) and copied it to the new system. How do I install it now? I have tried to follow various guidelines from various forums and how to's but they don't seem to work in 10.04.

What I do have is a the downloaded tar.gz file. I extracted it and now have a series of directories and subdirectories containing files and more subdirectories. 

I understand that I have to open a terminal, navigate to the folder with the source files and use the commands ./config, make and install. But to which folder to I have to navigate? So far all I got from ./config was :"no such folder" what I get from "make" is "no rules" or someting like that.

Help is appreciated.

---

### Post by chili555 on 2010-06-08
Are you still there? It will be a bit tricky to compile this package. I wonder if there isn't an easier way.

Please post:```
lspci -nn
```You can omit the parts not related to your wireless. You might also look at:```
dmesg | grep p54
```Is there any interesting message?

---

### Post by DrScum on 2010-06-08
Meanwhile I found a .deb version here
[http://mirror.informatik.uni-mannheim.de_1.8_all.deb](http://mirror.informatik.uni-mannheim.de_1.8_all.deb)
The adapter is up and running.

Thanks for your help.

---

