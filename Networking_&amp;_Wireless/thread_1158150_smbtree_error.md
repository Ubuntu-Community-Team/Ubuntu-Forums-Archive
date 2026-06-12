---
title: "smbtree error"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by mardangga on 2009-05-13
Hello everyone...
I got a problem when I try to create a workgroup. I try to make 2 workgroup with 2 computer for each workgroup. So, there's totally 4 pc. All pc is connected to same hub. I'm using 2 ubuntu 8.04 server and 2 windows xp. When I set all pc to the same workgroup & same network id, there no problem. The problem happen when I try make 2 workgroup with different network id. One of the workgroup is working fine, but the other one give an error message when I use "smbtree -N". I got an error message: 

failed tcon_X with NT_STATUS_NO_SUCH_USER 
failed tcon_X with NT_STATUS_NO_SUCH_USER 

I don't know what's thats mean? But after I turn off all pc, and turn it all on again. The problem is gone. Can anyone told me what is the problem?

Oh, BTW, I'm using the default smb.conf. And I just change a few option likes: 
workgroup = GAMANK
server string = Latihan
netbios name = Ubuntu01
security = share

And makes share folder like this:
[coba]
   comment = Coba2 Sharing
   path = /home/agus/coba
   browseable = yes
   guest ok = yes
   writeable = yes

The other option is same as default. So, could anyone told me, where's my mistake?

Thx for u'r attention, and sorry for my poor English.

---

