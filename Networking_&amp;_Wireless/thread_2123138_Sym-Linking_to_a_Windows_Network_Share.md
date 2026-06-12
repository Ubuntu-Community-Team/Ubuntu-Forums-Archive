---
title: "Sym-Linking to a Windows Network Share"
date: 2013-03-07
forum: Networking &amp; Wireless
---

### Post by JamesR100 on 2013-03-07
We have a Windows Network and each user has two user areas, 'Safe User Area' and 'Temporary User'.

With many users starting to bring in and wanting support for mobile devices and with us planning a BYOD implementation, we are looking to prepare for this, so we have setup Owncloud an OpenSource self run cloud. On OwnCloud we have synced it with Active Directory to import all users. 

Now for the tricky part:

I want to map the data folders stored on the OwnCloud server to the Windows Network Share for each user. I tried making a sym link;
 
[B]" ln -s [windows share path for user] [owncloud path for user]"
 
[COLOR=#ff0000]e.g ln -s //server1/users/staff/jsmith /var/www/owncloud/data/jsmith

[/COLOR][/B]When I attempt this it says system link broken. I am not even sure if what I am attempting is even possible. So could anyone help me achieve this or point me to something else that could achieve this.[COLOR=#ff0000]
[/COLOR]
Thanks,

James

---

### Post by Lisiano on 2013-03-07
First, you reversed ln, you need to first type What to link then Where to put it, appended with What to name it ```
ln -s /var/www/owncloud/data/jsmith  //server1/users/staff/jsmith/data
``` but I'd doubt that would work in this use case. I think it would make more sense if you stored the OwnCloud server on the same server as your AD server. This way (If it's a Linux AD) you could simply link this way ```
ln -s /var/www/owncloud/data/jsmith  /home/jsmith/data
```

---

