---
title: "Can stop networking, but not restart it"
date: 2013-02-10
forum: Networking &amp; Wireless
---

### Post by AussieGuy on 2013-02-10
I have always thought of myself as a reasonably knowledgable linux user, but today's problem: computer only accessing the network when booted with a live CD, has me beat.

I've tried several times to restart networking.  The command

sudo /etc/init.d/networking restart

tells me that I should use "service" or "start".  Well, both of

sudo start networking
sudo service networking start

simply produce

networking stop/waiting

I've also tried

sudo ifup -a
sudo ifup eth0
sudo ifconfig eth0 up

Nothing.  I simply cannot restart the network, without a reboot.  (I've done about 10 reboots so far; I'm now using a liveCD).  I've tried using the KDE system settings, but

System settings -> Network

causes System settings to crash!  Arrrgh!

I'm at my wits end: I can't work without access to the network, and my desktop machine, when booted up normally, just will not connect.  (I've tried unplugging and replugging the network cable too.)

Any advice short of smashing the maching with an axe would be most gratefully received!

thanks,
Al

---

### Post by steeldriver on 2013-02-10
Is this Desktop or Server? Unless you have configured things manually via /etc/network/interfaces, the current Desktop editions don't use the networking service - they use network-manager (configured via the desktop applet) instead:

```
$ service networking status
networking stop/waiting
$ service network-manager status
network-manager start/running, process 3723
$
```

---

### Post by AussieGuy on 2013-02-10
Oh yes - that makes sense!  I'll try that now.

I'll see if a mix of cable unplugging and replugging, along with network-manager restarting, will fix my problem.

---

### Post by AussieGuy on 2013-02-10
I can now stop and start the network at will. However, my desktop still cannot connect. What a colossal waste of a day. I'll bring my laptop in tomorrow, so at least l can get some work done. 

Maybe I'll have to reinstall Ubuntu? Seems like there should be an easier solution....

---

### Post by SlugSlug on 2013-02-11
am not a fan of network manager and normally remove it upon fresh install
I then edit my interfaces file like so..

```
 cat /etc/network/interfaces
``` 
```
 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1

```or DHCP
```
 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


```

---

