---
title: "Trouble installing DWA-130 USB Wireless adapter"
date: 2011-02-13
forum: Networking &amp; Wireless
---

### Post by Sidhiel on 2011-02-13
Hello all,

I'm trying to use a D-Link DWA-130 wireless adapter with my desktop running Ubuntu 10.10. I've been scouring the forums (and google of course) and really can't understand why it's not working.

The output from "iwconfig wlan0 is:

```
wlan0 no such device
```

So here is where I ask the stupid question: must you have a wireless card in the computer to use a wireless usb adapter? I built the computer myself you see and was looking to save some money.

Thanks for your help in advance.

---

### Post by bkratz on 2011-02-13
> **Sidhiel said:**
> Hello all,

I'm trying to use a D-Link DWA-130 wireless adapter with my desktop running Ubuntu 10.10. I've been scouring the forums (and google of course) and really can't understand why it's not working.

The output from "iwconfig wlan0 is:

```
wlan0 no such device
```

So here is where I ask the stupid question: must you have a wireless card in the computer to use a wireless usb adapter? I built the computer myself you see and was looking to save some money.

Thanks for your help in advance.



All you need is a usb port. I use a version of the DWA-130, there are 5 versions--each has a different chipset. Mine is the A1 version. The version number is on the label just after the DWA number.

---

### Post by Sidhiel on 2011-02-13
Yeah, I was afraid of that. I have the A1 version too, installed the driver using ndiswrapper etc. Still nothing, it's not showing up anywhere except under lsusb.

---

### Post by bkratz on 2011-02-13
I always use the ndisgtk gui and have installed it on all versions since 8.10 successfully (well 9.10 did give me a lot of problems!).  
Were the two files you stuck somewhere named 

 MRVW245.SYS  and NETMW245.INF

?

---

### Post by Sidhiel on 2011-02-13
Yes and yes. I used the ndisgtk gui too. It says that the hardware is detected, but I have no luck actually using it.

---

### Post by bkratz on 2011-02-13
> **Sidhiel said:**
> Yes and yes. I used the ndisgtk gui too. It says that the hardware is detected, but I have no luck actually using it.

Could you copy/paste the output of the following:

```
ndiswrapper -l
sudo lshw -C Network
sudo iwlist scan

```


the l is a lowercase L, be sure to capitalize the C above.

---

### Post by Sidhiel on 2011-02-13
ndiswrapper -l

```
netmw24c : driver installed
	device (07D1:3B11) present

```



sudo lshw -C Network
```
sudo] password for jacob: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 06
       serial: e0:cb:4e:ce:80:20
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:45 ioport:e800(size=256) memory:f8fff000-f8ffffff memory:f8ff8000-f8ffbfff memory:febf0000-febfffff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: 86:51:22:02:ab:5d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.119 link=yes multicast=yes

```

sudo iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

usb0      Interface doesn't support scanning.

```

---

### Post by bkratz on 2011-02-13
Don't know what usb0 is.

this is what I get back for ndiswrapper -l

netmw245 : driver installed
	device (07D1:3B11) present

note it has a different driver name. Are you sure you have the same driver names?  If so and you PM me I will send you my drivers. I know they work!

---

### Post by Sidhiel on 2011-02-13
Oh, right, sorry. The 24c driver is the 64-bit driver, or at least what I thought it was. The 245 driver was invalid.

---

### Post by bkratz on 2011-02-13
So is this a 64 bit install? The driver I use is 32!

what is the output of 

uname -mr

?

---

### Post by Sidhiel on 2011-02-13
> **bkratz said:**
> So is this a 64 bit install? The driver I use is 32!

what is the output of 

uname -mr

?


Yeah, sorry, shoulda said that earlier.

uname -mr

```
2.6.35-25-generic x86_64

```

So I suppose it's possible that 64 bit isn't supported yet?

---

### Post by bkratz on 2011-02-13
Sorry, but I went to the D-Link website and they don't seem to offer a 64 bit driver for the version A that I can find unless it is on the installation disk (which is out of state for me!). If you see one make sure that you get the xp or 2000 version. Wish i could have been more help, but since they have 4 more versions since the A, I doubt they ever will support it in 64 bits.

---

