---
title: "Installing and maintaining a ubuntu computer lab ?"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by chrisdee on 2009-08-28
Hello.

I know similare question has been posted befor but so far I have not found any answers that applies to this kind of setup.

I just startet in a new job at my home town university. One of my tasks is to maintain a computer lab with 8 machines currently running Ubuntu 8.10.
The guy who had the position befor me has as I understand setup things the following way :

- The 8 lab machines with Ubuntu are connected to a virual debian server (vmware).
- From this server the lab machines gets account username, password and home folder.
- The virtual debian server gets this information from the universitys central user database and ldab database.
- In addition the virual debian server push out ubuntu "images" to the lab machines (if in need of reinstall) from something called puppet.
- Lastly the lab machines are setup with a link to a windows terminal server from the ubuntu login menu. This is for students who wants to use windows instead of Ubuntu.


Ok I think I got down everything above. My first task is to update to Ubuntu 9.04. I'v started to manually updated via the Ubuntu update menu. So far I'v updated one machine just to check if everything goes ok. Looks good so far.

But I'm thinking it would be better to make a new image of 9.04 instead at push this out via network installation. As described above the guy befor me developed a system for this, but I find it very technical. I have a very little idea on how spesifically things are put together. Besides i think everything is done by shell wich I'm not so familiare with. I'v made images and snapshots on windows at school many years ago, but never on linux.


Im wondering if the described way (above) is the easiest and best way of doing things like this or are there more standarized ways install and maintain computerlabs like this ?

Maby anybody out here could point me to a "easy" step by step guide on how to do this the best way. 



Reguards
chrisdee

---

