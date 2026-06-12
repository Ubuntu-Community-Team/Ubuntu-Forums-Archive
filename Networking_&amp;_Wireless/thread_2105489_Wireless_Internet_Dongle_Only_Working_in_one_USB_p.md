---
title: "Wireless Internet Dongle Only Working in one USB port - why??"
date: 2013-01-16
forum: Networking &amp; Wireless
---

### Post by Andrew F in Australia on 2013-01-16
Hi All,

More aggravating than anything else, but a Huawei E188 wireless 3G dongle that used to work in any USB port now only works in one specific port of the four available on this laptop (HP Probook 4730s.)  It did used to work in all four ports.

All other USB devices work in the other ports, including USB2.0 & USB 3.0 ports.

Is it possible that it's been configured to only read in one USB2.0 port accidentally? 

I'd like to fix it before it gives up the ghost all together. (Left the USB dongle in the port for five minutes with no response.)

Here's configuration that I think is relevant, but I'm sure I've missed something.

Does anybody know a cause or possible solution??

With thanks in advance,

AF
```
horace@horace-HP-ProBook-4730s:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 007: ID 12d1:1c07 Huawei Technologies Co., Ltd. 
Bus 001 Device 003: ID 138a:003c Validity Sensors, Inc. VFS471 Fingerprint Reader
Bus 002 Device 003: ID 1bcf:2888 Sunplus Innovation Technology Inc. 
horace@horace-HP-ProBook-4730s:~$ 
horace@horace-HP-ProBook-4730s:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr e4:11:5b:3f:e2:b3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:56 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:212 errors:0 dropped:0 overruns:0 frame:0
          TX packets:212 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17496 (17.4 KB)  TX bytes:17496 (17.4 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.122.238.253  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:15236 (15.2 KB)  TX bytes:3730 (3.7 KB)

ra0       Link encap:Ethernet  HWaddr 74:de:2b:fe:78:c7  
          inet6 addr: fe80::76de:2bff:fefe:78c7/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:537 errors:0 dropped:0 overruns:0 frame:0
          TX packets:196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:66967 (66.9 KB)  TX bytes:0 (0.0 B)
          Interrupt:19 

```output of /etc/modules```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rt3592sta
usbserial vendor=0x12d1 product=0x1c07
```Here's the entire lshw output as I'm not sure what's relevant in this case if anything at all
```

                logical name: eth0
                version: 06
                serial: e4:11:5b:3f:e2:b3
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multica
st=yes port=MII speed=10Mbit/s
                resources: irq:56 ioport:2000(size=256) memory:d4404000-d4404fff memory:d4400000-d4403fff
        *-pci:6
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 8
             vendor: Intel Corporation
             physical id: 1c.7
             bus info: pci@0000:00:1c.7
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:46 memory:d4500000-d45fffff
           *-usb
                description: USB controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:27:00.0
                version: 04
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:19 memory:d4500000-d4501fff
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:d4b08000-d4b083ff
:
```

---

### Post by Andrew F in Australia on 2013-01-16
Weird.

I had a thought after I posted the enquiry above.

I shutdown the computer, 
then plugged the device into one of the ports that wasn't recognising the Wireless Dongle
After this, I restarted the computer.   (hoping to force the machine to recognise the Wireless Dongle)
It took about three or four minutes to get to the log in screen.
But, after this, the USB Dongle works again in any port.

Weird - purely an academic question now as the thing's working again.

Regards,

AF

---

