---
title: "Ubuntu 64-bit Realtek Networking"
date: 2010-08-01
forum: Networking &amp; Wireless
---

### Post by johnnybgood115 on 2010-08-01
Hey guys/girls! 

I'm having an issue getting online with a new PC i just put together.  I'm using the motherboard's network adapter which is a Realtek RTL8168D and RTL8169.  I was able to get a network connection before a series of updates to Ubuntu 10.04, until recently when I am no longer able to connect to the internet. 

I tried the following diagnostic commands: 

```
su -c "lspci | grep -i ether"
```
RETURNED ....
```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
07:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
```


```
/sbin/lsmod | grep r8169
```
RETURNED....
```
r8169                  39554  0 
mii                     5237  1 r8169
```

```
dmesg | grep eth0
```
RETURNED...
```
[    2.764931] eth0: RTL8168d/8111d at 0xffffc9000066e000, 00:26:18:9b:8b:3f, XID 083000c0 IRQ 35
```

Any help or leads will be greatly appreciated!

Thanks!
John

---

### Post by dillzz on 2010-08-02
johnnybgood115,

I have a GIGABYTE GA-EX38-DS4 775 X38 Realtek (r8169), running 10.04 x86_64 as well.  I am having similar problems.  I have static IP's set (doesn't matter if its DHCP) and the only way I can get networking to work is to stop/start networking. . . After that it works fine.  I just put in /etc/rc.local 
/etc/init.d/networking stop && /etc/init.d/networking start

Curious to see if you get this same behavior. . .There are many posts about this with little to no resolution. 

-Dillzz

---

### Post by johnnybgood115 on 2010-08-06
I finally got around to trying that.  Unfortunately, it doesn't seemed to have worked. 

I stop the networking with no problems but then when I go to start up networking again I get: 

```
networking stop/waiting
```

Not really sure what it's trying to tell me but I can't get online.

- John

---

### Post by unclecharlie on 2010-08-22
Lots of discussion on this chipset here:

[http://ubuntuforums.org/showthread.php?t=1436667](http://ubuntuforums.org/showthread.php?t=1436667)

Don't worry, it didn't actually destroy the guy's network card.

In my case I have to unplug and replug in the router to connect after logging on and I lose connection if I don't do anything over the network for five minutes or so.  I'm using the ASUS P7P55 board which has the Realtek 8168B chip.  Windows 7 networking has no problems at all.

ch

---

### Post by johnnybgood115 on 2010-08-22
I've got the same exact motherboard, the Asus P7P55D.  My Windows 7 install works with no issues (in regards to networking).  When I'm in Ubuntu 10.04, unplugging and then plugging the cable back in do nothing.  I don't even see networking running.  I'm going to consider buying a PCI network card and not use the onboard one.

---

