---
title: "Mount encoding"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by timmson on 2008-12-18
Hello
I have some problem with mount. 
when i try to open share on my windows xp from my router, everythink is ok
when i try to mount share on my intrepid from my router, russian encoding is wrong.

smb.conf from router
```

[global]
	interfaces = br0
	bind interfaces only = yes
	workgroup = POWERGROUP!
	server string = WL500gp
	guest account = nobody
	security = share
	browseable = yes
	guest ok = yes
	guest only = yes
	log level = 1
	max log size = 100
	encrypt passwords = no
	preserve case = yes
	short preserve case = yes
	client code page = 866
	character set = 1251

[share]
	path = /tmp/harddisk
	writable = yes
	force user = admin

``` 

what option will i use to mount?

---

