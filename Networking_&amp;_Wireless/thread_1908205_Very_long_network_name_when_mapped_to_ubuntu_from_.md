---
title: "Very long network name when mapped to ubuntu from XP"
date: 2012-01-12
forum: Networking &amp; Wireless
---

### Post by alchemist7107 on 2012-01-12
Hi all,
 
Sorry for been a noob on this and apologize if this qns has been asked.
 
Setup:
Ubuntu Server 11.04 / Ubuntuserver(hostname) with the IP: 192.168.102.248
 
Shared folder name "Public" with the comments "Public shared folder"
 
-----------------------------------------------------------------------------------------
 
From Client Machine - Windows XP Professional SP3
I type "[\\ubuntuserver]("file://\\ubuntuserver")" or \\192.168.102.248" on the explorer
 
New windows pop up and i see the shared folder call public with the comments as above.
 
When i map the "Public" Shared folder to Z: drive, the system give me a very long network name(below):
 
**Public on 'ubuntuserver server (Samba, Ubuntu) (192.168.102.248 '(z: )**
 
I create couple of other shared folder with different name and mapped it to another drive letter, result is still the same.
 
**Test on 'ubuntuserver server (Samba, Ubuntu) (192.168.102.248'(y: )**
**Ops on 'ubuntuserver server (Samba, Ubuntu) (192.168.102.248'(X: )**
 
 
[SIZE=2]Is it possible to have a shorter netwrk drive name i.e "Public on ubuntuserver(z: ) upon after the completion of mapping? like [/SIZE][SIZE=2]those done in windows between pc to pc or pc to server example: "Shareddocs on 'Asuspc'(P: )[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]Please advise [/SIZE] [SIZE=2]& thanks in advance[/SIZE]

---

### Post by varunendra on 2012-01-14
First, welcome to the forums! ;)

Now some business-
> **alchemist7107 said:**
> [SIZE=2]Is it possible to have a shorter netwrk drive name i.e "Public on ubuntuserver(z: ) upon after the completion of mapping?[/SIZE][SIZE=2][/SIZE]
Sure it is possible! Just click the mapped drive > press F2 (or right-click > rename) >> then change the name to what you want.

---

