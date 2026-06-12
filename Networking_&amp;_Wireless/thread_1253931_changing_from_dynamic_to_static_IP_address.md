---
title: "changing from dynamic to static IP address"
date: 2009-08-30
forum: Networking &amp; Wireless
---

### Post by chippanfat on 2009-08-30
I'm looking to change the ip address on my laptop and server from dynamic to static. Mainly so i can access my server from the Internet. And for other reasons on my laptop.

I've tried so many different methods on both the server and desktop editions and nothing has worked.
I just want a general walk through on how to make them static. I've researched alot on google and tried loads of diffrent methods and nothing has worked and i've asked around on the IRC and we've had no luck.

before i forget. I'm running Ubuntu 9.04 Desktop Edition on my laptop and Ubuntu 9.04 Server Edition on my server. And I'm using Gadmin ProFTP on the server

Cheers.

---

### Post by Iowan on 2009-08-30
You *should* be able to configure the server via */etc/network/interfaces*, the laptop via Network Manager or */etc/network/interfaces*. to access from internet, you'll need to configure port-forwarding on the router, and have either a static address from your ISP, or use a service like no-ip, or dyndns.

---

### Post by chippanfat on 2009-08-30
I've set up all the port forwarding on my router/ I'm using a netgear router so I simply need to click on the forwarding section and choose SSH, FTP & SFTP
 and I've used the dyndns service for the external static route. Its just the internal IP address I need to configure now.

using the method you suggested to access the network settings would I just enter:
 ```
/etc/network/interfaces
```Into the terminal and just change the settings that way?

**You'll have to excuse me, I can use ubuntu fine, its just i'm still a novice when moving into more advanced things like this**

---

### Post by bear24rw on 2009-08-30
[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

---

### Post by chippanfat on 2009-08-30
That link looks like a really easy tutorial. 
Thanks for your help :P

---

### Post by XZero450 on 2009-09-01
I, myself, have followed that tutorial to assign a static ip to eth0. The same adapter that would then have this static ip in Windows XP.

My problem arises after restarting the computer.

Symptoms:
eth0 isn't managed in the connection manager. It tells me so.
VirtualBox can not do anything connection intensive without timing out.
Any applications that rely on this adapter fail to be able to use and rely on the other, thus losing the ports designated for them.
ifconfig displays all the information set for eth0 as being assigned to eth0.


Solution thus far:
Undo everything to get it managed again.
Redo everything to get it static.

What can be done to eliminate the process of my current solution?

---

### Post by Iowan on 2009-09-02
XZero450:
If you need a static address, Network Manager can be used. */etc/network/interfaces* can also be used - if NM won't play nice, but try NM first. The "unmanaged" message is because NM won't (generally) touch interfaces defined in */etc/network/interfaces*.

---

