---
title: "problem with n/w connection"
date: 2011-06-07
forum: Networking &amp; Wireless
---

### Post by sandy0594 on 2011-06-07
Hey all,i have Ubuntu 10.10 installed in my pc.Today i happen to update the linux headers,did some post installation things to enable my n/w connection.But,strangely i am not even seeing the connections icon on gnome-panel.have a look at the attachment

```

sandy@ubuntu:~$ uname -r
2.6.35-30-generic
sandy@ubuntu:~$ sudo lshw -C network
[sudo] password for sandy: 
  *-network               
       description: Ethernet interface
       product: Atheros Communications
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: bc:ae:c5:50:83:1f
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1C driverversion=1.0.1.14 duplex=full firmware=L1e latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:44 memory:febc0000-febfffff ioport:ec00(size=128)


```

Can someone kindly suggest me what to do in order to enable my n/w connection

---

### Post by sandy0594 on 2011-06-08
No one seems to be interested to reply,solved it myself with the help of [http://ubuntuguide.net/fix-network-connection-icon-disappear-on-top-right-panel](http://ubuntuguide.net/fix-network-connection-icon-disappear-on-top-right-panel)

---

