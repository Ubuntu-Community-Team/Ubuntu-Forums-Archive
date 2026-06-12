---
title: "Problem with samba share"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by eNc707 on 2010-03-14
Hi,

I set up a samba share for my ubuntu. But Samba works only after I enabled sharing options for a random folder (that has nothing to do with the folder i wanna share manually) via GUI. Then ubuntu installs some packages (almost the same I installed before manually) and after that it works.

But thing is, I want to have a samba shared folder on my minmal ubuntu installation without any GUI stuff and so on because it is used as a minimal web server. So I don't have the ability enabling folder sharing the way I can do under a standard ubuntu distribution.

I think I have to configure additional stuff after I installed my samba4 package. For my Samba shared folder I followed the steps in this tutorial:
[http://ubuntuforums.org/showthread.php?t=652640](http://ubuntuforums.org/showthread.php?t=652640)
(This only works after i enabled folder sharing via GUI.)

Thanks for help,

Frank

---

### Post by johnson.d on 2010-03-15
You can probably try setting up samba using the following command:

$ sudo apt-get install samba

After samba installation edit the /etc/samba/smb.conf file and append the following lines: 

[<share-name>]
path = /<share-path>
browseable = yes
read only = no


Now restart the samba server using the following command:

$ sudo /etc/init.d/samba restart

Now you can share the files among other machines.

---

### Post by eNc707 on 2010-03-15
Thank you, it was the missing browsable field! :)

But thing is, I'm using ubuntu via VMWare Player under Windows 7 and I can't see my ubuntu in my Network places. I have to access via IP-ADDRESS/folder... with a full ubuntu distribution I can browse my samba shares the "normal" way via windows explorer network places...

What do I have to do?

Thx. :)

---

### Post by johnson.d on 2010-03-16
As the VM-ware player uses NAT by default, you can try changing the network setting to Bridged mode at VM-ware player window by clicking VM-> Removable devices-> Network adapter-> Bridged. This would enable broadcast and hence the Ubuntu machine may be browsed from the Windows machine.

---

