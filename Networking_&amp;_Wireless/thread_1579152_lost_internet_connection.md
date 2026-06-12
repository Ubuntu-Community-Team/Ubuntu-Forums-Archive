---
title: "lost internet connection"
date: 2010-09-21
forum: Networking &amp; Wireless
---

### Post by shallowthought on 2010-09-21
After a shutdown I lost internet connection.
Did the right click to try to enable networking. Didn't work
Tried:
     sudo service network-manager stop
     sudo rm /var/lib/NetworkManager/NetworkManager.state
     sudo service network-manager start

still no connection
did reboot  still no connection

I barely computer literate.
Help!

using Ubuntu 64 bit

---

### Post by Iowan on 2010-09-21
More threads to check:
[http://ubuntuforums.org/showthread.php?t=1537792]("http://ubuntuforums.org/showthread.php?t=1537792")
[http://ubuntuforums.org/showthread.php?t=1484913]("http://ubuntuforums.org/showthread.php?t=1484913")

---

### Post by shallowthought on 2010-09-22
> **Iowan said:**
> More threads to check:
[http://ubuntuforums.org/showthread.php?t=1537792](http://ubuntuforums.org/showthread.php?t=1537792)
[http://ubuntuforums.org/showthread.php?t=1484913](http://ubuntuforums.org/showthread.php?t=1484913)

Thanks for the reply. 
From the first forum, when I do

sudo lshw -C network > lshw.txtI get very briefly,

PCI (sysfs)

which disappears and then I get back the prompt.
Don't know what it means.

---

### Post by shallowthought on 2010-09-22
By the way I am wired to a router with no wireless. But the applet on the upper panel shows a wireless icon with
a red line through it. And there is no "up down" arrow signifying a hard wired connection.

I tried to ping ubunto.com without success.
I can ping 127.0.0.1 successfully, which I guess means the ethernet cable is okay?

---

### Post by shallowthought on 2010-09-22
After fruitless hours, I solved the problem by ----  turning off the router, and then back on again.
It restored the internet connection.

Which leads me to two questions:

1 Is there a (ubuntu) site for ignorant people like me to go to get a list of things to try in order
to get things working in such cases? Turning the router off and on again would probably be near the top of the list!

2. I am running 10.04 64 bit. Two other computers were connected to the same router: a Windows
machine and an old Dell running Ubuntu 10.04 32 bit. Neither of these had the problem. The 32 bit has run
flawlessly for several months.
It is my impression that the 64 bit system is less stable than the 32 bit.
Is that true?

---

