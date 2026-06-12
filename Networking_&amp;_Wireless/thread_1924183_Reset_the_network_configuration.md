---
title: "Reset the network configuration?"
date: 2012-02-12
forum: Networking &amp; Wireless
---

### Post by Magma828 on 2012-02-12
I have an embedded computer running ubuntu server which relies on ethernet for management using SSH etc. I've accidentally messed up the network configuration by trying to give it a static IP (was just auto DHCP before).

I modified the file /etc/network/interfaces and replaced the following line:
iface eth0 inet dhcp

with this:
iface eth0 inet static
    address 10.42.43.10
    netmask 255.255.255.0
    network 10.42.43.1
    broadcast 10.42.43.1
    gateway 10.42.43.1

I still have access to the keyboard and can use CTRL+ALT+F3/etc to blindly login and perform commands! Can anyone suggest a command to revert these changes?

---

### Post by praseodym on 2012-02-12
Use the terminal text editor "nano":

```
sudo nano /etc/network/interfaces
```
Move with the arrow keys, manipulate, and save&exit with CTRL+X. After that restart the network with:

```
sudo /etc/init.d/networking restart
```

---

### Post by Iowan on 2012-02-12
Ordinarily, the network would be 10.42.43.0. and the broadcast address would be 10.42.43.255. 
"blindly login and perform commands" sounds like the screen isn't working?
If SSH is working, SCP might let you copy a modified file back onto the server.

---

### Post by Magma828 on 2012-02-13
Managed to get it working by doing cp to make a backup and nano to type in a new file :)

And yeah, the device has no screen because I was relying on SSH always working...

---

