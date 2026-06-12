---
title: "ndiswrapper"
date: 2013-03-24
forum: Networking &amp; Wireless
---

### Post by Hawkthorne1973 on 2013-03-24
I've been waiting for a solution to be eventually downloaded with system updates, but then I found this:

[https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/1132511](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/1132511)

Where the poster days SourceForge.net had a newer version of ndiswrapper that seemed to solve his problem. So I uninstalled Windows Wireless Drivers from the Ubuntu Software Center, and found:

[http://sourceforge.net/projects/ndiswrapper/?source=directory](http://sourceforge.net/projects/ndiswrapper/?source=directory)

I downloaded the file, unarchived it, and started to follow the Install directions. I amazed myself by getting to the point where I had to install the driver using:

ndiswrapper -i driver.inf

but when I did I received:

driver rt64win7.inf is already installed

So I found a page telling me how to uninstall drivers in terminal and typed

sudo ndiswrapper -e rt64win7.inf
and
sudo ndiswrapper -r rt64win7.inf

and both provided the result

couldn't delete /etc/ndiswrapper/rt64win7.inf: No such file or directory

And when I type

ndwrapper -l

I get 

rt64win7.inf : invalid driver

So...where to next? LoL

---

### Post by Hawkthorne1973 on 2013-03-24
Newbie mistake - it's case sensitive. I'm one step further. If I need more help, I'll ask again. :P

---

