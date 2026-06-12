---
title: "failing to establish connection to wireless network"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by amitkenny on 2009-11-09
I'm running ubuntu 9.10. since the 9.10 installation I couldn't establish connection through the wifi. It seems that hardware  and driver work fine, since the wifi network is recognized, but any attempt to connect it failed. 
It take more than 30 sec for the system to ask for password. but connection does not established. I tried removing the password from the router, and it still couldn't connect.
all this time, a laptop with virtually the same configuration successfully connect the net via wifi.
I already installed some packages offered in other  threads. It didn't change the situation.

---

### Post by Iowan on 2009-11-09
I've seen a couple of threads where setting **acpi=off** on the kernel line in menu.lst helped.

---

### Post by amitkenny on 2009-11-10
where the menu.lst file is located?

---

### Post by Iowan on 2009-11-10
In Jaunty (and before) it was in */boot/grub*. I haven't seen Karmic to know if the directory got changed to **grub2**.

---

### Post by amitkenny on 2009-11-12
I found the directory, but there is no such file in this directory. also "find" couldn't located any file with this name

---

### Post by bcpaes on 2009-11-12
try this in a terminal

> sudo gedit /boot/grub/menu.lst

but i have tha same problem and acpi doesent appear here

---

### Post by Iowan on 2009-11-12
> **bcpaes said:**
> but i have tha same problem and acpi doesent appear hereIt may default to "ON" if you don't say otherwise...

---

### Post by Iowan on 2009-11-16
> **amitkenny said:**
> where the menu.lst file is located?Grub2  file structure is described [here]("https://help.ubuntu.com/community/Grub2#File%20Structure").

---

