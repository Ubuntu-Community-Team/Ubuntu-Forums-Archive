---
title: "Networking Framework gone"
date: 2013-01-17
forum: Networking &amp; Wireless
---

### Post by 404usernotfound on 2013-01-17
Hello Ubuntu Forums,
First things first:
Ubuntu 12.04 
64 bit
No internet access, but can flash drive for command lines/files
Would be happy to provide any other information you need.

I switched to Ubuntu this summer and I have loved every aspect of the switch from Windows 7; however, I finally ran into a problem that I cannot fix.

As the title states, my entire networking software/framework/whatever the official name for it is....is totally gone. This happened after I removed Firestarter, which I probably should not have done. 

I did not want to resort to making a new thread but I've spent many hours trying to resolve this myself to no avail. I've tried just searching for the specific framework my version of Ubuntu uses and installing the .tar, when that didn't work I tried a .deb, that didnt work either. I do not want to resort to reinstalling Ubuntu, but if that would be the easiest solution, so be it.

Would and of you kind souls please help a new Ubuntu user?

Thank you

---

### Post by steeldriver on 2013-01-17
Hello and welcome

If you only hosed network manager, then there's a good chance you will be able to bring up an internet connection manually either by editing the /etc/network/interfaces file or on the command line using ifconfig (or 'ip link set ...'). If that works you can then reinstall the missing bits.

---

