---
title: "Can't get permissions in samba share"
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by dave_wilford on 2010-06-06
Hi guys & girls,

When I create a new folder on my ubuntu machine and share it with my windows 7 machine using 'net usershare add <dir> <path>', I can't get write perms in Win 7. It keeps giving me a "You need permission to perform this action'. I've chmod the folder to 777 but still no luck. 

The funny thing is, it was all working fine until I tried to add a new usershare yesterday (Can't think what I've changed). I use this sharing method to share all of my development /var/www/ folders so I can work on them from my win machine.

I have had a few problems with my samba smb.conf, and it nuked and rebuilt yesterday.
I'm fairly new to the Linux game, and this permissions problem has me baffled.

Thanks in advance,

Dave

---

### Post by dave_wilford on 2010-06-06
Ok I got it solved.

Incase anyone ever has same issues, It was a smb.conf issue, I am now using this minimum config which is working well.

> 
null passwords = true
browsable = yes
follow symlinks = yes
wide links = yes
unix extensions = no

[home]
  path = /home
  read only = no
[root]
  path = /
  read only = no



---

