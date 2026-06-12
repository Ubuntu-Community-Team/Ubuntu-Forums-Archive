---
title: "Using cifs to mount network share"
date: 2011-10-17
forum: Networking &amp; Wireless
---

### Post by johnb4b on 2011-10-17
Hi everyone

I'm trying to mount a network share on the local network. I have this entry in my /etc/fstab: 

# Mount the public network drive
//192.168.1.5/Public /media/public cifs username=myusername,password=mypassword,_netdev,uid=john 0 0

(My ubuntu username is john). After I mount the share using ```
sudo mount -a
```

then the drive is mounted on /media/public/ but the root of the share is owned by "root". I can read files from the root directory of the share, and even delete files from there, but I cannot write to that directory. If I then navigate to any subfolder of the share, then I have all permissions. I can read, write, delete files etc. 

How can I make it so that I have all permissions in the root directory too? 

Thanks in advance.

---

### Post by johnb4b on 2011-10-17
I found the solution. I have to include the "rw" option: 

```
# Mount the public network drive
//192.168.1.5/Public /media/public cifs username=myusername,password=mypassword,_netdev,uid=john,**rw** 0 0
```

---

