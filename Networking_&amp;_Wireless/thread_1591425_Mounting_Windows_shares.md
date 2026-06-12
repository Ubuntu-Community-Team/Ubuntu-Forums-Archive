---
title: "Mounting Windows shares"
date: 2010-10-09
forum: Networking &amp; Wireless
---

### Post by theanalyst on 2010-10-09
My computer is connected to the college lan where almost all machines are some variant of Windows OS. If i use Places > Network, while windows network is displayed, mostly it returns unable to mount shares, my workaround for this problem is I use some tool like nbtscan to see which hosts are up and then use network > Connect to Server > windows share and type in the ip address, this mounts the windows share even though Places> network doesn't display such hosts. 
My question is there some command line way where I can invoke nautilus to mount the windows share, ie the same job connect to server > windows share does? And is there some application like say lan surfer for windows which lists all the folders shared by a windows client. This problem has been keeping most people from installing some linux variant in college for some time now, any solution would be of help

---

### Post by d1brian on 2010-10-09
try [this]("http://ubuntuforums.org/showthread.php?t=280473")

---

### Post by theanalyst on 2010-10-12
Well 
```
smbclient -L 192.168.1.2 -U%
```doesn't seem to work for me, this is what i got after smbclient -L <ipaddr> -U%
```
Error returning browse list: NT_STATUS_ACCESS_DENIED
session request to 192.168.x.xfailed (Called name not present)
session request to 192 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available


```So is there a workaround for this??

Also if I use connect to server windows share of the same ip i am able to view the contents.

---

### Post by d1brian on 2010-10-12
> **theanalyst said:**
> Well 
```
smbclient -L 192.168.1.2 -U%
```doesn't seem to work for me, this is what i got after smbclient -L <ipaddr> -U%
```
Error returning browse list: NT_STATUS_ACCESS_DENIED
session request to 192.168.x.xfailed (Called name not present)
session request to 192 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available


```So is there a workaround for this??

Also if I use connect to server windows share of the same ip i am able to view the contents.

I was able to view the shares from a Windows machine using the following syntax:
```

smbclient -L <ipaddr>

```

---

