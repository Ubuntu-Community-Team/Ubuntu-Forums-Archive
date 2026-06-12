---
title: "Route add default gw question"
date: 2009-02-27
forum: Networking &amp; Wireless
---

### Post by all metro on 2009-02-27
Hello all,
I got a question I can't seem to find anywhere on these forums or else where. I have a static ip here at my work. For some reason the default gateway needs to be manually installed every time I boot up. I.E. sudo route add default gw 10.0.0.254.

Is there a way to automaticly have that put in at start up? Did I set my network up wrong? 

Thanks Tim

---

### Post by albinootje on 2009-02-27
> **all metro said:**
> For some reason the default gateway needs to be manually installed every time I boot up. I.E. sudo route add default gw 10.0.0.254.

You probably have something wrong in the NetworkManager settings.
Here's an example of /etc/network/interfaces in case you want to try with that.
```

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
	address 192.168.1.2
	netmask 255.255.255.0
	broadcast 192.168.1.255
	gateway	192.168.1.1

```

---

### Post by all metro on 2009-02-27
Here is what mine looks like now. Still does not work. I entered the default gw and then it worked. It shows the gateway there. Kind-of lost on where to go. ](*,)

auto lo
iface lo inet loopback


 

auto eth1
iface eth1 inet static
	address 10.0.0.102
	netmask 255.255.255.0
	gateway 10.0.0.254

Thanks Tim

---

### Post by albinootje on 2009-02-27
> **all metro said:**
> 
auto eth1
iface eth1 inet static
	address 10.0.0.102
	netmask 255.255.255.0
	gateway 10.0.0.254


I don't know how Network Manager works with a customized /etc/network/interfaces

If you want you can remove Network Manager completely, and then try : sudo ifconfig eth1 up, or /etc/init.d/networking restart

And are you using eth1 or eth0 ? eth1 was just an example from my local fileserver.

---

### Post by superprash2003 on 2009-02-27
before you type the command to add the gateway.. got to the terminal and type **ifconfig **and post output.. also post output of **route -n**

---

