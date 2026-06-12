---
title: "Broadcom STA driver not working in 10.04 with Dell Xps 1647"
date: 2010-07-12
forum: Networking &amp; Wireless
---

### Post by paras301 on 2010-07-12
Hello,

When I freshly installed my Ubuntu 10.04, broadcom wireless worked after I installed the driver using hardware manager. But somehow it got de-activated, and not its not working. I need help related to that.

Here is some output which might help you to understand the problem.

```


paras@ubuntu:~$ sudo lshw -C network
[sudo] password for paras: 
  *-network DISABLED      
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: f0:7b:cb:7f:a6:c4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:f0500000-f0503fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 10
       serial: 00:26:b9:22:0a:15
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=sb v2.19 ip=192.168.1.18 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:35 memory:f0800000-f080ffff
paras@ubuntu:~$ 
paras@ubuntu:~$ 
paras@ubuntu:~$ lsmod|grep -e b43 -e ssb -e wl
wl                   1964968  0 
lib80211                6151  2 lib80211_crypt_tkip,wl
paras@ubuntu:~$ 
paras@ubuntu:~$ 
paras@ubuntu:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.


```Need help!
Thank you,
Paras

---

### Post by michele.bartolettistella on 2010-07-12
Hello,

currently I having to do with the same problem; I own a Dell Vostro 3700, and I installed Ubuntu 10.04 some days ago...

My Wireless card is a Broadcom, too, and when I try to activate the Broadcom third-part drivers from [COLOR=DarkRed]System>Administration>Hardware Drivers[/COLOR], I receive an error message.

I attached a[COLOR=DarkRed] screenshot[/COLOR] about these issues, hoping someone more expert will help us!

MBS

---

### Post by bkratz on 2010-07-12
> **michele.bartolettistella said:**
> Hello,

currently I having to do with the same problem; I own a Dell Vostro 3700, and I installed Ubuntu 10.04 some days ago...

My Wireless card is a Broadcom, too, and when I try to activate the Broadcom third-part drivers from [COLOR=DarkRed]System>Administration>Hardware Drivers[/COLOR], I receive an error message.

I attached a[COLOR=DarkRed] screenshot[/COLOR] about these issues, hoping someone more expert will help us!

MBS


You do have a wired connection attached when you try this-right?

---

### Post by michele.bartolettistella on 2010-07-12
Well, the situation is as follow:

.I turn on the notebook and start Ubuntu 10.04 2.6.34;
.The wireless card seems to be dead: I can't connect via wireless, the card doesn't either receive the signal of any wireless network in the air;
.I go to System>Administration>Hardware Drivers, and see that the Broadcom STA drivers are not active (see the screenshot attached to this post);
.I try to activate the Broadcom drivers, but I receive the following message:

> Sorry, the installation of this driver failed. Please have a look at the log file for details /var/log/jockey.log

and the drivers keep not active... apparently.

In fact, after doing this, the wireless suddenly goes alive, and I can connect via wireless. But at the next reboot, I will again have to do the same procedure...

Any help?

---

### Post by bkratz on 2010-07-12
> **michele.bartolettistella said:**
> Well, the situation is as follow:

.I turn on the notebook and start Ubuntu 10.04 2.6.34;
.The wireless card seems to be dead: I can't connect via wireless, the card doesn't either receive the signal of any wireless network in the air;
.I go to System>Administration>Hardware Drivers, and see that the Broadcom STA drivers are not active (see the screenshot attached to this post);
.I try to activate the Broadcom drivers, but I receive the following message:



and the drivers keep not active... apparently.

In fact, after doing this, the wireless suddenly goes alive, and I can connect via wireless. But at the next reboot, I will again have to do the same procedure...

Any help?


Did you use ndiswrapper at one time? The picture shown seems to indicate so. If so, ndiswrapper and the STA driver are probably competing for dominance and simply confused. We probably need to get rid of one or the other.

---

### Post by michele.bartolettistella on 2010-07-12
I agree with you; in fact, I have already removed ndiswrapper (the screenshot is two-days old...) But it seems that the problem doesn't disappear. The Broadcom STA drivers always look as "inactive"...

---

### Post by paras301 on 2010-07-12
> **michele.bartolettistella said:**
> 
Hello,

currently I having to do with the same problem; I own a Dell Vostro 3700, and I installed Ubuntu 10.04 some days ago...

My Wireless card is a Broadcom, too, and when I try to activate the Broadcom third-part drivers from [COLOR=DarkRed]System>Administration>Hardware Drivers[/COLOR], I receive an error message.

I attached a[COLOR=DarkRed] screenshot[/COLOR] about these issues, hoping someone more expert will help us!

MBS

In my case the driver is perfectly installed. I tried re-installing the driver too, but its not coming up. I need help in getting the network card up.

Thankyou.

---

### Post by roomey on 2010-12-14
hi,
This worked for me twice, so it may work for you. When I went into jockey-kde it showed two drivers, Broadcom B43 wireless driver and Broadcom STA wireless driver.

when I activated the STA driver first it did not work, however, if I then activate the B43 driver, and then activate the STA driver again, it works!

---

