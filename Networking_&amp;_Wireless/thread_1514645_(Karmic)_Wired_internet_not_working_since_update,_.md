---
title: "(Karmic) Wired internet not working since update, wless not working since yesterday"
date: 2010-06-21
forum: Networking &amp; Wireless
---

### Post by LindisfarneJazzClub on 2010-06-21
[LEFT]Hello,[/LEFT]
 
[LEFT]I have been looking around the forums searching for similar problems, it seems not only me had this problem. About a month ago I did a regular update via Upd Manager. The next day - no wired connection.[/LEFT]
Still managable, since the local library has wireless. Now that won't work either.
 
[LEFT]Just after I upgraded from Jaunty, I accidentally removed NetwMngr from the top right corner of the screen, but that should not have anything to do with how the program works, right? I now cannot reach NM, if I run it from the terminal, nothing happens visibly.[/LEFT]
 
[LEFT]I have tried a few tips i found in posts here: 
-hard/cold reboot
-disabling IPv6 in Mozilla Firefox
-pppoeconf shows no respons from the Access Concentrator, with possible reasons 1: network&cables 2: another running pppoe process
-assigning a static ip is not working, since NetwMng won't work visibly (that is, through a window in my GUI)
-pinging anything else than 127.0.0.1 just prints *"connect: Network is unreachable"*
*-*getting a new driver from [HTML]http://linuxwireless.org/download/compat-wireless-2.6[/HTML][/LEFT]
 
 
fconfig -a 
```
eth0   Link encap: Ethernet   HWaddr 00:0a:e4:ee:23:7f 
 
[LEFT]      UP BROADCAST MULTICAST MTU:1500  Metric:1

      RX packets:0 errors:0 dropped:0 overruns:0 frame:0
[LEFT]      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:0
      RX bytes:240 (240.0 B) TX bytens:240 (240.0 B)[/LEFT]
[/LEFT]

 
 
 
 
[LEFT]lo      Link encap:Local Loopback

      inet addr:127.0.0.1 Mask: 255.0.0.0
[LEFT]      inet6 addr:  :: 1/128 Scope:Host
     UP LOOPBACK RUNNING  MTU: 16436 Metric:1
     RX packets:4 errors:0 dropped:0 overruns:0 frame:0
     TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:0
     RX bytes:240 (240.0 B) TX bytens:240 (240.0 B)[/LEFT]
[/LEFT]

 
 
 
 
[LEFT]wlan0  Link encap: Ethernet   HWaddr 00:14:a4:6b:b6:6e

      UP BROADCAST MULTICAST MTU:1500  Metric:1
[LEFT]      RX packets:0 errors:0 dropped:0 overruns:0 frame:0
      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1000
      RX bytes:0 (0.0 B) TX bytens:0 (0.0 B)[/LEFT]
[/LEFT]

 
 
 
 
[LEFT]wmaster0   Link encap:UNSPEC  HWaddre 00-14-A4-6B-B6-6E-00-00-00-00-00-00-00-00-00-00

              UP RUNNING MTU:0 Metric:1
[LEFT]              RX packets:0 errors:0 dropped:0 overruns:0 frame:0
              TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000
              RX bytes:0 (0.0 B) TX bytens:0 (0.0 B)[/LEFT]
[/LEFT]

 
 
 

``` 
 
 
 
[LEFT]sudo lshw -C network[/LEFT]
```

[LEFT]*-network:0 [/LEFT]
 
[LEFT]    description: Wireless interface

    product: AR2413 802.11bg NIC
[LEFT]    vendor: Atheros Communications Inc
    physical id: 5
    bus info: pci@0000:06:05.0
    logical name: wmaster0
    version: 01
    serial: 00:14:a4:6b:b6:6e
    width: 32 bits
    clock: 33MHz
    capabilities: pm bus_master cap_list logical ethernet physical wireless
    configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
    resources: irq:21 memory:b0100000-b010ffff
*-network:1
    description: Ethernet interface
    product: RTL-8139/8139C/8139C+
    vendor: Realtek Semiconductor Co., Ltd.
    physical id: 7
    bus info: pci@0000:06:07.0
    logical name: eth0
    version: 10
    serial: 00:0a:e4:ee:23:7f
    size: 10MB/s
    capacity: 100MB/s       
    width: 32 bits
    clock: 33MHz
    capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
    configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
    resources: irq:20 ioport:3000(size=256) memory:b0110000-b01100ff[/LEFT]
[/LEFT]

 
 
 

``` 
 
 
 
[LEFT]I can't remember that *-network:0 was wmaster0 before, the two networks used to be eth0 & wlan0 respectively. [/LEFT]
 
 
sudo cat /etc/network/interfaces
```

 
[LEFT]# info ... [/LEFT]
 

[LEFT]#The loopback network interface
[LEFT]auto lo
iface lo inet loopback[/LEFT]
[/LEFT]

 

[LEFT]#The primary network interface
[LEFT]auto eth0
#iface eth0 inet dhcp /[/LEFT]
[/LEFT]

 

```
 
 
[LEFT]Thankful for any help avaliable!

/Björn[/LEFT]

---

### Post by SnuShogge on 2010-06-21
I have had the same or similar problem. However my connection disapears randomly (it seams). The output of ifconfig, cat /etc/network/interfaces is as it should be, except for the missing connection. 

This has happend twice and the only solution i've found is to restart, over and over again. Last time i shut down the system, pulled out the power cord, put it back in, started and i had connection again (a last resort). Maybe something wrong with the motherboard/bios. 

I've got asus motherboard with intel h55 chipset ans realtec semiconductor network card. (Detailed spec are not available since I'm on vacation)

Hope there is an explaination and a solution to this.

---

### Post by regala on 2010-06-21
> **LindisfarneJazzClub said:**
> [LEFT]Hello,[/LEFT]
 
```


[LEFT]#The primary network interface
[LEFT]auto eth0
#iface eth0 inet dhcp /[/LEFT]
[/LEFT]

 

```
 
 
Thankful for any help avaliable!


hum, well, if you don't have networkmanager any more and if this is your interfaces file, it is expected you don't have any network beyond 127.0.0.1

either your interfaces are managed by networkmanager, either you have to configure them in interfaces file.
so you gotta uncomment the iface line dealing with eth0 (and remove the trailing /)
and then
```

ifup eth0

```
should issue the dhcp requests to configure eth0.

br

Mathieu

---

### Post by Iowan on 2010-06-21
If you want Network Manager to control the interface, comment out the "auto eth0" line. If you want hte */etc/network/interfaces* file to be in control, you *might* need to completely remove Network Manager... I've seen reports that configuring via "interfaces" only "seems" to work.

---

### Post by LindisfarneJazzClub on 2010-06-23
Thanks for your reply!
 
SnuShogge: I tried the reboot, no luck there.
 
regala & Iowan: How do I uncomment the lines? What commands to use?
I don't want to remove NetworkManager, it has worked just fine before. I forgot to mention that the wired connection stopped working a few days before I started having problems with NtwMngr
The slash in 
 
[LEFT]> #The primary network interface
[LEFT]auto eth0
#iface eth0 inet dhcp /[/LEFT]
[LEFT] 
was a typo, sorry about that![/LEFT]
[/LEFT]

---

### Post by LindisfarneJazzClub on 2010-06-28
Did some basic library work, found out the meaning of "comment / -out", tried your tips and UP IT GOES!

Now NetworkManager handles eth0, and /etc/network/interfaces is in time out.

Thanks a lot!

---

