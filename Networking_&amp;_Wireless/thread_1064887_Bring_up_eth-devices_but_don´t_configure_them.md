---
title: "Bring up eth-devices but don´t configure them"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by adieb on 2009-02-09
Hi,

I am running a Server (Ubuntu 8.04 64bit) that runs Virtualbox. It has 3 eth devices in three different networks. 

Now (since there is a new version of virtualbox, where you don´t need bridges and tap/tun and no source routing) i want /etc/network/interfaces just to configure eth0, but bring up eth1 and eth2.

Even if I wrote in etc/network/interfaces

```
auto eth1
iface eth1 inet static

auto eth2
auto eth2 inet static
```


It doesn´t bring them up. So after a restart I have to type

```
ifconfig eth1 up
ifconfig eth2 up
```

Is there a "natural" way to do this? Otherwise i am going to put these two command into /etc/rc.local

---

### Post by adieb on 2009-03-11
bump

---

### Post by kevdog on 2009-03-11
Just a few things

The commands within the /etc/network/interfaces file are only referenced by the command ipup/ifdown

ifconfig up/down are two separate commands.

I've never worked on the server before, however after you boot, and you run the command
sudo /etc/init.d/networking restart

Do the devices come up then?

---

### Post by adieb on 2009-03-11
well, after a restart, they are not listed with "ifconfig". I can bring them up with 
"ifconfig eth1 up"
"ifconfig eth2 up"

I didn´t test, if they´ll be up, after typing "/etc/init.d/networking restart"
But i think they wouldn´t be, since it does nothing else then the boot up process does.

So to get them up (visible in the output of ifconfig) i need to manually type 
"ifconfig eth1 up"
"ifconfig eth2 up"
(or let rc.local do that)

---

### Post by kevdog on 2009-03-11
Do you have a file /etc/init.d/networking?  This is just a shell script file!
1

---

