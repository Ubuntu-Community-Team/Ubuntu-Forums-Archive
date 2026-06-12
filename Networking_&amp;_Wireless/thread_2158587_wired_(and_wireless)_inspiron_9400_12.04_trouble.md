---
title: "wired (and wireless) inspiron 9400 12.04 trouble"
date: 2013-06-29
forum: Networking &amp; Wireless
---

### Post by baligirl on 2013-06-29
Hi everyone,

I know this has been asked a number of times, and I have attempted a number of the suggested solutions, but to no avail.  And I can't tell you what I did, as I am thoroughly confused!  Please help if you can.  I would love to get my wired internet working!  And my wireless, too, at some point....

I have a Dell Inspiron 9400 laptop with a wired ethernet cable (the wireless works too, but I don't have a wireless router set up here at home).  I've been using Ubuntu for several years, version 10.04, and that has recently come to the end of the LTS.  So I bought a new hard drive and installed 12.04.02 LTS (32-bit).  (And I just reinstalled it fresh again, in case I messed anything up).

When I am booted with the 12.04.02 LTS Live CD, the wired internet works fine.  At times it will even recognize that there are wireless networks nearby.  It has a Broadcam STA wireless driver (not activated), and it comes up with a little icon to install restricted drivers, etc....

However, once I take out the Live CD and boot into my new hard drive where I've actually installed the 12.04.02 LTS, there is no action at all.  The wired doesn't work, the wireless doesn't seem to be active, and there are no drivers installed.  And since I am unable to connect to the internet, I'm guessing that I will have to download whatever driver or package that I need to a USB stick, and then install it from there.  Or is there some way that I can grab a driver from my Live CD / RAM here, copy it to a USB, and then copy it into my hard drive?

Thanks so much for your help!!

Jennie



Here is some info - but these are from my LIVE CD (where the wired ethernet works), not from the troublesome hard disk installation:


cat /etc/network/interfaces

```

auto lo
iface lo inet loopback

```


cat /etc/NetworkManager/nm-system-settings.conf
```

cat: /etc/NetworkManager/nm-system-settings.conf: No such file or directory

```


dmesg | grep -e eth0 -e bcm

```

[    5.328581] b44 ssb1:0: eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:18:8b:da:72:20
[   65.329599] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   94.234724] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   94.235144] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   97.804199] b44 ssb1:0: eth0: Link is up at 100 Mbps, full duplex
[   97.804205] b44 ssb1:0: eth0: Flow control is off for TX and off for RX
[   97.804494] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2792.764298] b44 ssb1:0: eth0: powering down PHY
[ 2794.244776] b44 ssb2:0: eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:18:8b:da:72:20

```


ifconfig -a

```

eth1      Link encap:Ethernet  HWaddr 00:18:8b:da:72:20  
          inet addr:192.168.1.47  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:8bff:feda:7220/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2334 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3820102 (3.8 MB)  TX bytes:354310 (354.3 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1605 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1605 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:154482 (154.4 KB)  TX bytes:154482 (154.4 KB)

```

---

### Post by Hadaka on 2013-06-29
Hi, please boot to your harddrive installation
then open a terminal and enter..
```
sudo apt-get remove --purge bcmwl-kernel-source
```
boot again..
is the wired connection working?

---

### Post by baligirl on 2013-06-30
Hadaka,

Thanks so much for your advice!  I did as you suggested.  It seemed to indicate that it was removing the dkms package and rebuilding the kernel.  I figured this would take some time, so I waited, and waited.... many hours.  Finally I killed it, rebooted, and tried it again.  Then it compained that dkpg was interrupted, and to manually run

```
sudo dpkg --configure -a
```

to correct the problem, which I did.  That reported that it was removing the dkms, and downloading andinstalling some updates.  YES!!  Now my wired is working!  I can hardly believe it, as I have been fiddling with this for three weeks now.  THANK YOU SO MUCH!!

The Broadcam STA wireless driver is there now, but not activated.  Dare I attempt this, or will this cause a conflict with my wired connection somehow?

Again, I THANK YOU!!!!

Jennie

---

### Post by Hadaka on 2013-06-30
Hi, glad the wired is working !!!
NO do not load the broadcom sta driver..'
it will conflict with your current driver and you will
be without a wired connection again..so ..no do not load it.
If you would like to get your wireless working...please post
the output of..
```
lspci -nn | egrep '0200|0280'
```
thanks.

---

### Post by baligirl on 2013-06-30
Here is the output:

```

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

```

Thanks!!!!

---

### Post by Hadaka on 2013-06-30
this should do it..
please do..
```
sudo apt-get install linux-firmware-nonfree 
sudo modprobe b43
```
thanks.

---

### Post by baligirl on 2013-06-30
Hadaka,

It worked!!  I cannot begin to thank you enough!!  I so appreciate your help here!  You got me up and running again.  THANK YOU!!!!

Jennie

---

### Post by Hadaka on 2013-06-30
You are welcome. Glad everything is working.
please mark this thread solved..
How to -> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
be sure to edit the first post of this thread to mark solved.
thanks.

---

