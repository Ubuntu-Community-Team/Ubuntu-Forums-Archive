---
title: "Can't Access 2nd &amp; 3rd Drives via Network"
date: 2010-11-10
forum: Networking &amp; Wireless
---

### Post by onaridge on 2010-11-10
I have a  Dell XPS with Ubuntu 10.04 installed. I have a laptop dual booting Windows 7 and Ubuntu 10.04. I can see all shared folders on the Dell from my Windows partition in my laptop but can only see the shared folders in Home on the Dell from my Ubuntu partition in the laptop. My set up is as follows:

Dell:

root, home and swap are on the 1st 160g hard drive. 
2nd 160g hard drive has only the one partition: /storage1
3rd hard drive, 500g has only one partition: /storage2

I cannot access any of the shares on either storage drive but I can see them from the ubuntu laptop. What I want to do is have access to those storage drives from my laptop. If I go into Nautilus, navigate to either storage drive, I cannot share them via right click, properties because I don't have root. Basically I am not sure how to go about this. There are a few folders in storage 1 and storage 2 that I want to be able to access from my Ubuntu partition in my laptop. This is one of the reasons I still have Windows on the other laptop partition but I really would like to dump it. :-) Samba is installed and I tried giving permissions that way. It allowed me to add the drives but it had no effect.

---

