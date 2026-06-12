---
title: "wireless not connecting"
date: 2011-02-16
forum: Networking &amp; Wireless
---

### Post by philipballew on 2011-02-16
i have a Levano S10e intel atom preccessor and the net-book is not connecting wirelessly to the network. i have tried at two locations and even plugged in a exterlal wifi adapter. it wouldnt connect then either, the only way to get connected is to use a cat5 cable. here is the ifconfig output with no cat5 inserted and it not connecting to the internet.:
```
carina@carina-Lenovo:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:8b:49:f3:75  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:23:4e:ba:68:c1  
          inet6 addr: fe80::223:4eff:feba:68c1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:335 errors:0 dropped:0 overruns:0 frame:325
          TX packets:5 errors:16 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17420 (17.4 KB)  TX bytes:1750 (1.7 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
```

---

### Post by philipballew on 2011-02-17
bump

---

### Post by Sean Moran on 2011-02-17
> **philipballew said:**
> bump
I'm still quite a dunderhead when it comes to networking without a good length of RG-58 coax and a couple of BNC connectors with 50ohm terminators, but some quick terminal commands that I read on here a week or two ago might help to determine what's going on.  I also had major dramas getting my wifi to work with Meerkat, and resorted to Karmic, although I have a working 10.10 with wifi now, although that was by chance.

The commands I read on here before that 'might' be of some help were:
```

sudo ifconfig wlan0 up           # To open the wlan0 interface along with eth0 and eth1 .
sudo iwlist wlan0 scanning   # This will hopefully display a list of wifi access points if any.
sudo iwconfig wlan0 essid  [desired access point name]
sudo iwconfig wlan0 key [passphrase]
sudo dhclient wlan0             # Excuse me if my memory fails on that one. That should try to get connected.

```I hope that at least the first two parts might shed some light on this problem.  Sorry that I'm not as familiar with command-line wifi operations as I should be.  Good luck with it.

PS: The last command may just be 'sudo dhclient'.  I can't remember.

---

### Post by philipballew on 2011-02-17
i looked at those. is ifconfig showing no wlan meaning theres no wireless interface?

---

### Post by grahammechanical on 2011-02-17
First, does the user manual say anything about switching on the on board wireless adapter? Such as pressing fn+f12 key combination or something like that? So, is the on board wireless adapter switched on?

If it is, then does Ubuntu recognize the device? Do you see a network icon? If not, then go to System>Administration>Additional Drivers. Is the system suggesting that you activate a driver? Connect by ethernet and activate that driver. 

Regards.

---

### Post by Sean Moran on 2011-02-17
> **philipballew said:**
> i looked at those. is ifconfig showing no wlan meaning theres no wireless interface?
Yes, typing ifconfig in the terminal should list the wireless adaptor/s as wlan0, wlan1 etc. Sorry for the delay in reply - I was sleeping.  It's a lot of extra length to a post, but here is a concise listing from my current ifconfig to show what the extra items for wlan0 & wlan1 should look like:
```

user@trial-system:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:16:ea:15:63  
...  (roughly the same as usual)
lo        Link encap:Local Loopback  
...  (roughly the same as usual)
wlan0     Link encap:Ethernet  HWaddr 00:26:5e:38:e7:56  
          inet6 addr: fe80::226:5eff:fe38:e756/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:127 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12986 (12.9 KB)  TX bytes:5415 (5.4 KB)

wlan1     Link encap:Ethernet  HWaddr 00:19:cb:c3:3b:27  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:cbff:fec3:3b27/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1968 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1933 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1853330 (1.8 MB)  TX bytes:317598 (317.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-26-5E-38-E7-56-63-33-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster1  Link encap:UNSPEC  HWaddr 00-19-CB-C3-3B-27-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
I don't know what wmaster0 and wmaster1 are there for, but assume they're something related to wlan0 and wlan1.

Regarding the built-in adaptor on/off status, on my Compaq laptop, the Wireless button is beside the Power button, and seems to switch off the onboard wifi if I press it for a split second, and then switch back on if I press it for a second or two, but you've also tried another external adaptor, which should hopefully have been switched on by default when you plugged it into the USB socket, I assume.

---

### Post by philipballew on 2011-02-17
@ grahammechanical there is a switch marked wireless on/off. it is in the on position. plus i see the network icon and can pick up the available networks. it just attempts to connect and never does. but it has connected occasionally when i boot into an older kernel

---

### Post by philipballew on 2011-02-20
bump

---

### Post by starkiez on 2011-05-07
> **philipballew said:**
> @ grahammechanical there is a switch marked wireless on/off. it is in the on position. plus i see the network icon and can pick up the available networks. it just attempts to connect and never does. but it has connected occasionally when i boot into an older kernel


Yep me too. Happened after I deleted all my keyring's in the .gnome2 folder to get rid of the annoying asking for default password on startup.

It sees all the networks but can't connect!

---

