---
title: "wired network connection active but no internet"
date: 2009-11-27
forum: Networking &amp; Wireless
---

### Post by Nikontu on 2009-11-27
Hi !

I just recently made some updates on ubuntu 9.10 (also installed openvpn), after what my internet connection stopped to work. I removed openvpn and followed the instruction of peepingtom on [http://swiss.ubuntuforums.org/showthread.php?p=8276560](http://swiss.ubuntuforums.org/showthread.php?p=8276560)
But my internet connection still does not work, although the NetworkManager Applet says that "the wired network connection XXX is active".
I have a manually configured IP.
Can you please tell me what should I do ? Here is some supplementary info:


**ifconfig :**
> eth0      Link encap:Ethernet  HWaddr 00:1a:a0:b8:81:ad
          inet addr:134.76.118.9  Bcast:134.76.118.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:a0ff:feb8:81ad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:156 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:20641 (20.6 KB)  TX bytes:3957 (3.9 KB)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3988 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3988 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:239280 (239.2 KB)  TX bytes:239280 (239.2 KB)**sudo lshw -C network**:
       > description: Ethernet interface
       product: NetXtreme BCM5754 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:a0:b8:81:ad
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5754-v3.15 ip=134.76.118.9 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:fe7f0000-fe7fffffin **/etc/network/interfaces** I have :
> auto lo
iface lo inet loopbackin **/etc/NetworkManager/nm-system-settings.conf** i have : 
> [main]
plugins=ifupdown,keyfile

no-auto-default=00:1a:a0:b8:81:ad,

[ifupdown]
managed=false
when i run **sudo /etc/init.d/networking restart**, it gives me:
 > * Reconfiguring network interfaces...                                                                                                                              Ignoring unknown interface eth0=eth0.Thank you very much for your help !

---

### Post by Nikontu on 2009-11-30
Anybody has any idea? any suggestions??

Please help!!!

---

### Post by davidm84 on 2009-11-30
1st how far can you ping? and 2nd have you set "default route" or "DNS" properties?

 whenever I have those problems I just re-install OS!!! haha

---

### Post by kja999 on 2009-11-30
As above .. have you checked what your default gateway is set to ?
 
if its missing:
sudo route add default gw 192.168.x.x

---

### Post by Nikontu on 2009-11-30
Thank you very much, it was indeed a problem with the gateway. Now that it is well configured, everything is working again :)

---

