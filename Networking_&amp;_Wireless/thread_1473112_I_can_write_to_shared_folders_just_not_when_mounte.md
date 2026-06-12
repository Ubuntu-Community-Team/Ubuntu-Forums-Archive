---
title: "I can write to shared folders just not when mounted."
date: 2010-05-04
forum: Networking &amp; Wireless
---

### Post by ht3k on 2010-05-04
Ok here's my situation. 

In Ubuntu, when I go to Network > Windows Network > Workgroup > WindowsPC > SharedFolder. I can copy/write/read to it and everything normal. 

When I do the following steps to mount it : 
```
sudo mkdir /media/filehost
```

```
sudo mount -t cifs -o username=server,password=secret //192.168.0.43/SharedFolder/ /media/filehost
```


Everything works, I get the icon in my desktop and I can see all the files in the folder. Hell I can even open the files just fine, the one thing I can NOT do is write! Which was the purpose of the mount in the first place.

All I want is a damn short cut to that folder on my desktop and to be able to write to it. I don't get why I can write to it when I browse to it normally just not when I mount it? Any help is appreciated, thanks guys!

---

### Post by pastalavista on 2010-05-04
> **ht3k said:**
> Ok here's my situation. 

In Ubuntu, when I go to Network > Windows Network > Workgroup > WindowsPC > SharedFolder. I can copy/write/read to it and everything normal. 

When I do the following steps to mount it : 
```
sudo mkdir /media/filehost
```

```
sudo mount -t cifs -o username=server,password=secret //192.168.0.43/SharedFolder/ /media/filehost
```


Everything works, I get the icon in my desktop and I can see all the files in the folder. Hell I can even open the files just fine, the one thing I can NOT do is write! Which was the purpose of the mount in the first place.

All I want is a damn short cut to that folder on my desktop and to be able to write to it. I don't get why I can write to it when I browse to it normally just not when I mount it? Any help is appreciated, thanks guys!try it like this

```
sudo mount -t cifs -o --rw username=server,password=secret //192.168.0.43/SharedFolder/ /media/filehost
```

---

### Post by ht3k on 2010-05-05
--rw seems to be on by default according to 

```
man 8 mount
```

I however, found out that adding uid=1000 (userid) made it work!

```
sudo mount -t cifs -o username=server,password=secret,uid=1000 //192.168.0.43/SharedFolder/ /media/filehost
```

Thanks for your help, I hope this can help someone in the future!

---

