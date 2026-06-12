---
title: "Ubuntu 12.04 doesn't show wired connection, Win7 does"
date: 2012-05-27
forum: Networking &amp; Wireless
---

### Post by mark90 on 2012-05-27
I have a wired connection in my student dorm room which doesn't come up in network-manager with 12.04. It does work with Windows 7 though,so it's not anything hardware related,i would say.
On a spare partition on my HD i tried installing another 12.04,just to be sure it wasn't some configuration of mine being wrong: turns out,it doesn't work either.
The funny thing is that NM would recognize the connection until yesterday,so i thought some update had to with this,but there was nothing in the logs that seems to be able to break something network related..

My /etc/NetworkManager/NetworkManager.conf:

   ```
 [main]
    plugins=ifupdown,keyfile
    dns=dnsmasq
    
    [ifupdown]
    managed=false
```

My /etc/network/interfaces:

    ```
auto lo
    iface lo inet loopback
    
    auto eth0
    #iface eth0 inet dhcp
```

I don't know why the last line is commented,but i tried uncommenting it but it wouldn't work,and even worse it would say "device unmanaged". I then tried setting managed=true but it went back to not recognizing the connection,so i just rolled everything back.

ifconfig eth0 :

    ```
eth0      Link encap:Ethernet  HWaddr 00:26:9e:0a:2a:e3  
              UP BROADCAST MULTICAST  MTU:1500  Metric:1
              RX packets:0 errors:0 dropped:0 overruns:0 frame:0
              TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
              Interrupt:47 Base address:0xc000
``` 

lshw -C network:

    ```
*-network
           description: Ethernet interface
           product: RTL8111/8168B PCI Express Gigabit Ethernet controller
           vendor: Realtek Semiconductor Co., Ltd.
           physical id: 0
           bus info: pci@0000:03:00.0
           logical name: eth0
           version: 02
           serial: 00:26:9e:0a:2a:e3
           size: 10Mbit/s
           capacity: 1Gbit/s
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
           configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
           resources: irq:47 ioport:5000(size=256) memory:d1010000-d1010fff memory:d1000000-d100ffff memory:d1020000-d102ffff
```

lspci:

    ```
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
```

/var/log/dpkg.log (just the part for yesterday,because yesterday connection worked):
[http://pastebin.ubuntu.com/1010341/](http://pastebin.ubuntu.com/1010341/)

The wired connection isn't even seen by ubuntu..it's like the cable was unplugged!
Anybody that can help me?

---

### Post by praseodym on 2012-05-27
Remove anything but the 2 "lo" lines, remove any connection in the NM-applet in "cable" and "DSL", if any, and reboot.

---

### Post by mark90 on 2012-05-27
Ok,so it still doesn't show up in NM, **but** NM created automatically a "Wired connection 1" (which doesn't work,though)

---

### Post by praseodym on 2012-05-27
Remove the package "resolvconf", and reboot.

---

### Post by mark90 on 2012-05-27
Still nothing..plus i tried,just to see the output:

```
sudo ifup eth0
Ignoring unknown interface eth0=eth0.

sudo ifdown eth0
ifdown: interface eth0 not configured
```

---

### Post by praseodym on 2012-05-28
Did it work with the Live-CD?

Tried to reset the BIOS?

---

### Post by mark90 on 2012-05-28
Ok,turns out it's not ubuntu's problem: there were some issues with cables and switches and stuff..
Thanks a lot for your time anyway!Really appreciated it! :)

---

