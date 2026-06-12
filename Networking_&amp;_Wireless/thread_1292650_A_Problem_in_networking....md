---
title: "A Problem in networking..."
date: 2009-10-16
forum: Networking &amp; Wireless
---

### Post by aprashanth on 2009-10-16
I am trying to logging into a system(let me say sys-B from sys-A ).. to which I have access.. 

but once when the user has logged out of sys-B(the system is hardly used.. hence the comp Automatically logs out..)... 
I am not able to access the system..

what could be the reason for this and how am I able to stop this...

please help...

---

### Post by jonobr on 2009-10-16
A bit more info would b useful

How are you logging into the remote system.
What connection type are you using.

---

### Post by Iowan on 2009-10-16
Is the network on that machine configured via Network Manager? NM doesn't seem to activate network until login - it may disable network on logout. You might try setting the machine up via */etc/network/interfaces* file.

---

### Post by aprashanth on 2009-10-17
Thank for your reply... but what I am to set in that files..
it would be nice if you are more specific....

---

### Post by aprashanth on 2009-10-17
Dear jonobr:

I have logged into the system physicall not as a remote user...
but once the system gets logged out.. I repeat logged out not shut down.. 
still I must be ablt to connect to it.. but that is not happening..

Its a LAN connection.. I am trying the command ssh ranu@10.32.98.45

---

### Post by Iowan on 2009-10-17
How does machine get it's IP address - DHCP or static?
A DHCP connection might look like:```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
```
 A static configuration might look something like:```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static 
      address 192.168.1.180     
      netmask 255.255.255.0
      network 192.168.1.0        
      broadcast 192.168.1.255
      gateway 192.168.1.1
```

---

### Post by aprashanth on 2009-10-19
> **Iowan said:**
> How does machine get it's IP address - DHCP or static?
A DHCP connection might look like:```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
```
 A static configuration might look something like:```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static 
      address 192.168.1.180     
      netmask 255.255.255.0
      network 192.168.1.0        
      broadcast 192.168.1.255
      gateway 192.168.1.1
```
its a static.. connection..

---

