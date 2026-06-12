---
title: "How to set a permanent IP address for eth0 ?"
date: 2011-02-28
forum: Networking &amp; Wireless
---

### Post by oygle on 2011-02-28
The IP address I want for the gateway computer is 192.168.1.100

As I have 'sharing' enabled in Network manager, there is no provision there to specify the IP address for eth0. That is, cannot manually set it there.

Every time I boot up, the IP address changes to 

```

eth0      Link encap:Ethernet  HWaddr *******************  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: ********************* Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:6025 (6.0 KB)
          Interrupt:17

```

and so I have to do this

```

$ sudo ifconfig eth0 192.168.1.100

```

to make it the correct IP address again.

---

### Post by pressko on 2011-02-28
Hi ,
U forgot to set the mask prefix ... maybe that's the problem and why not try to set it up though GUI Network Manager ?

---

### Post by Hedgehog1 on 2011-02-28
> **oygle said:**
> The IP address I want for the gateway computer is 192.168.1.100


Recognizing that everyone network is a little different:

My router (which does assign all the IP addressed)  Has a 'Static DHCP table' in the UI that will allow me to set a hard IP address for a specific MAC address.

Does your setup allow the same?

:KS

---

### Post by Tabu.it on 2011-02-28
With gnome System->Preferences->Network Connection->Wired->Add->Ipv4->Method:Manual->Add

---

### Post by oygle on 2011-02-28
> **pressko said:**
> 
U forgot to set the mask prefix ... maybe that's the problem

I don't know what the prefix is, do you mean 192.168.1.0/24 to specify the complete range within 192.168.1.nnn ??

> **pressko said:**
> 
and why not try to set it up though GUI Network Manager ?

I need to have sharing enabled, as it is the gateway. Under NM, the IPv4 tab, if I use the 'Share to other computers' option, it greys out the ability to specify the IP address.

So, to me, NM has no provision to do it, when the 'share' option is used under IPv4 tab.

Or, ... I may have missed something.

---

### Post by tdhfox21 on 2011-02-28
I'm dropping in here as I am having issues with the networking gui as well. I am running 10.4 and it doesn't seem to have anywhere to actually configure the wired connections. If i open network tools and select the appropriate network device, then select configure, the network settings shows up but the first tab shown is general.... there is no connection tab. Clearly different to instructions and demos. it seems clear to me that after what seems to be years of issues with this, it still does not work.

---

### Post by oygle on 2011-02-28
> **Hedgehog1 said:**
> My router (which does assign all the IP addressed)  Has a 'Static DHCP table' in the UI that will allow me to set a hard IP address for a specific MAC address.

Does your setup allow the same?


No, I can't do that, as I have no router. The internet connection is ppp0 using wireless broadband, a USB dongle.

---

### Post by oygle on 2011-02-28
> **Tabu.it said:**
> With gnome System->Preferences->Network Connection->Wired->Add->Ipv4->Method:Manual->Add

I'm having [internet connection sharing problems]("http://ubuntuforums.org/showthread.php?t=1693652") with the computer, and was advised to use the 'Shared to other computers' option.

I used to have 'manual' and it worked just fine, but the 'share' option greys out the ability to specify the IP address.

---

### Post by oygle on 2011-02-28
> **tdhfox21 said:**
> I'm dropping .... 

use the IPv4 tab, and then the 'Manual' option. For me I used to put

Address  192.168.1.100
Netmask  255.255.255.0
Gateway  0.0.0.0

for the computer that is the gateway, and

Address  192.168.1.101
Netmask  255.255.255.0
Gateway  192.168.1.100

for the client computer.

---

### Post by dmizer on 2011-02-28
Why is having an IP of 10.42.43.1 a problem? It works just as well as 192.168.100.

When using ICS, network manager automatically picks a free IP range for sharing. It should work fine without you having to do anything at all.

---

### Post by dmizer on 2011-02-28
I am closing this thread. Please keep your ICS related discussion in your main thread here: [http://ubuntuforums.org/showthread.php?t=1693652](http://ubuntuforums.org/showthread.php?t=1693652)

This way, everyone (meaning you, and the people trying to help you) is following the same thread.

---

