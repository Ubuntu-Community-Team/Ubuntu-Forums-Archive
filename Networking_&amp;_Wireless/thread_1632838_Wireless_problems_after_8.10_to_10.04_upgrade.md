---
title: "Wireless problems after 8.10 to 10.04 upgrade"
date: 2010-11-28
forum: Networking &amp; Wireless
---

### Post by Nick Newman on 2010-11-28
Hi,

I have an out-of-the-box Belkin G wireless router.  I also have a Linksys USB adapter on a particular box.

When I run the Ubuntu 8.10 live CD on that box I can see the router's SSID, I supply the password, and all is fine.  I think that rules out any problems with the router or the ISP.

When I run the Ubuntu 10.04 on that same box I can still see the SSID but when I try to connect to it the DHCP fails.  Checking the system logs I see the DHCPDISCOVER entries but no corresponding DHCPOFFER responses.

So this seems on the surface to be a DHCP problem.  To get around this I tried to edit the connection to use manually supplied settings.  On the 8.10 system I supplied:
```

IP=192.168.2.200,
Netmask=255.255.255.0
Gateway=192.168.2.1
DNS=192.168.2.1

```
and again all worked just fine.  But when I supply the same values to the 10.04 system it does not work.  Even attempts to ping the router (192.168.2.1) fail.

So if this fails then perhaps the problem is more fundamental than DHCP?

I have tried searching the net for quite a while and found a number of similar problems, but clear solutions seem to be lacking (or I haven't come across them).  One common suggestion is to blacklist the ipv6 module.  I tried that and it seemed to have no effect.

Since this worked so well in 8.10 and doesn't work in 10.04 I'm hoping that someone will have an idea of what has changed and what I could do to fix the problem.

Any ideas?
Thanks,
Nick

---

### Post by uncaspi on 2010-11-29
Will you please post the result of sudo ifconfig and /etc/network/interfaces

---

### Post by Nick Newman on 2010-11-29
Thank you for the reply.

Here are the results that you asked for.  The 10.04 system was cleanly booted from the live CD and an attempt made to connect to the wireless prior to these.

```

ubuntu@ubuntu:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:95:69:31  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:e0380000-e03a0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6960 (6.9 KB)  TX bytes:6960 (6.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:76:52:5a  
          inet6 addr: fe80::212:17ff:fe76:525a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27580 (27.5 KB)  TX bytes:2300 (2.3 KB)

ubuntu@ubuntu:~$ 

```

```

ubuntu@ubuntu:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

ubuntu@ubuntu:~$ 

```

I think it may also be worth trying the ndiswrapper, even though it did not seem to be necessary with 8.10.  Do you agree?

Thanks,
Nick

---

### Post by uncaspi on 2010-11-29
I wouldn't tried that first. Let us get more info about the Linksys USB.
Please post sudo lsbusb

---

### Post by mikewhatever on 2010-11-29
Upgrading from 8.10 to 10.04 is quite a fit, as the direct path is not supported. Did you really do four consecutive upgrades 8.10->9.04->9.10->10.04?

---

### Post by Nick Newman on 2010-11-30
@uncaspi

I think that should be lsusb?  Here is the output:
```
ubuntu@ubuntu:~$ sudo lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 04e8:0100 Samsung Electronics Co., Ltd Kingston Flash Drive (128MB)
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 413c:3200 Dell Computer Corp. Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 13b1:000d Linksys WUSB54G Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ubuntu@ubuntu:~$ 


```

@mikewhatever

No, despite the title I chose (which I now see is misleading) this is not an upgrade.  This is a clean install.  In fact I am running these tests from the 10.04 live CD to absolutely ensure that I have not accidentally messed with any configurations.

Thanks!
Nick

---

### Post by mikewhatever on 2010-11-30
> **Nick Newman said:**
> 

@mikewhatever

No, despite the title I chose (which I now see is misleading) this is not an upgrade.  This is a clean install.  In fact I am running these tests from the 10.04 live CD to absolutely ensure that I have not accidentally messed with any configurations.


Cool, thanks for clarifying.

---

### Post by uncaspi on 2010-11-30
I found these threads for your WUSB54G adapter.

[http://ubuntuforums.org/showthread.php?t=1603421&highlight=Linksys+WUSB54G](http://ubuntuforums.org/showthread.php?t=1603421&highlight=Linksys+WUSB54G)


[http://ubuntuforums.org/showthread.php?t=1472475&page=4&highlight=Linksys+WUSB54G](http://ubuntuforums.org/showthread.php?t=1472475&page=4&highlight=Linksys+WUSB54G)


[http://ubuntuforums.org/showthread.php?t=1569392&highlight=Linksys+WUSB54G](http://ubuntuforums.org/showthread.php?t=1569392&highlight=Linksys+WUSB54G)

---

### Post by Nick Newman on 2010-12-01
@uncaspi

Thank you for finding those links.  I'll take a careful look later and let you and other readers know how it goes.

Perhaps the solution of the first link is simplest - buy a different adapter!  (But I'll try other options first).

Nick

---

### Post by Nick Newman on 2010-12-12
Okay, apologies for the delay in getting back about those threads you suggested.

The first thread seems to end with the user giving up on Linksys.  I'll get back to that.

The second thread seems to suggest that Maverick with kernel 2.6.35-22-generic solved the problem.  I tried Mint 10 which is based on those, and it did not seem to resolve anything for me.

The third thread suggested changing the router configuration.  Allow me a small diversion:

[INDENT]*It is interesting that I used to have a Linksys router too, and ALL of the machines that used it started having problems with large downloads.  They would start off fine and then slow to a crawl so they never finished.  A friend with the same router and ISP had the same problems.  I decided to risk the princely sum of $20 on a Belkin G router (Newegg) and problems instantly disappeared.  My friend did the same too, same result.*[/INDENT]

Back to the topic.  Changing the security settings on the router made no difference.

So back to the first thread.  Emboldened by my success with the router I splashed out another $20 on a TP-Link USB wireless adapter.  (Newegg again!)  Linux claimed to support it and it had good reviews.  When I plugged it in I was starting to get ready to fiddle around with things to see if I could get it to connect when I noticed it had already connected!

I would say my take-away message from this is that if you have a Linksys component and it seems to be giving trouble, just spend a little money to get a non-Linksys replacement.  I'm not saying that with enough effort the Linksys part couldn't be made to work, but for me (and probably most people) the $20 replacements are cheap to avoid the fuss.


Nick

---

### Post by uncaspi on 2010-12-12
Glad it works. Yes Linksys + Ubuntu + wireless = could be problems.

---

