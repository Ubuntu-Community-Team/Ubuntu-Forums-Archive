---
title: "Wired Network Problems"
date: 2011-05-28
forum: Networking &amp; Wireless
---

### Post by Cicko on 2011-05-28
hello guys, ive just installed ubuntu some days ago and im still learning.

Ive got this problem that i cant connect to my wired connection?
ive tried to boot the grub.cfg as i dont have the menu.lst with these settings "noapic nolapic acpi=off"
and i still cant get it to work??

any suggestions on this one would be greatly appreciated

---

### Post by poolet on 2011-05-28
hello , post the output of 

```
sudo lshw -C network 
``````
iwconfig 
```and 

```
lspci
```

---

### Post by Cicko on 2011-05-28
its quite an old pc but here they are

```
cicko@Pc-01:~$ sudo lshw -C network
[sudo] password for cicko: 
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:00:07.0
       logical name: eth0
       version: 10
       serial: 00:10:a7:15:0c:d2
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:10 ioport:d000(size=256) memory:de001000-de0010ff
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth1
       version: 74
       serial: 00:11:09:08:fc:cf
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=full latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
       resources: irq:11 ioport:ec00(size=256) memory:de003000-de0030ff
cicko@Pc-01:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.

cicko@Pc-01:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:06.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev f0)
00:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)
cicko@Pc-01:~$ 

```

---

### Post by poolet on 2011-05-28
Try this one....

```
sudo su 
``````

mii-tool -F 10baseT-HD
/etc/init.d/networking restart
mii-tool -R

```if it's works.... you should save it at rc.local


gedit /etc/rc.local  

and add the above into that file: 

**Note:** don't touch,  at the end of file "exit 0" instruction

---

### Post by Cicko on 2011-05-28
it doesn change anything i still cant get my internet to work?
i maybe should have mentioned im going directly from a modem to a router and from the router to my pc

---

### Post by Iowan on 2011-05-28
That machine has two ethernet ports? 
What are the results of **ifconfig -a**?

---

### Post by Cicko on 2011-05-28
```
cicko@Pc-01:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:10:a7:15:0c:d2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0xd000 

eth1      Link encap:Ethernet  HWaddr 00:11:09:08:fc:cf  
          inet6 addr: fe80::211:9ff:fe08:fccf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:187 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17820 (17.8 KB)  TX bytes:8664 (8.6 KB)
          Interrupt:11 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:39896 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39896 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:169591020 (169.5 MB)  TX bytes:169591020 (169.5 MB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.233.83.72  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:149611 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98670 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:194129392 (194.1 MB)  TX bytes:14931316 (14.9 MB)

cicko@Pc-01:~$ 

```

EDIT: I got it working lol =/ the comment on 2 ethernet ports made me look for the other! this is quite embarrasing =/

Thanks alot for the help guys really appreciate it!

---

