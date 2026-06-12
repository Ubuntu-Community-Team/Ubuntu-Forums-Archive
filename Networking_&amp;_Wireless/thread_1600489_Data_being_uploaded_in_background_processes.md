---
title: "Data being uploaded in background processes"
date: 2010-10-19
forum: Networking &amp; Wireless
---

### Post by Creators.guru on 2010-10-19
hi i am using ubuntu 10.4, i have attachedd my desktop screenshot , my problem is that i use no software that uses network but still OS uploads data from my pc, is it something to worry about my network security ? and please tell me if there is any way to check which file is using network and how much it is using. 

[CENTER][url=http://www.freeimagehosting.net/][img]http://www.freeimagehosting.net/uploads/515e748421.png[/img][/CENTER]

---

### Post by mikewhatever on 2010-10-19
The following command will show all active connections, as well as the processes associated with them.

```
sudo netstat -tupn
```

The amount of uploading is shown in the screenshot, about 0.2KBps.

---

