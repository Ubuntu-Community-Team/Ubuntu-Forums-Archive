---
title: "Wireless NIC"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by Silver-revo on 2006-06-03
This has to be the busiest forum on the entire board....

Anyway I have a Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02). I have tried everything and then some to get this working, I am assuming someone on this board has got this particular NIC working.

Just so that you have a little background, I recently did a fresh install of dapper drake, I think that is the new ubuntu distribution, and did everything according to this post here: [WIFI POST]("http://ubuntuforums.org/showthread.php?t=185174&highlight=wifi")

That got my little blue light on my laptop to fire up so I am assuming that is because of the firmware addition. 

The problem is that I cannot connect to ANY wifi connection even manually entering IP information little-lone DHCP. Funny thing is when I go into network tools and look at the info for eth1 which is my wireless nic, it doesn't have the mac address or anything listed.](*,) :-k .........

Anyone???????

---

### Post by darkshadow on 2006-06-03
Sound like the same problem I had here is the fix I used
[http://ubuntuforums.org/showthread.php?t=187498](http://ubuntuforums.org/showthread.php?t=187498)

---

### Post by Silver-revo on 2006-06-03
Is there anyone? 




........
The pleading of a desperate man whom is parched from wifi defecency

---

### Post by Braino on 2006-06-04
I was unable to get my BCM4318 to work the fwcutter. It detected my card, and I was able to connect to the essid of my router, but I couldn't get any further than that. 

These are the steps I took:

Blacklist bcm43xx, and un-blacklist ndiswrapper (if it is). This can be done by adding 'blacklist bcm43xx' to
```

 sudo gedit /etc/modprobe.d/blacklist

```

A working driver can be found from Acer [here]("ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip").

Then, unzip that, get rid of the bad driver and hook up the good driver to ndiswrapper
```

sudo ndiswrapper -e bcmwl5

```
```

sudo ndiswrapper -i Desktop/bcmwl5.inf

```
Check it:
```

sudo ndiswrapper -l

```
Then, if you need to put the ndiswrapper module back:
```

sudo modprobe ndiswrapper

```
Make sure the bcm43xx module is gone:
```

sudo rmmod bcm43xx

```


Then, restart everything:
```

sudo /etc/init.d/networking restart

```


If this does not correct the problem, it could have something to do with how  your /etc/network/interfaces is setup

Here is mine:

```

# The loopback network interface
auto lo
iface lo inet loopback

iface eth1 inet dhcp
wireless-essid YOURESSIDHERE
wireless-key open
iface eth0 inet dhcp
auto eth1
auto eth0

```

Replace eth1 with whatever yours is.

Hope this helps :)

---

