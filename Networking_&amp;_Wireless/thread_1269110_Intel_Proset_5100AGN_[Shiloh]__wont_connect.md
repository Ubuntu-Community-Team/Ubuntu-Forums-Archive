---
title: "Intel Proset 5100AGN [Shiloh]  wont connect"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by TheHardWinter on 2009-09-17
Okay, it took me about two days to code the wireless card to actually turn on, and now its visible, and the drivers are installed.  
Using the network manager (GNOME) it finds like 13 networks.  (better than it did with vista prem) However when i try to connect to any of them.  It tries forever, and then says wireless disabled.  
also im not sure how to write and file startup code.  so i have to activate it every login with the following code. 

sudo modprobe -r iwlagn 
sudo modprobe iwlagn 11n_disable=1 11n_disable50=1


and then it recognizes the networks but wont connect.  

Running a Lenovo Laptop
Sys: 2x Intel (R) Core(TM)2 Duo CPU   P8400 @ 2.26GHz
3040MB (630MB used)
Karmic Koala 9.10 Development Branch


also have vista home prem.  on a partition

any help would be great.  i have a total of about 1 year ubuntu experience....so be gentle haha

---

