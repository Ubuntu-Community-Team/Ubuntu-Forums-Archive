---
title: "NFS take over on WIFI"
date: 2009-08-25
forum: Networking &amp; Wireless
---

### Post by DJJo on 2009-08-25
hello
i dit the [Installation OnNFSDriveWithLocalBoot]("https://help.ubuntu.com/community/Installation/OnNFSDriveWithLocalBoot") tutorial.
wehn i boot up i youse my cabel connection. 
but i want dat when i dit boot up dat my wifi take over my cabel connection.
i this possible?

and hou can i test my wifi connection. i dit ping but it is 0.04. is this to fast?

o jah.
my wifi card has has cals eth1_rename

---

### Post by dlmarti on 2009-08-25
I'm sorry, but I didn't understand a word of that.

What were you trying to achieve, and what are the problems your having now?

---

### Post by aromo on 2009-08-25
> **dlmarti said:**
> I'm sorry, but I didn't understand a word of that.

What were you trying to achieve, and what are the problems your having now?

Some kind of encryption, I'm pretty sure.

---

### Post by DJJo on 2009-08-25
> **dlmarti said:**
> I'm sorry, but I didn't understand a word of that.

What were you trying to achieve, and what are the problems your having now?

Sorry for my bad english

I boot up from network with a NFS share. with my eth0.

but when i boot up i want that my eth1_rename( my wifi connection) takes over. so i can unplug my cabel connection(eth0).

first i want to check my eth1_rename connection.
when i ping i get a answer. (0.04) but when i ping my localhost i get the same numbers (0.04)

---

### Post by dlmarti on 2009-08-25
> **DJJo said:**
> Sorry for my bad english

I boot up from network with a NFS share. with my eth0.

but when i boot up i want that my eth1_rename( my wifi connection) takes over. so i can unplug my cabel connection(eth0).

first i want to check my eth1_rename connection.
when i ping i get a answer. (0.04) but when i ping my localhost i get the same numbers (0.04)

If your root partition is a NFS share on your wired network, you can't unplug it without your system locking up.

What does 0.04 mean???

---

### Post by DJJo on 2009-08-25
> 

What does 0.04 mean???

0.04 ms is the ping speed.

---

