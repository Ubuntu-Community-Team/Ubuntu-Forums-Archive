---
title: "Auto Mount Samba Share"
date: 2012-01-06
forum: Networking &amp; Wireless
---

### Post by cleric28 on 2012-01-06
Hi everyone, I am new here and this is my first post here at ubuntuforums.org. I am not sure if this is the right place to post this question, so admin feel free to move this post if this is not the correct section.

I just want to ask how to auto mount my centos samba share to my ubuntu 10.10, so whenever I login to my account, the share is there at my desired mount point. My smb.conf set up as like this

[global]
security = share
guest account = guest
[share]
writeable = yes
guest ok = yes
browseable = yes

So anyone can access "share" w/o needing to input username and password. If I try to browse this share on my ubuntu, I can access it w/o problems. But when I try to add it to my /etc/fstab file as:
//192.168.0.5/share /opt/share cifs default 0 0
It is not working. I tried to browse the web for answers but all tutorials is like this:
//192.168.0.5/share /opt/share cifs -o username=username,password=pass 0 0
But this is not working on my case since my share doesn't need to input username and password to access. Please help me with this, I am new to linux and trying to learn more about it. Thanks. Oh, by the way, sorry for my bad grammar.

TIA. :)

---

### Post by jsra on 2012-01-06
Hello,

try blank username and password
```
//192.168.0.5/share /opt/share cifs -o username=,password= 0 0
```

jsra

---

### Post by collisionystm on 2012-01-06
did you set your permissions on /opt/share

---

### Post by cleric28 on 2012-01-07
> **jsra said:**
> Hello,

try blank username and password
```
//192.168.0.5/share /opt/share cifs -o username=,password= 0 0
```jsra

Hi jsra,

Thanks for replying, I tried what you said, but it is still not working after rebooting my computer the share files doesn't show in /opt/share folder. I think the syntax is wrong or something, because it's putting a red background on fstab. See screenshot. Thanks.

[IMG]http://i22.photobucket.com/albums/b306/cleric228/screenshot-1.png[/IMG]

@collisionystm,

Yes, I set the permission to 777 for /opt/share folder. Thanks for replying.

UPDATE:
Managed to make it working! :D. 
Correct syntax is like this:
//192.168.0.5/share /opt/share cifs username=guest,password= 0 0

Thanks for all your help. Till next time.

---

