---
title: "Xubuntu 10.04 IBM Thinkpad 390X Netgear WG511 PCMIA wireless adapter"
date: 2011-01-21
forum: Networking &amp; Wireless
---

### Post by bondmatt on 2011-01-21
Edit: after upgrading everything using a usb to ethernet port converter ndiswrapper is working perfectly

I do not have internet access on a laptop I am trying to upgrade. It has no ethernet port. I may resort to buying a USB to ethernet adapter but I spent more than I would like to have already.

I have tried every command in the HOWTO for wireless difficulties and posted the output.

Any advice would be greatly appreciated.

Thank you,
- Matt Bondy

```
lspci
```
```
06:00.0 Ethernet Controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
```

```
ifconfig
```
```
 lo    Link encap: Local Loopback
             inet addr:127.0.0.1 Mask:255.0.0.0
             inet6 addr:  ::1/128 Scope: Host
             UP LOOPBACK RUNNING   MTU: 16436   Metric:1
             RX packets:4 errors:0 dropped:0 overruns:0 frame:0
             TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
             collisions:0 txqueelen:0
             RX bytes:240 (240.0B) TX bytes:240 (240.0B)
```

```
 iwconfig 
```
```
 lo      no wireless extensions 
```

```
 sudo lshw -C network 
```
```
 *-network UNCLAIMED
description: Ethernet controller
product: 88w8335 [Libertas] 802.11b/g Wireless
vendor: Marvell Technology Group Ltd.
physical id: 1
bus info: pci@000:06:00.0
version: 03
width: 32 bits
clock: 66MHz
capabilities: pm cap_list
configuration: latency=0
resources: memory:24000000-2400ffff memory:24010000-2401ffff

```

```
 uname -mr 
```
```
 2.6.32-21-generic i686 
```

---

### Post by ajgreeny on 2011-01-21
Install ndisgtk, then go to System ->Administration ->Windows Drivers (I think that's where it is) and use that to install the Windows XP or identical Windows 2000 WG511v2.INF file from the netgear CD for that pcmcia adapter.

10.04 will not connect with WPA, I'm afraid, but will with WEP.  10.10 can use either WEP or WPA, so I now run 10.10 on my old laptop (Acer Travelmate 2200), but I use gnome ubuntu, not xubuntu.  Should be the same wireless.

---

### Post by bondmatt on 2011-01-21
WEP should be fine. In another post I made in the general forum someone said I might not need ndiswrapper. I was playing with that for a while. I had some trouble with the error with the kernel incompatibility that requires ndiswrapper be compiled.

I run linux on the computer I am using now to post on the forum but I am certainly not an expert. I have never (knowingly) compiled anything. I also had an issue with the synaptic package manager using the live cd as a repository (on the old IBM). It seemed like if a package had more than one dependency the second (and every other) package would never be found. If I go one at a time and install packages trying to get to the 'root' package I was successful but this was taking a ridiculous amount of time. I tried installing packages from the command prompt (I had never really dont this before so at least I learned something) but it worked no better.

I have now purchased a usb to ethernet adapter hoping it will work. If not I am not sure what I will do.

Thank you for the advice,
- Matt

---

### Post by ajgreeny on 2011-01-21
That very same card with marvell chipset works very well in my laptop with ndiswrapper, which is what ndisgtk installs the driver with, so there is no reason why yours should not do so as well.  The ndiswrapper I use is not compiled by me but from the repos.

For you synaptic problem, make sure the CD as repository is not checked in the software sources; the live CD will not work like that anyway, and it will just confuse the system.  All the packages needed as dependencies of other packages should then be available.

---

### Post by bondmatt on 2011-01-21
I bought the usb to ethernet cable just to get the old ibm connected to the internet. I found a forum post from years indicating that the same adapter from the same cheap electronics retailer probably works with ubuntu. It is working just fine (from factorydirect.ca, no brand name on it). I was worried the old (lone - to give an indication of the age) usb port on the laptop would be slow but it is plenty fast enough.

It looks like I might have some luck getting this wireless card to work.

Thank you for the advice,
- Matt

---

