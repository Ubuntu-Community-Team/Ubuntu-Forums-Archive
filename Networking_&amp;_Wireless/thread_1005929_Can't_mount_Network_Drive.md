---
title: "Can't mount Network Drive"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by phillip181 on 2008-12-08
Help and thanks to those of you that can. 

I have troubling getting access to shares on both my Windows computer and my NAS (MediaVault). I can ping them and they show up in Nautilus, but when I click on them to access the drives, this is what appears. 

Sorry, could not display all the contents of "Windows shares on desktop": DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Anybody got any ideas?

---

### Post by tvtech on 2008-12-08
do you have samba or... nfs installed? if no samba, no windows shares.

you can install it via terminal 

sudo apt-get install samba    

I think that's it if not it should give you the correct package in the error message, I"d double check for you but i"m stuck at work on my vista partition.

---

### Post by phillip181 on 2008-12-08
I have samba installed but not NFS. Should I try reinstalling it?

---

### Post by phillip181 on 2008-12-08
PS 

I can also ping them if that helps.

---

