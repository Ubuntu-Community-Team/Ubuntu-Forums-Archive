---
title: "i can't log onto web"
date: 2010-02-06
forum: Networking &amp; Wireless
---

### Post by mo7amed120 on 2010-02-06
[LEFT][SIZE=4]hey
i have just installed ubuntu 9.10 on my machine after the instalation completed yhe internet didn't worked that's also happen when i install windows xp sp3 but i was able to overcome this proplem by editing my lan settings that i have entered my local area connection and then propeties then configure the lan card and then choose advanced then i choose 10base T full dupleux if any one have asoloution please email me at 
[email]mo7amed120@gmail.com[/email]
[/SIZE][/LEFT]

---

### Post by theozzlives on 2010-02-06
Is it wireless, if so you may have to go wired to get the Restricted drivers.

---

### Post by northd_tech on 2010-02-06
Could you boot into Ubuntu and save the results of the following commands into a/some text file(s) when you run them from a terminal mo7?:

```
lspci 

lsmod

uname -a

sudo lshw -C network

ifconfig

iwconfig
```

It might be easiest if you save that/those text files (using Kate or gedit) to a USB drive so that you can access them from Windows to post the results here.

Then the people here can probably steer you toward the right threads for your hardware.

---

### Post by mo7amed120 on 2010-02-06
[SIZE=5]it's in my attachment
[/SIZE]

---

### Post by mo7amed120 on 2010-02-06
> **northd_tech said:**
> Could you boot into Ubuntu and save the results of the following commands into a/some text file(s) when you run them from a terminal mo7?:

```
lspci 

lsmod

uname -a

sudo lshw -C network

ifconfig

iwconfig
```It might be easiest if you save that/those text files (using Kate or gedit) to a USB drive so that you can access them from Windows to post the results here.

Then the people here can probably steer you toward the right threads for your hardware.
it's in my attachment

---

### Post by northd_tech on 2010-02-06
OK- it looks like "lspci" identifies your network card (NIC) as: 
"00:04.0 Ethernet controller: **Silicon Integrated Systems [SiS] SiS900** PCI Fast Ethernet (rev 90)"

It looks like "lsmod" indicates the module is loaded as:
"Module                  Size  **Used by**
**sis900**                 24320  0 
mii                     6400  1 **sis900**"

You are running the following 32 bit kernel: 2.6.24-26-generic

I'll just quote the network stuff directly:

> sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 90
       serial: 00:14:85:78:26:80
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.1.1 latency=64 link=no maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=100MB/s


ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:85:78:26:80  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:85ff:fe78:2680/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          **RX packets:18** errors:0 dropped:0 overruns:0 frame:0
          **TX packets:0** errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          **RX bytes:1080 (1.0 KB)  TX bytes:0 (0.0 B)**
          Interrupt:16 Base address:0xa800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1390 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1390 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:69692 (68.0 KB)  TX bytes:69692 (68.0 KB)


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.I haven't worked with that SiS 900 before under Linux, but it looks like an integrated motherboard-type thing to me (your sound and video also look to be integrated motherboard SiS stuff).

In case you need it for some reason down the road, your video adapter shows as:

"01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"

and the motherboard main bridge as: 
"00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)"

In a quick forum search here for "SiS 900 ethernet" I found this thread that sounds related:

[SOLVED] Network Manager can't find network  
[http://ubuntuforums.org/showthread.php?t=1370526&highlight=SiS+900+ethernet](http://ubuntuforums.org/showthread.php?t=1370526&highlight=SiS+900+ethernet)

You appear to be receiving [Rx] packets (but not transmitting [Tx] them) have you looked at your router/firewall? settings (and maybe tried a different network cable- sometimes the ends get messed up)?

---

### Post by mo7amed120 on 2010-02-06
thnx for all but mine isn't working

---

