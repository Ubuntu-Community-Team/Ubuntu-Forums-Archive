---
title: "NetworkManager: Detection of Ethernet connection"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by abhilash82 on 2009-05-26
I have upgraded to Ubuntu 9.04 and the NetworkManager (0.7.0.100) applet does not auto configure the ethernet connection through which I connect to the internet. 

The creation of a wired connection manually does not result in the detection of the 'eth0' network interface.

How is it possible to make the Network Manger applet to detect the available network connections?

Thanks,
ARK

---

### Post by cariboo on 2009-05-26
Could open an Application-->Accessories-->Termianl and type:

```
sudo lshw -C network
```

and paste it into your next post. The above command will print out the details of your network devices, whether they have been detected and if the drivers have been loaded.

---

### Post by kerry_s on 2009-05-26
> **abhilash82 said:**
> I have upgraded to Ubuntu 9.04 and the NetworkManager (0.7.0.100) applet does not auto configure the ethernet connection through which I connect to the internet. 

The creation of a wired connection manually does not result in the detection of the 'eth0' network interface.

How is it possible to make the Network Manger applet to detect the available network connections?

Thanks,
ARK


i came across that a couple of days ago on a friends system, i had to remove the eth0 entry in /etc/network/interfaces then reboot and then network manager would manage the eth0.

---

### Post by abhilash82 on 2009-05-27
> **cariboo907 said:**
> Could open an Application-->Accessories-->Termianl and type:

```
sudo lshw -C network
```

and paste it into your next post. The above command will print out the details of your network devices, whether they have been detected and if the drivers have been loaded.

I have pasted below the network details.

```
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 10
       serial: 00:e0:4c:e9:62:1f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=116.75.237.161 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
```

---

### Post by Iowan on 2009-05-27
DHCP? What happens if you try:```
dhclient eth0
```

---

### Post by abhilash82 on 2009-05-28
> **kerry_s said:**
> i came across that a couple of days ago on a friends system, i had to remove the eth0 entry in /etc/network/interfaces then reboot and then network manager would manage the eth0.

I removed the eth0 entry from the interfaces file and it worked (after a reboot). The network manager now detects my ethernet connection automatically.

Thanks for your support.

---

