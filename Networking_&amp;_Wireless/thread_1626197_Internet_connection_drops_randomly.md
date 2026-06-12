---
title: "Internet connection drops randomly"
date: 2010-11-20
forum: Networking &amp; Wireless
---

### Post by karthick87 on 2010-11-20
My internet connection drops randomly in ubuntu but works fine in XP.The connection is not disconnected but i cant browse any sites,so what i do is i will reboot my system so that i can surf again but after few minutes the same problem is happening again..Can anybody help me?

---

### Post by mikewhatever on 2010-11-20
Hm..., interesting. What's the output of **nm-tool** ?

---

### Post by uncaspi on 2010-11-20
There are many thing you could try. For instance change the channel and / or increase txpower among other things. Also use OpenDNS nameservers.

sudo iwconfig wlan0 txpower 20 channel 1 mode managed

wlan0 is an example and you may put in the logical name of your card. Recently in a thread I read changing the MAC address solved the problem. And at last I could be a driver problem.

---

### Post by karthick87 on 2010-11-20
> **mikewhatever said:**
> Hm..., interesting. What's the output of **nm-tool** ?

```
karthick@Ubuntu-desktop:~$ nm-tool 

NetworkManager Tool

State: connected


** (process:5328): WARNING **: error: failed to read connections from org.freedesktop.NetworkManagerUserSettings:
    The name org.freedesktop.NetworkManagerUserSettings was not provided by any .service files
- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unmanaged
  Default:           no
  HW Address:        00:1C:C0:AB:17:70

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

```

---

### Post by uncaspi on 2010-11-20
Try sudo /sbin/ifconfig eth0 mode managed

---

### Post by karthick87 on 2010-11-20
> **uncaspi said:**
> Try sudo /sbin/ifconfig eth0 mode managed


```
karthick@Ubuntu-desktop:~$ sudo /sbin/ifconfig eth0 mode managed
mode: Unknown host
ifconfig: `--help' gives usage information.

```

---

### Post by mikewhatever on 2010-11-20
karthick87, there is no active wireless interface according to the output. Is the wireless on?
Can you also post the output of **sudo lshw -C network** .

---

### Post by karthick87 on 2010-11-20
```
karthick@Ubuntu-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:1c:c0:ab:17:70
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.10 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:e000(size=256) memory:ff820000-ff820fff memory:ff800000-ff81ffff(prefetchable)

```

---

### Post by mikewhatever on 2010-11-20
Not sure why I thought you were talking about wireless. It's wired, and I don't see any reference to DNS servers in the nm-tool output. Must have been disconnected when you posted it.

---

### Post by karthick87 on 2010-11-20
> **mikewhatever said:**
> Not sure why I thought you were talking about wireless. It's wired, and I don't see any reference to DNS servers in the nm-tool output. Must have been disconnected when you posted it.

Who told you that i am talking about wireless..It's wired and i am not disconnected when  i posted the last one.

---

### Post by mikewhatever on 2010-11-20
> **karthick87 said:**
> Who told you that i am talking about wireless..It's wired and i am not disconnected when  i posted the last one.

No one, that's what I alluded to in post #9, and the output of nm-tool wasn't the last one.
Try following uncaspi's suggestion and use OpenDNS as your dns servers.

---

