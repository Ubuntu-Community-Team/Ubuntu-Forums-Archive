---
title: "smb share &amp; 3g modem...?"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by windoze87 on 2009-12-28
I've googled the bejesus out of this and cant find any type of answer, anywhere. Here's my situation- I'm running UNR 9.10 on my emachines em250 netbook. I have a tower running Windows 7. On an external hdd connected to the tower, i've got music and movies i share over the wireless network. Installed samba, works fine, i can access and play my music/movies fine. However, if i have the wifi on and Im connected to the internet using my tethered phone on the netbook, my internet does not work. It does nothing indefinitely till i shut off the wifi, then it proceeds as before. What gives? its like Ubuntu is expecting my internet to come through wifi (which isnt the case) and as soon as it's connected to a wifi connection, it drops everything else. Any help would be awesome.

---

### Post by windoze87 on 2010-01-11
bumpity bump bump:popcorn:

---

### Post by pdc on 2010-01-11
this issue has been described before on this forum, and I don't think the answer has emerged;

if you have a workaround, you may need to keep working around things

good luck;

there are specialist linux network forums: what about joining those? You probably need to look like are a member of ZZTop to really be part of those forums .............

---

### Post by changingstate on 2010-01-11
Have you tried looking at your routing table with :  

```
sudo route -n
```

while the wifi is on and while it is off?

---

