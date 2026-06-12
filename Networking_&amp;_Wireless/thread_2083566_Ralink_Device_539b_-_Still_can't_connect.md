---
title: "Ralink Device 539b - Still can't connect"
date: 2012-11-13
forum: Networking &amp; Wireless
---

### Post by davewhelchel on 2012-11-13
I still can't connect to my wireless router. You can reference the following link to see what I've tried so far [http://ubuntuforums.org/showthread.php?p=12349537#post12349537](http://ubuntuforums.org/showthread.php?p=12349537#post12349537). Btw, thanks for your efforts ahallubuntu. 

Not sure if I'm on the right track, but I downloaded the driver from [http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501), entitled RT539x PCIe based on the name of my hardware (or at least what I think is the name of my hardware).

david@Desktop:~$ lspci -nn | grep 0280
04:00.0 Network controller [0280]: Ralink corp. Device [1814:539b]

If someone could walk me through the setup process it would be greatly appreciated since I don't really know what I'm doing and I really don't want to go back to Windows...

---

### Post by ahallubuntu on 2012-11-13
Download the file (double .bz2 extension for some reason when I downloaded it; change ".bz2.bz2" to ".tar.bz2")

bunzip2 (downloadedfile.bz2)
tar xvf downloadedfile
(cd into new directory created)

There are instructions in the file "README_STA_pci" .

But once you have cd'ed into this directory (in a terminal window), try typing

```
sudo make
```

and follow the rest of the instructions in the readme file.

FYI, this drive is a year old and predates Ubuntu 12.04 by a while and may not necessarily work with the 3.0 kernel.

---

### Post by davewhelchel on 2012-11-13
Thanks for the reply. In the README_STA_pci file it gives the following instructions:

2> In Makefile
     define the linux kernel source include file path LINUX_SRC
     modify to meet your need.

I'm not sure exactly what line to change here and what I should change it to.

---

### Post by davewhelchel on 2012-11-15
Just to follow up on this, I installed Ubuntu 12.10 and everything worked. I was having trouble getting my speakers to work with 12.04 but this was also fixed by installing 12.10.

---

