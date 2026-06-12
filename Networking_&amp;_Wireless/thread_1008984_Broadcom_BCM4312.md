---
title: "Broadcom BCM4312?"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by XtremeGamer99 on 2008-12-12
I'm trying to get WEP craking working on my card.

I tried getting this to work a few months back but gave up due to lack of support for the chipset. Now it seems that the Broadcom chipset has gained enough support, and I would like to dive back into trying to crack my WEP.

Please note that I'm not trying to crack my neighbours connection or anything -- I'm doing this strictly to broaden my knowledge of wireless and Linux overall, and to give me something to do.

Let me start off by saying -- knowing if my card is supported / if my kernel is patched / if I'm using the correct driver -- this has been a big headache. :) I am using Ubuntu 8.10, with kernel version 2.6.27-8-generic. Do I have to patch this kernel? The aircrack-ng site says that the mac80211 driver (which include b43) needs no patch for the 2.6.27 kernel, but then goes on to say that it might ([link]("http://www.aircrack-ng.org/doku.php?id=mac80211&s=mac80211#fragmentation_attack_support")).

So my first question is: Do I need to patch my kernel? If so, how do I go about doing that (I generally don't mess with the kernel).

My next question: it seems that Ubuntu uses the wl driver be default. I would assume that I would need to use the b43 driver. How can I switch? Again, I'm not too familiar with kernel modules and drivers.

Thanks!

Some more info:
Machine:
```
Linux 2.6.27-8-generic x86_64
```

Interfaces (eth1 is the wireless):
```
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:3c:00:6e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:251 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:21:00:04:31:9f  
          inet addr:192.168.1.135  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ff:fe04:319f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:312 errors:0 dropped:0 overruns:0 frame:331
          TX packets:335 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:239551 (239.5 KB)  TX bytes:67752 (67.7 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:118 errors:0 dropped:0 overruns:0 frame:0
          TX packets:118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11413 (11.4 KB)  TX bytes:11413 (11.4 KB)

```
```
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:226  Noise level:166
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```

```
~$ lspci | grep Broadcom
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```

```
~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:04:31:9f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=192.168.1.135 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
```

---

### Post by Larppaxyz on 2008-12-12
I can confirm BCM4312 works with Ubuntu 8.10 default kernel. However, you need to install restricted drivers package.

Driver is named 'wl' and works perfectly with my HP 6735S.

You need to make sure that no modules named ssb, b43, or other variants are loaded before wl. My Ubuntu install did this automatically.

---

### Post by XtremeGamer99 on 2008-12-12
> **Larppaxyz said:**
> I can confirm BCM4312 works with Ubuntu 8.10 default kernel. However, you need to install restricted drivers package.

Driver is named 'wl' and works perfectly with my HP 6735S.

You need to make sure that no modules named ssb, b43, or other variants are loaded before wl. My Ubuntu install did this automatically.

This has nothing to do with my problem. It's my fault, actually -- I didn't specify what I was trying to do in the title, making the post have a different meaning.

I've fixed the title now. Hopefully Someone can help me. =)

---

### Post by Ayuthia on 2008-12-12
> **XtremeGamer99 said:**
> I'm trying to get WEP craking working on my card.

I tried getting this to work a few months back but gave up due to lack of support for the chipset. Now it seems that the Broadcom chipset has gained enough support, and I would like to dive back into trying to crack my WEP.

Please note that I'm not trying to crack my neighbours connection or anything -- I'm doing this strictly to broaden my knowledge of wireless and Linux overall, and to give me something to do.

Let me start off by saying -- knowing if my card is supported / if my kernel is patched / if I'm using the correct driver -- this has been a big headache. :) I am using Ubuntu 8.10, with kernel version 2.6.27-8-generic. Do I have to patch this kernel? The aircrack-ng site says that the mac80211 driver (which include b43) needs no patch for the 2.6.27 kernel, but then goes on to say that it might ([link]("http://www.aircrack-ng.org/doku.php?id=mac80211&s=mac80211#fragmentation_attack_support")).

So my first question is: Do I need to patch my kernel? If so, how do I go about doing that (I generally don't mess with the kernel).

My next question: it seems that Ubuntu uses the wl driver be default. I would assume that I would need to use the b43 driver. How can I switch? Again, I'm not too familiar with kernel modules and drivers.

Thanks!

Some more info:
Machine:
```
Linux 2.6.27-8-generic x86_64
```

Interfaces (eth1 is the wireless):
```
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:3c:00:6e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:251 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:21:00:04:31:9f  
          inet addr:192.168.1.135  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ff:fe04:319f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:312 errors:0 dropped:0 overruns:0 frame:331
          TX packets:335 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:239551 (239.5 KB)  TX bytes:67752 (67.7 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:118 errors:0 dropped:0 overruns:0 frame:0
          TX packets:118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11413 (11.4 KB)  TX bytes:11413 (11.4 KB)

```
```
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:226  Noise level:166
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```

```
~$ lspci | grep Broadcom
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```

```
~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:04:31:9f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=192.168.1.135 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
```

You will need to check your lspci -nn info and see if you have a 14e4:4315 card.  If you do, the b43 module is not supported for your card.  I don't recall seeing that the wl driver working with aircrack-ng.  Sorry.

---

### Post by XtremeGamer99 on 2008-12-15
> **Ayuthia said:**
> You will need to check your lspci -nn info and see if you have a 14e4:4315 card.  If you do, the b43 module is not supported for your card.  I don't recall seeing that the wl driver working with aircrack-ng.  Sorry.

```
lspci -nn | grep Broadcom
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
```

So I guess I'm screwed with this particular card? Any word on if they are working on supporting 14e4:4315? Or would it be more likely to wait until the wl driver supports the aircrack suite?

---

### Post by Ayuthia on 2008-12-15
Last I heard from the b43 mailing list, they are still working on the reverse engineering process.  There is no timeline on when it will be complete.  I am not for sure which will come first, 4315 support on b43 or wl support on aircrack.

---

### Post by waffen on 2008-12-18
Hello,

I can do work the aircrack package:

```

root@mario-laptop:~# lspci -nn | grep Broadcom

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 01)

```

But when I try:

```

root@mario-laptop:~# aireplay-ng -9 eth1
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.

root@mario-laptop:~# airmon-ng start eth1


Interface	Chipset		Driver

eth1		UNKNOWN		wl (monitor mode enabled)

```

I cant see the Chipset name.. any idea?

---

### Post by Ayuthia on 2008-12-18
> **waffen said:**
> Hello,

I can do work the aircrack package:

```

root@mario-laptop:~# lspci -nn | grep Broadcom

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 01)

```

But when I try:

```

root@mario-laptop:~# aireplay-ng -9 eth1
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.

root@mario-laptop:~# airmon-ng start eth1


Interface	Chipset		Driver

eth1		UNKNOWN		wl (monitor mode enabled)

```

I cant see the Chipset name.. any idea?

Your card is a 14e4:4312 rev 01 so you should be able to use the b43 driver.  You are currently using the wl module so I am not for sure if it will work.  I have seen or heard anyone that has been able to use this with the wl module.

---

### Post by lonecoyote911 on 2008-12-18
****the problem with this driver should be resolved by Dec 23rd

---

### Post by Ayuthia on 2008-12-18
> **lonecoyote911 said:**
> ****the problem with this driver should be resolved by Dec 23rd

Any links to this info?  Inquiring minds want to know!!!

---

### Post by Mine's Ultimate R on 2008-12-19
> **lonecoyote911 said:**
> ****the problem with this driver should be resolved by Dec 23rd

which driver!? the wl driver? if so i'm happy!!!!!!!!!!

---

### Post by waffen on 2008-12-19
> **Ayuthia said:**
> Your card is a 14e4:4312 rev 01 so you should be able to use the b43 driver.  You are currently using the wl module so I am not for sure if it will work.  I have seen or heard anyone that has been able to use this with the wl module.


Yes you are right! I change to b43 and all work, but when I try to obtain IVs I dont see the counter move from zero, only beacons change...any idea?

Thanks!

---

### Post by cdcr1985 on 2008-12-19
Dec 23rd? christmas gift?? xD I hope that :P

---

### Post by cdcr1985 on 2008-12-26
And somebody knows something about broadcom's driver?

---

### Post by greenpee on 2009-01-12
Im having similar problems with my

Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

so from what I understand wl has to be replaced with b43?

---

### Post by Ayuthia on 2009-01-12
> **greenpee said:**
> Im having similar problems with my

Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

so from what I understand wl has to be replaced with b43?

Either one should work.  If you are having problems with the wl, try the b43.  They both work pretty well with the 4311 rev 01 card.  Can you let me know which version of Ubuntu you are using (Hardy, Intrepid, etc.)?

---

### Post by phil0stine on 2009-02-17
They don't have much on the aircrack forums, has anybody heard word on the status of the 14e4:4315 support?? Anxiously waiting...

---

### Post by Ayuthia on 2009-02-17
> **phil0stine said:**
> They don't have much on the aircrack forums, has anybody heard word on the status of the 14e4:4315 support?? Anxiously waiting...

There is no change for this chipset.  Work is still being done for the b43 module and the wl module is not supported by aircrack.

---

### Post by phil0stine on 2009-02-17
Thanks for the quick reply. I will keep my eyes peeled for updates.
Any helpful links (besides the obvious)?

---

### Post by infernosoft on 2009-08-05
So....has anyone been able to successfully use aircrack with their BCM4312. I'm going to receive a laptop in a couple of days that uses the BCM4312 chipset, and was wondering if it works??
 
I really hope so!
 
Thanks.

---

### Post by Ayuthia on 2009-08-05
> **infernosoft said:**
> So....has anyone been able to successfully use aircrack with their BCM4312. I'm going to receive a laptop in a couple of days that uses the BCM4312 chipset, and was wondering if it works??
 
I really hope so!
 
Thanks.
If it has the 14e4:4315 chipset (check via lspci -nn), it will not work with aircrack.  The Broadcom STA and NDISwrapper modules do not provide this functionality.

---

