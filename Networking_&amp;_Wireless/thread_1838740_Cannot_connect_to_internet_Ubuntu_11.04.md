---
title: "Cannot connect to internet Ubuntu 11.04"
date: 2011-09-04
forum: Networking &amp; Wireless
---

### Post by stephenconnolly on 2011-09-04
Hello,

I'm trying to connect to the internet on ubuntu 11.04. I have the ethernet cable plugged directly into the modem. 

I've added a wired connection and updated the IPv4 settings changing the method to 'manual'. I've added the ip address, netmask and gateway. I've checked the settings of my modem and got he DNS Server details. 

But I'm not sure what the Search Domain should be. Can anyone point me in the right direction ?

Any help appreciated.

Regards,
Stephen

---

### Post by piedog98 on 2011-09-04
try plugging the cable into your router? i just had ubuntu and i had the same problem.

---

### Post by stephenconnolly on 2011-09-04
Not sure what you mean, I have the cable plugged directly into the router/modem.

cat /etc/network/interfaces has the following settings:

# The loopback network interfaces

auto lo
iface lo inet loopback

# The primary network interfaces
auto eth0
iface eth0 inet static
       address 192.168.1.115
       netmask 255.255.255.0
       gateway 192.168.1.1

Can anyone tell me if these are the correct settings.

---

### Post by stephenconnolly on 2011-09-04
Ok, I think I have a solutions. The following thread has a similar problem and solution:

[http://ubuntuforums.org/showthread.php?t=1838773](http://ubuntuforums.org/showthread.php?t=1838773)

I'm trying to edit the file NetworkManager.conf as per the thread above, but I do not have permission. I can't change the permissions as I'm not the owner. 

So, can someone tell me how to log on as 'root' so I can edit this file.

---

### Post by blitzit on 2011-09-04
Does this work for you? : Type this at the terminal.

```
sudo gedit /etc/dbus-1/system.d/NetworkManager.conf
```

* I don't know if it is the same folder for 11.04 as well. This works for 10.04.

---

### Post by stephenconnolly on 2011-09-04
Vijay, thanks very much for that. I'm back online.

---

