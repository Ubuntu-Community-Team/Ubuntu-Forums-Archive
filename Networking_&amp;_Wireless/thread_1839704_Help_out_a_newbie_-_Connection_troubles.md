---
title: "Help out a newbie - Connection troubles"
date: 2011-09-06
forum: Networking &amp; Wireless
---

### Post by Aeretic on 2011-09-06
I'm a new Linux user, I've just installed Ubuntu 11 and my ethernet connection (ISP: Fastweb - Italy) isn't working well.

Sometimes it's really fast, sometimes it takes ages and then it fails to load the page.
It's a matter of minutes, if not only seconds between one slow and another and it doesn't take much to work again but it's really annoying...

On Windows Seven this problem doesn't exist.



```

aeretic@Ish:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 1c:6f:65:c9:a8:ab  
          inet addr:37.2.106.203  Bcast:37.2.106.255  Mask:255.255.255.0
          inet6 addr: fe80::1e6f:65ff:fec9:a8ab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17055 errors:0 dropped:17055 overruns:0 frame:17055
          TX packets:13233 errors:0 dropped:52 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21372819 (21.3 MB)  TX bytes:1728091 (1.7 MB)
          Interrupt:41 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:279 errors:0 dropped:0 overruns:0 frame:0
          TX packets:279 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25291 (25.2 KB)  TX bytes:25291 (25.2 KB)

```

---

### Post by praseodym on 2011-09-06
Hi,

set the nameservers of you provider or the google public nameservers 8.8.8.8 and 8.8.4.4 in the network-manager applet ("IPv4-settings"->change to "Automatic (DHCP), addresses only". Separate them by comma

---

### Post by Aeretic on 2011-09-06
> set the nameservers of you provider or the google public nameservers 8.8.8.8 and 8.8.4.4 in the network-manager applet


Where exactly?
I can edit

DNS Servers:
Search domains:
DHCP Client ID:


I changed to "Automatic (DHCP) addresses only" and it's not working at all, the wired is connected but i can't load web pages, it doesn't even try like before, it just says that i can't.


And thanks for your time ;)

---

### Post by praseodym on 2011-09-06
Put them into "DNS Servers", separated per comma. After that close all and

```
sudo service network-manager restart
```

---

### Post by HereInOz on 2011-09-06
Your first post has me fascinated.  The IP addresses listed in your Ethernet connection are public, routable addresses.  37.2.106.203 is a netherlands address, by the look of it.  So how are you actually connecting to the Internet?  

What type of connection is it which gives your machine a public routable address, rather than a private address behind a router?  Do you have a direct cable connection or something similar?

---

### Post by Aeretic on 2011-09-06
I really don't know much about nets, but my ISP is fastweb, which is a "mega LAN" (so far i know).

I connect to the internet via ethernet, there are 2-3 PCs connected in my home, 1 via cable (mine) and 2 wireless laptops.


@praseodym: Tnx for the help again, i'm not on my PC atm but i'll try asap ^^

---

### Post by Aeretic on 2011-09-06
Now it works much better, but sometimes (quite often) it fails to load  the page. There's still something that doesn't work... it's pretty  annoying when i'm downloading updates/stuffs and it stops.

---

### Post by bkratz on 2011-09-06
> **Aeretic said:**
> I'm a new Linux user, I've just installed Ubuntu 11 and my ethernet connection (ISP: Fastweb - Italy) isn't working well.

Sometimes it's really fast, sometimes it takes ages and then it fails to load the page.
It's a matter of minutes, if not only seconds between one slow and another and it doesn't take much to work again but it's really annoying...

On Windows Seven this problem doesn't exist.



```

aeretic@Ish:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 1c:6f:65:c9:a8:ab  
          inet addr:37.2.106.203  Bcast:37.2.106.255  Mask:255.255.255.0
          inet6 addr: fe80::1e6f:65ff:fec9:a8ab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17055 errors:0 [COLOR=Red]dropped:17055 [/COLOR]overruns:0 frame:17055
          TX packets:13233 errors:0 [COLOR=Red]dropped:52 [/COLOR]overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21372819 (21.3 MB)  TX bytes:1728091 (1.7 MB)
          Interrupt:41 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:279 errors:0 dropped:0 overruns:0 frame:0
          TX packets:279 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25291 (25.2 KB)  TX bytes:25291 (25.2 KB)

```

You do show some errors, perhaps the MTU value is set to high (1500).

---

### Post by Aeretic on 2011-09-06
At the moment i'm online with a new automatic connection called "Auto Ethernet" (Automatic DHCP).

"Auto eth0" (with Automatic (DHCP) addresses only) isn't working.
i tried another ifconfig -a and there are still the dropped packets and the connection isn't stable...


```
aeretic@Ish:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 1c:6f:65:c9:a8:ab  
          inet addr:37.2.106.203  Bcast:37.2.106.255  Mask:255.255.255.0
          inet6 addr: fe80::1e6f:65ff:fec9:a8ab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:602 errors:0 dropped:602 overruns:0 frame:602
          TX packets:525 errors:0 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:552452 (552.4 KB)  TX bytes:93496 (93.4 KB)
          Interrupt:42 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4152 (4.1 KB)  TX bytes:4152 (4.1 KB)

```

---

### Post by gastly on 2011-09-06
I'm having a similar problem. Does it happen with Windows too, Aeretic?
For me, it's Linux only (tried a few distro's like Arch, same problem).

You should try to ping the gateway and see if there are any lost connection problems "Destination Host Unreachable" or high ping times.
Oh and also post the output of **lshw -C network** please :)

---

### Post by Aeretic on 2011-09-07
Now i'm totally offline, i can't connect ubuntu at all.
And yes, windows works perfectly...



"Auto eth0" only works when i set method to "Shared with other computers", but then i still can't see any web pages.
Yesterday the other connection, Auto Ethernet, was working with "Automatic (DHCP)" as method.

I really can't understand...

---

