---
title: "pppoeconf breaks regular dhcp?"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by cesera on 2009-09-10
My router died recently, which meant that for a day or two I had to access my ADSL directly, so I ran pppoeconf (with all the defaults), told it not to start automatically and off I went.
 
However when I got around to buying a new router I presumed everything would just work again (as I had told pppoe not to start automatically), but now everytime I reboot I have to do:
```
sudo dhclient3 eth0
```to get my network up an running.
 
Anyone know why this is happened? And more importantly anyone know how to fix it? I don't mind doing the dhclient thing every so often, but my wife is not very happy with that.

---

### Post by shredder12 on 2009-09-10
Actually I think its the network manager which runs the same command for you automatically when you login.. 
but since you configured ADSL modem directly from terminal so the changes you made in the /etc/network/interfaces file are not known to Network manager..

since ADSL settings are for eth0 interface and i guess your dhclient runs on eth0 too.. and network manager doesn't want to interfere with your settings on eth0 interface. so it doesn't connect automatically..

If i am right then on clicking the network manager you will see that the wired connection is not managed.

If that is the problem then you jst need to comment out some lines in your /etc/network/interface file..
please post the contents of that file...
so that we may if there is something else wrong..

---

### Post by cesera on 2009-10-11
OK, four weeks and 7500km driving later I finally get around to picking up this issue again (sorry about the long delay).
 
Here is a copy of my /etc/network/interfaces file:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
 
# The loopback network interface
auto lo
iface lo inet loopback
 
# The primary network interface
auto eth0
#iface eth0 inet dhcp
 
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider
iface eth0 inet manual
```
Just for future reference, is there a non-commandline way of configuring the ADSL modem?
 
 
Thanks

---

### Post by shredder12 on 2009-10-11
A quick fix to the problem...
comment out all the lines of the /etc/network/interfaces file.. except the "lo" one..
so now you /etc/network/interfacs file should have only these 2 lines..
```
auto lo
iface lo inet loopback

```

restart the network or ur system and ur network manager should be showing any error..

You an configure ADSL connections using your network manager. right click on the icon and select edit connections...
you will see a tab named ADSL...you can use it to configure ADSL connections..

---

