---
title: "Can't access ubuntu share from windows 7 machine"
date: 2010-10-08
forum: Networking &amp; Wireless
---

### Post by rkylemyers on 2010-10-08
Hey all. I am running Ubuntu 9.10 on my desktop right now. I have an external western digital terabyte drive plugged into it. I am able to see it and view it fine. Let's work with my music folder for example. I want to be able to access this music from my Windows 7 laptop so that I may add it to my itunes. However, when I enter the \\server\share from the windows 7 laptop it says that the "server" is found but the "share" seems to be invalid. I've checked this 20 times and setting the share name to "music". I've rebooted 2 times on each computer yet to no avail. If I make a share on the Ubuntu desktop I can access it from the laptop. So it seems like it just gets lost when looking inside the external. This was just working last week, then I had to blow away they win 7 lappy and now it just won't work! It's aggrevating, but I was hoping someone here could help.

---

### Post by josir on 2010-10-11
Try to install samba 3.4 or superior. Early versions do not work with Win 7.

---

### Post by Morbius1 on 2010-10-11
> If I make a share on the Ubuntu desktop I can access it from the laptop.  So it seems like it just gets lost when looking inside the external.This doesn't sound like a Samba problem ( and BTW - Do not install Samba4 ). It sounds like a Linux Permissions problem. The external HDD formatted in NTFS by any chance? It makes a difference only because of how you may be mounting it. If it's a linux permissions problem there is an easy fix.

Anyway, We don't have enough information. Please post the output of the following commands:
```
net usershare info
``````
testparm -s
```

---

