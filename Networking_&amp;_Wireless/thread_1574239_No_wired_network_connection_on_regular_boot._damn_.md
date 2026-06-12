---
title: "No wired network connection on regular boot. damn it."
date: 2010-09-14
forum: Networking &amp; Wireless
---

### Post by winchendonsprings on 2010-09-14
Since this morning I cannot get any network connection working from regular boot up. I'm beyond frustrated.

I booted into windows xp for the first time in at least a year today and connected fine.
I booted into recovery mode -> then failsafe graphics mode , two times and had internet one of the times.
I'm writing this from live cd.
 
I have a feeling it is something super simple to fix but ...

Any ideas or help would be greatly appreciated. 

Here is my ifconfig -a from regular(not working network boot)

```
ry@ry-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:24:1d:71:13:55  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:33 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:24:1d:71:13:57  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:34 Base address:0x4000 

eth2      Link encap:Ethernet  HWaddr 00:0a:cd:18:7f:27  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ry@ry-desktop:~$ 
```--------

and here is my ifconfig -a from the recover/low graphics mode(working connection)

```
ry@ry-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:24:1d:71:13:55  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:33 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:24:1d:71:13:57  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:34 Base address:0x4000 

eth2      Link encap:Ethernet  HWaddr 00:0a:cd:18:7f:27  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:cdff:fe18:7f27/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9583 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7716 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9667841 (9.6 MB)  TX bytes:1189464 (1.1 MB)
          Interrupt:17 Base address:0x8000 

eth0:avahi Link encap:Ethernet  HWaddr 00:24:1d:71:13:55  
          inet addr:169.254.4.167  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:33 Base address:0x2000 

eth1:avahi Link encap:Ethernet  HWaddr 00:24:1d:71:13:57  
          inet addr:169.254.4.177  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:34 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

ry@ry-desktop:~$
```

edit: Also I have reset the modem and router multiple times and it didn't help

---

### Post by MaindotC on 2010-09-14
> **winchendonsprings said:**
> I booted into windows xp for the first time in at least a year today and connected fine.
I booted into recovery mode -> then failsafe graphics mode , two times and had internet one of the times.

The operating system has nothing to do with your connection seeing as how network communication are all constructed using open standards.  What you have here is a configuration issue and according to your ifconfig none of your network interfaces have an ip address.  Are you using NetworkManager?

If not you can get an ip address by typing```
sudo dhclient
```.

I know you didn't know this but just to save you some time in the future - this has nothing to do with your wired connection:>  Also I have reset the modem and router multiple times and it didn't help  The wired connection is just between your machine and the access point (it's not called a router) and everything beyond that doesn't really have anything to do with Ubuntu.

---

### Post by winchendonsprings on 2010-09-14
thanks for taking time to help

> The operating system has nothing to do with your connection seeing as  how network communication are all constructed using open standards.I just mentioned that to rule the obvious out, and to clarify that I have, in fact, had luck making a connection. I do have a physical cable that runs from my computer to a modem.

>  Are you using NetworkManager?I don't think I am using networkmanager. it always tells me that the last connection made was - never. for example under wired - eth0 - never eth2 - never


before I leave the live cd I'm on and boot into my regular set up, what will I do after?

```
 sudo dhclient
```thanks again

---

### Post by MaindotC on 2010-09-14
If you're using NetworkManager there will be an icon in the top right displaying the status of your connection and it will have options similar to System -> Preferences -> Network.

dhclient will send a request to your access point for an ip address.  As long as your AP is giving out DHCP leases you should then be able to commnunicate on your network.  I'm certain your problem is much deeper than that but unfortunately the only thing I see wrong is that you didn't have an ip address.  Let me know how it goes.

---

### Post by winchendonsprings on 2010-09-14
well strAlan, I have to tell you, I ran sudo dhclient, and it's fixed. simple as that. I feel dumb. 

thanks again

---

### Post by MaindotC on 2010-09-14
It's cool - np.  Unfortunately you should not have to run that because [NetworkManager]("https://help.ubuntu.com/community/NetworkManager0.7") should try to reconnect you when the connection fails so you may want to try rebooting and making sure the connection stays.

---

