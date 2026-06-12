---
title: "howto fix network manager?"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by berale on 2009-11-30
While playing around with Ubuntu 9.10 I stupidly purged net-tools and network-manager.
```


 Now I don't have a network connection so I cant just apt-get install them.
I tried to reinstall both packages from the liveCD but no luck:
[code]
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install net-tools network-manager

```
but it can't locate network-manager
 
I then downloaded the packages (only the above two, no dependencies) from the Ubuntu repositories and tried to reinstall them, still no luck. Both packages are installed but something is missing because when I do:
```

ifconfig

```
or:
```

sudo /etc/init.d/networking start|restart|stop

```
I get nothing, no error or anything.
Right now I'm working with a liveCD and everything is working. Can anyone help me get my system networking?
Thanks...

---

### Post by Iowan on 2009-11-30
Again, I'm guessing on 9.10...
Check if NM is in the startup program list (where/how??)
[Here]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1301543") is some (old) information  from the Development forum.

---

