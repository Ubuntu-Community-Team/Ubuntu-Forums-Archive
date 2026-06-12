---
title: "Windows 7 Cannot Access Second HD shared through Samba"
date: 2012-02-12
forum: Networking &amp; Wireless
---

### Post by Bascotie on 2012-02-12
hi guys,

I've asked around irc, tried a couple similar forum posts, etc, but I cannot get this second drive to work. This is a fresh install of Ubuntu 11.10.

1- I used a Samba guide to share a folder within /srv and it works great.
2- I have a 2nd hard drive that I labeled and tried sharing and Windows 7 will see the share but when I try to open it, it says it cannot be accessed. 


Here is my smb.conf, as well as the fstab (which I don't know much about but someone said I needed to do something with it)
[B]
fstab: [/B][http://pastebin.com/Nbd9J44c](http://pastebin.com/Nbd9J44c)
**smb.conf: **[https://gist.github.com/1813523](https://gist.github.com/1813523)

---

### Post by Bascotie on 2012-02-12
Not sure what I was doing wrong but it ended up working this way:

I removed [extradrive] share from the smb.conf file and just right clicked the files folder within the 2nd hard drive -> went to properties -> sharing and setup the share there. 

For any noobs doing this, like me, remember to hit "create share" when you are done and make sure the permissions are set for full read and write (if youre ok with anyone changing the files)

---

### Post by Bascotie on 2012-02-13
lump o' bump

---

