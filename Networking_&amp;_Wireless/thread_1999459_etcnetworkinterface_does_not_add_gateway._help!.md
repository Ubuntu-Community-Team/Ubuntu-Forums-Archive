---
title: "/etc/network/interface does not add gateway. help!"
date: 2012-06-08
forum: Networking &amp; Wireless
---

### Post by chicago31415 on 2012-06-08
I set up a machine with a static IP and I can only access the internet if I issue the following command at the terminal 

```
sudo route add default gw xxx.xxx.xx.x 
```

where xxx.xxx.xx.x is my gateway

I entered the same line in my /etc/network/interface with a preceding "up" and "post-up" but route -n does not show this gateway. I have to issue this command every time I boot my machine.

Sorry I am new to networking so please forgive me if I did something stupid.

---

### Post by sanderj on 2012-06-08
Looks the same as my question ([http://ubuntuforums.org/showthread.php?t=1997443](http://ubuntuforums.org/showthread.php?t=1997443)), so I'll follow this thread.

---

