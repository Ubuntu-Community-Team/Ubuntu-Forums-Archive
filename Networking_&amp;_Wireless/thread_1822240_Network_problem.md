---
title: "Network problem"
date: 2011-08-10
forum: Networking &amp; Wireless
---

### Post by Vaielab on 2011-08-10
Hello,

Today I started my computer who run under ubuntu 11.04 and I didn't have network anymore.
I could not ping the router (192.168.0.1) but everyone else was ok.

On my computer I have some virtualbox installed, and if I start them, I could go on the internet without any problem with them.
Since my last reboot, I didn't change any config on my computer, and I am the only one with the password for the router, so I will be surprise if any config had changed.

Here my ifconfig -a:
```

eth0      Link encap:Ethernet  HWaddr e0:69:95:78:0e:ab  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::e269:95ff:fe78:eab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14577 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8497 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17540278 (17.5 MB)  TX bytes:899519 (899.5 KB)
          Interrupt:20 Memory:fe700000-fe720000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

My /etc/network/interfaces
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

I tried to remove the 2 last line, but didn't change anything

And my /etc/hosts
```

127.0.0.1	             localhost
127.0.0.2 	localhost
127.0.0.3	             localhost


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

Of course, I tried to reboot my computer, reboot the router, disconnect the router, or reboot my network (both with /etc/init.d/networking restart and ifconfig eth0 down than up)

But absolutly nothing work... I cannot even ping my router
But everything work in my virtualbox machines

Anyone have an idea?!

---

### Post by jualin on 2011-08-10
It looks like your wireless card is not being recognized.
Please post the results of ```
lsusb
```.
Did you install your wireless driver using Ndiswrapper (if you don't know what this is then your probably didn't do it this way)?
If you did then post the results of the following command ```
ndiswrapper -l
```

When you say that everything works on the virtual machine, does this mean that the virtual machine is running within Ubuntu (Ubuntu as a host), or are you running the virtual machine within Windows (Windows as a host)?

---

### Post by moorhead98 on 2011-08-10
Try and lower the MTU value.
I had a problem like yours that was solved by lowering it to 1024.
Go to edit connections (in the wifi menu thing), and edit your eth0 connection (or whatever it is). On the first tab it should have a section called "MTU" and a drop down box with a list of values. Type in "1024" and save. Then restart, and all should be good.

---

### Post by Vaielab on 2011-08-10
etienne@CodeStation:~$ lsusb
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 001 Device 003: ID 045e:0752 Microsoft Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


I did not installed Ndiswrapper
And it's a wired cable, not wireless

My host is ubuntu 11.04 (that do not work)
And my virtual machine are both ubuntu & windows and both virtual machine work

---

### Post by nm_geo on 2011-08-10
Do the following in terminal Just Copy and paste commands
 
```
 
sudo lshw -C network

```
 
```
 
lspci -nn | grep 0200

```
 
```
 
nm-tool

```
 
Copy and paste results back in thread. Maybe we can spot something.

---

### Post by Vaielab on 2011-08-10
etienne@CodeStation:~$ sudo lshw -C network
sudo: unable to resolve host CodeStation
[sudo] password for etienne: 
  *-network               
       description: Ethernet interface
       product: 82579V Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 05
       serial: e0:69:95:78:0e:ab
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-k2 duplex=full firmware=0.13-4 ip=192.168.0.101 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:fe700000-fe71ffff memory:fe728000-fe728fff ioport:f040(size=32)
etienne@CodeStation:~$ 





etienne@CodeStation:~$ lspci -nn | grep 0200
00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 05)
04:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 03)
etienne@CodeStation:~$ 




etienne@CodeStation:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        E0:69:95:78:0E:AB

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.101
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

---

### Post by Vaielab on 2011-08-12
Anyone?
Since that day, every morning I have to reboot my computer 2-3times, reboot the router 2-3times, revoke my ip in the router 2-3times, than reboot pretty much everything again, and if i'm lucky I can get the internet in less than 15minutes

---

### Post by jualin on 2011-08-12
**Something that you already know:** It's very weird since you say that the Virtual machine guest internet works okay. I suspect it has something to do with the line "sudo: unable to resolve host CodeStation". Check [this post]("http://ubuntuforums.org/showthread.php?t=770801") Let me know if it helps.

This are the contents of my /etc/hosts file:
> 127.0.0.1	localhost
127.0.1.1	cari

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters


where "cari" is my computer name. I am guessing that should be "CodeStation" for you.

---

