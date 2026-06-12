---
title: "Can't connect to router via WIFI &quot;Bad password&quot;"
date: 2011-07-14
forum: Networking &amp; Wireless
---

### Post by fontis on 2011-07-14
Hey guys!
I can't seem to get my wifi connection going on my laptop.
The wired connection works fine, and the wifi seems to detect networks, but upon trying to connect I get "Bad password". Network at this location uses WPA2.

Upon lspci | grp "Network" I get

```
02:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe
```

and on lshw -C network I get;

```
*-network               
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: e0:2a:82:18:77:6d
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-10-generic firmware=0.11 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:d3000000-d300ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 64:31:50:5e:d0:ad
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.0.0.2 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:45 ioport:2000(size=256) memory:d1004000-d1004fff memory:d1000000-d1003fff memory:d1010000-d101ffff

```


ANY help would be greatly welcomed.

---

### Post by haqking on 2011-07-14
well the obvious answer would be:

Enter the correct key/password ;-)

have you checked, try setting the password/key to a very simple one then test it ?

---

### Post by fontis on 2011-07-14
Yes I know. The password is 12345678. The password works perfectly fine on Windows, Android, iOS, OS X. It's just this Ubuntu install that refuses to connect to it. :confused:

---

### Post by haqking on 2011-07-14
> **fontis said:**
> Yes I know. The password is 12345678. The password works perfectly fine on Windows, Android, iOS, OS X. It's just this Ubuntu install that refuses to connect to it. :confused:

have you tried creating a permanent connection in network manager with the password stored.

also what happens if you drop from wpa ?

---

### Post by fontis on 2011-07-14
Well, I don't know how to permanently add a connection. But I did start off Network manager and try to edit the connection with no use.

And I can't drop WPA on the router here. It's not mine. Besides it works perfectly fine for all other machines.

---

### Post by haqking on 2011-07-14
> **fontis said:**
> Well, I don't know how to permanently add a connection. But I did start off Network manager and try to edit the connection with no use.

And I can't drop WPA on the router here. It's not mine. Besides it works perfectly fine for all other machines.

in network manager choose to create new wireless connection.

You might want add the mac of the router though it shouldnt make no difference.

I take it there is no reason why you should not be allowed to connect right ? such as mac address filtering on the router itself ?

---

### Post by fontis on 2011-07-14
Yup I tried that, still doesn't work. And you're right dear, there is no MAC filtering enabled on the router. It's freely accessible by all other devices, it's just ubuntu refusing to play ball atm :<

---

### Post by haqking on 2011-07-14
i see you are using maverick meerkat, i take it you havent recently upgraded to 11.04 have you ? 

i have seen some issues inn11.04 with the RT3090 ?

Was it ever working ? and is it just this connection it is not working with ?

---

### Post by fontis on 2011-07-14
Ah!
I fixed it!
Turns out it's a known problem that is solved by simply blacklisting a few other options.

Solution so far seems to be to do
```
sudo gedit /etc/modprobe.d/blacklist.conf
```

and add the following lines:

```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
```

That did the trick. Now the permanent connection with WIFI seems to work. 
Can't seem to "see" any other networks though, but I guess that's another headache.

---

### Post by haqking on 2011-07-14
> **fontis said:**
> Ah!
I fixed it!
Turns out it's a known problem that is solved by simply blacklisting a few other options.

Solution so far seems to be to do
```
sudo gedit /etc/modprobe.d/blacklist.conf
```and add the following lines:

```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
```That did the trick. Now the permanent connection with WIFI seems to work. 
Can't seem to "see" any other networks though, but I guess that's another headache.


yeah the blacklist was the next thing i was gonna mention which is why i asked if you were using 11.04 as i saw that was a solutuon for people.

anyways glad you got it sorted

---

### Post by fontis on 2011-07-14
Yea thanks for the replies.

Hmm. I seem to be able to finally connect now when choosing the network from the menu. But I keep getting disconnected all the time now. I mean very frequently. But I suspect this might rather be an issue with the entry not being added as ad-hoc since the WAP I'm trying to access atm is an ad-hoc router rather than main.

---

