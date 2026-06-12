---
title: "Wireless card issues"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by k508 on 2010-04-30
Hi there, I have just upgraded from 9.10 to 10.04 and now my wireless card isn't being detected as far as I know. It was working perfectly in the previous version. At the moment I've physically put an ethernet cable straight to the router. Any help would be appreciated :)

ifconfig:
```

iash@Jebus:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:76:6a:08:f1  
          inet6 addr: fe80::20c:76ff:fe6a:8f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1663 (1.6 KB)  TX bytes:4216 (4.2 KB)
          Interrupt:20 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

ash@Jebus:~$ 

```

Copied from lspci
```

02:00.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)

```

sudo lshw -C network
```

ash@Jebus:~$ sudo lshw -C network
  *-network:0 UNCLAIMED   
       description: Network controller
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32 maxlatency=28 mingnt=10
       resources: memory:fa400000-fa401fff
  *-network:1
       description: Ethernet interface
       product: VT6105/VT6106S [Rhine-III]
       vendor: VIA Technologies, Inc.
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: eth0
       version: 8b
       serial: 00:0c:76:6a:08:f1
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.2.2 latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
       resources: irq:20 ioport:b000(size=256) memory:fa403000-fa4030ff
ash@Jebus:~$ 

```

---

### Post by k508 on 2010-04-30
Bump

Any help would be greatly appreciated. Thanks.

---

### Post by bkratz on 2010-04-30
> **k508 said:**
> Bump

Any help would be greatly appreciated. Thanks.



Look at posts 8 and on of the following: it may suggest a direction
to go

[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/509265](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/509265)

---

### Post by k508 on 2010-04-30
Thanks for the help. I eventually got it working. Apparently there were drivers for my wlan and bluetooth that weren't installed even though they were installed automatically in the last version.

Not to worry, all up and running :)

---

### Post by sub5even on 2010-05-02
Hi what exactly did you do? I've got the same problem!

---

### Post by k508 on 2010-05-03
> **sub5even said:**
> Hi what exactly did you do? I've got the same problem!
Do you have the same card as me? If not, I don't think what I did will help you at all. There were some bluetooth/PRISM drivers I found in the ubuntu repositories that fixed it for me.

---

### Post by ubunnewb on 2010-05-09
I have exactly the same problem & card installed. I played around a bit with the drivers available in the ubuntu repositories, but couldn't get it to work. Can you pls indicate exactly which drivers you installed as I would really like to get this card to work.. tnx!

edit: 
Suddenly solved it myself by installing "linux-firmware-nonfree" using synaptic package manager. Maybe someone else is helped with this info.

---

### Post by 666j.e.t on 2010-05-12
same problem can you give a guide to the fix please

---

### Post by elwylly on 2010-05-14
Hi,

Please, could you explain a little bit better what to do? I have a similar problem with a SMC prism GT card. I get the same outputs as you (except for models, etc) and I have no clue how to enable my card or assign a proper driver.

Thanks!

---

### Post by artfrik on 2010-05-14
> **ubunnewb said:**
> 
Suddenly solved it myself by installing "linux-firmware-nonfree" using synaptic package manager. Maybe someone else is helped with this info.

It help me too!!! BIG THANKS!

---

### Post by ubunnewb on 2010-05-16
Installing the non-free drivers:
System -> Administration -> synaptic package manager, and then search for: "linux-firmware-nonfree" and install

However, when using WLAN my system sometimes 'freezes' with no other option than forcing a reboot. Does someone have the same problem and knows a way to deal with it? Or if someone could tell me where to look for what exactly caused the pc to freeze. (tried var/log/messages & syslog but couldn't really find anything helpful there).

thanks.

---

### Post by DrScum on 2010-06-01
I've got the same problem: wlan adapter working in previous version and not working in 10.04. From the posts above I gather that the adapter needs non-free firmware, which is no longer installed with 10.04. My problem now is that I have no option to connect to the internet with the machine in question other than through the very wlan adapter that is not working. 

Can anyone tell me how to download the software and install it from a usb stick or something?

---

### Post by peterthevicar on 2010-07-12
download the deb package from [http://packages.ubuntu.com/lucid/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/lucid/all/linux-firmware-nonfree/download) and put it on a USB stick.

Then mount the USB stick on your isolated machine and, in a terminal, use the command:
```

sudo dpkg -i /path-to-stick/linux-firmware-nonfree*.deb


```

---

