---
title: "Alfa AWUS036H ubuntu"
date: 2009-03-02
forum: Networking &amp; Wireless
---

### Post by rashwan on 2009-03-02
[SIZE="4"]Hello, 

Can anyone please explain how can i use the BT3 Driver
 
"Alfa AWUS036H (RTL8187L)" in Ubuntu 8.04 or 8.10 ?!

have been trying to get this card to work properly but no 

luck :(

Thanks[/SIZE]

---

### Post by rattking on 2009-03-02
Hey I posted about this a few days ago over here
[http://ubuntuforums.org/showthread.php?p=6805081#post6805081](http://ubuntuforums.org/showthread.php?p=6805081#post6805081)

and don't forget to add
 
blacklist rtl8187

to the file /etc/modprobe.d/blacklist
to disable the default ubuntu driver

edit. I forgot to explain that you wont be able to copy the bt3 driver and load it into ubuntu.. you will need to compile the driver for the ubuntu kernel

---

### Post by rashwan on 2009-03-02
does it work in Manage mode too ?! coz actually i can manage to get it to work in monitor mode

but in manage mode it drops every 1min.

Thanks Alot

---

