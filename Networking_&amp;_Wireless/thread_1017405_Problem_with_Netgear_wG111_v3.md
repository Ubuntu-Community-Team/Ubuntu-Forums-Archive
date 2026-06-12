---
title: "Problem with Netgear wG111 v3"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by Tony Flury on 2008-12-21
I am running Hardy Heron on an HP pavillion Dv6000 laptop.

The internal Broadcom wireless card seems to have died (again), and i am trying to use a Netgear wG111v3 Wifi USB Dongle (which i know works on Windows XP).

What I have done so far :

I know that the dongle is recognised on the USB port : 

```

tony@laptop:~$ lsusb
Bus 002 Device 004: ID 0c45:62c0 Microdia 
Bus 002 Device 002: ID 0846:4260 NetGear, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 105: ID 04fc:0015 Sunplus Technology Co., Ltd 
Bus 001 Device 003: ID 03f0:171d Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000  

```

I also know that the driver is correctly loaded in ndiswrapper (i used ndisgtk to do this)
```

tony@laptop:~$ ndiswrapper -l
wg111v3 : driver installed
	device (0846:4260) present

```

but : the system does not seem to recognise the dongle as a network adapter : 

```

lshw -C network
 Produces no output

```

but
```

lshw -C generic
....
  *-usb:0 UNCLAIMED
       description: Generic USB device
       product: NETGEAR WG111v3
       vendor: Manufacturer_NETGEAR
       physical id: 1
       bus info: usb@2:1
       version: 2.00
       serial: 001E2AB6719B
       capabilities: usb-2.00
       configuration: maxpower=500mA speed=480.0MB/s
....

```

I am not sure where to go from here - any assitance would be appreciated.

There are no power buttons on the dongle - and I know that the dongle works - at least in Windows XP.

---

### Post by Tony Flury on 2008-12-23
sorry to bump this.

---

### Post by Tony Flury on 2009-01-06
ok - I got my H/w recognised - basically i scrapped my 64 bit installation since i could not find a 64 bit driver that would work.

I am now on 32 bit Hardy Heron - and the USB dongle can see the network - woooo hooo :-)

However i can't connect - it keeps trying to connect but does not work

---

### Post by Tony Flury on 2009-01-08
can anyone help ? The router is using a 80 bit WEP connection, the Dongle identifies the network and i am prompted for the key, but the dongle wont connect.

When the internal Broadcom B43 card works then it can connect with the same network with the same key without a problem. However the B43 card is on the way out (and can't be repaired) so I am relying on being able to get the USB dongle working.

---

