---
title: "wired connection will not connect (11.10)"
date: 2011-11-12
forum: Networking &amp; Wireless
---

### Post by Hunnter on 2011-11-12
Hello
 

I am very noobish when it comes to linuxy things so I would be very appreciative if anyone could help me  :)
 
I'm trying to connect to the internet with a wired connection. My PC is connected through an ethernet cable to a Linksys Wireless G Router WRT54G (currently acting as a switch) which is in turn connected (also via ethernet cable) to a Netgear DG834G router which is then connected to the outside world.
 
This setup is working on the same PC when I boot into Windows XP (64 bit).
 
I'm currently running Ubuntu off of a Live CD but I was under the impression that that doesn't matter. I was going to try to actually install Ubuntu but it said "For best results make sure you are connected to the internet" so I thought I'ld try getting the internet working first if possiible.
 
Here is the output of some commonly requested / useful sounding commands:
**ifConfig -a**
```
 
ubuntu@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1a:92:78:22:95  
          inet6 addr: fe80::21a:92ff:fe78:2295/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1 dropped:0 overruns:0 frame:1
          TX packets:0 errors:0 dropped:193 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:7815 (7.8 KB)
          Interrupt:47
 
eth1      Link encap:Ethernet  HWaddr 00:1a:92:78:2b:41  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:48 Base address:0xa000
 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:528 errors:0 dropped:0 overruns:0 frame:0
          TX packets:528 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:40600 (40.6 KB)  TX bytes:40600 (40.6 KB)

```
 
**lshw -C network**
```
 
nothing

```
 
**nm-tool**
```
 
ubuntu@ubuntu:~$ nm-tool
 
NetworkManager Tool
 
State: disconnected
 
- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             disconnected
  Default:           no
  HW Address:        00:1A:92:78:22:95
 
  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s
 
  Wired Properties
    Carrier:         on
 
 
- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        00:1A:92:78:2B:41
 
  Capabilities:
    Carrier Detect:  yes
 
  Wired Properties
    Carrier:         off

```
 
**grep eth0**
```
 
ubuntu@ubuntu:~$ dmesg | grep eth0
[    3.880673] forcedeth 0000:00:11.0: ifname eth0, PHY OUI 0x5043 @ 19, addr 00:1a:92:78:22:95
[   74.944006] eth0: no IPv6 routers present
[ 2380.168006] eth0: no IPv6 routers present
[ 2403.376008] eth0: no IPv6 routers present
[FONT=Liberation Serif][ 2426.560005] eth0: no IPv6 routers present[/FONT]
```
 

I have been trying to use Ubuntu for a few years now but every time I try I haven't been able to connect to the internet and after a few days of frustrating Googling I got disheartened and went back to using Windows for a year before deciding to try again :( but this time I'm determined to get Ubuntu working!
 
thankies,
Carl

---

### Post by praseodym on 2011-11-12
Hi,

the module (driver) forcedeth often needs additional parameters:

```
echo "options forcedeth msi=0 msix=0" | sudo tee /etc/modprobe.d/forcedeth.conf
```
This is one line, copy/paste it. Remove your current wired profile and reboot after that. Checks:

```
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
```
Checked the cable?

---

### Post by Hunnter on 2011-11-12
Hi Praseodym,

I tried those things you suggested but I still can't connect :(

Here is the output:

```
ubuntu@ubuntu:~$ ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:1a:92:78:22:95   
          inet6 addr: fe80::21a:92ff:fe78:2295/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4123 (4.1 KB) 
          Interrupt:47 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:1a:92:78:2b:41   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:48 Base address:0xa000 

lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:3600 (3.6 KB)  TX bytes:3600 (3.6 KB) 

```

```

ubuntu@ubuntu:~$ cat /etc/network/interfaces 
auto lo 
iface lo inet loopback 
```

```
ubuntu@ubuntu:~$ cat /etc/resolv.conf 
```

---

### Post by praseodym on 2011-11-13
Right click on the NetworkManager->Edit connections, choose your wired one->Edit

In "IPv4-settings" choose "Automatic (DHCP), addresses only" in the pull-down menu and add

```
8.8.8.8,8.8.4.4
```
in the field "DNS-server". Then reconnect

---

### Post by Hunnter on 2011-11-13
Hello,

I entered those details but still no luck,

here is the screenshot of the IPv4 dialogue window after making the changes

[IMG]http://desmond.imageshack.us/Himg718/scaled.php?server=718&filename=wiredconnectiondialogue.png&res=medium[/IMG]

---

### Post by praseodym on 2011-11-13
IPv6-settings are on "ignore"?

---

### Post by superdad0128 on 2011-11-13
computer says "device not ready-firmware missing" under wireless connections. help?

---

### Post by sum1nil on 2011-11-13
I just had that same problem today after a fresh install.

I used the command 'lspci -v' and discovered my wireless adapter was: 
> 02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

I did a search in synaptic for 'BCM4312' and it displayed a package for the firmware. The wireless came on-line after installing the package and rebooting.

What is the network controller stated when you issue 'lspci -v'?

---

### Post by sum1nil on 2011-11-14
If resolv.conf is empty that could be a problem since a name server should be listed.
Add the name servers of your isp into resolv.conf like:
 
> nameserver 192.168.1.254

---

### Post by vidtek on 2011-11-14
> **Hunnter said:**
> Hello
 

I am very noobish when it comes to linuxy things so I would be very appreciative if anyone could help me  :)
 
I'm trying to connect to the internet with a wired connection. My PC is connected through an ethernet cable to a Linksys Wireless G Router WRT54G (currently acting as a switch) which is in turn connected (also via ethernet cable) to a Netgear DG834G router which is then connected to the outside world.
 
This setup is working on the same PC when I boot into Windows XP (64 bit).
 
I'm currently running Ubuntu off of a Live CD but I was under the impression that that doesn't matter. I was going to try to actually install Ubuntu but it said "For best results make sure you are connected to the internet" so I thought I'ld try getting the internet working first if possiible.
 
Here is the output of some commonly requested / useful sounding commands:
**ifConfig -a**
```
 
ubuntu@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1a:92:78:22:95  
          inet6 addr: fe80::21a:92ff:fe78:2295/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1 dropped:0 overruns:0 frame:1
          TX packets:0 errors:0 dropped:193 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:7815 (7.8 KB)
          Interrupt:47
 
eth1      Link encap:Ethernet  HWaddr 00:1a:92:78:2b:41  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:48 Base address:0xa000
 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:528 errors:0 dropped:0 overruns:0 frame:0
          TX packets:528 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:40600 (40.6 KB)  TX bytes:40600 (40.6 KB)

```
 
**lshw -C network**
```
 
nothing

```
 
**nm-tool**
```
 
ubuntu@ubuntu:~$ nm-tool
 
NetworkManager Tool
 
State: disconnected
 
- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             disconnected
  Default:           no
  HW Address:        00:1A:92:78:22:95
 
  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s
 
  Wired Properties
    Carrier:         on
 
 
- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        00:1A:92:78:2B:41
 
  Capabilities:
    Carrier Detect:  yes
 
  Wired Properties
    Carrier:         off

```
 
**grep eth0**
```
 
ubuntu@ubuntu:~$ dmesg | grep eth0
[    3.880673] forcedeth 0000:00:11.0: ifname eth0, PHY OUI 0x5043 @ 19, addr 00:1a:92:78:22:95
[   74.944006] eth0: no IPv6 routers present
[ 2380.168006] eth0: no IPv6 routers present
[ 2403.376008] eth0: no IPv6 routers present
[FONT=Liberation Serif][ 2426.560005] eth0: no IPv6 routers present[/FONT]
```
 

I have been trying to use Ubuntu for a few years now but every time I try I haven't been able to connect to the internet and after a few days of frustrating Googling I got disheartened and went back to using Windows for a year before deciding to try again :( but this time I'm determined to get Ubuntu working!
 
thankies,
Carl

Carl-

You haven't said what adapter you are using.
I had a similar problem with new kernels where the realtek drivers are stuffed, they use the RTL8169 driver instead of the RTL8168.  If you use a lateish motherboard with Z68 chipset this is probably the problem, Gigabyte and Asus motherboards use this chipset.

Best regards, Tony.

Tony.

---

### Post by Hunnter on 2011-11-14
Wow, thanks for all the responses :)

> **praseodym said:**
> IPv6-settings are on "ignore"?
I don't know what this means, the tick box labelled "Require IPv6 addressing for this connection to complete" is un-ticked

> **sum1nil said:**
> If resolv.conf is empty that could be a problem since a name server should be listed.
Add the name servers of your isp into resolv.conf like:
hello, I'm sorry but I'm really new to linux. How do I check resolv.conf and add a name servers?

> **vidtek said:**
> Carl-

You haven't said what adapter you are using.
I had a similar problem with new kernels where the realtek drivers are  stuffed, they use the RTL8169 driver instead of the RTL8168.  If you use  a lateish motherboard with Z68 chipset this is probably the problem,  Gigabyte and Asus motherboards use this chipset.

Best regards, Tony.

Tony.
Hi Tony, I'm not sure what model my mother board is but I think the make is Asus. I will look in to this further and respond :)

---

### Post by SebastianInHiding on 2012-07-09
> **Hunnter said:**
> Hello
 

I am very noobish when it comes to linuxy things so I would be very appreciative if anyone could help me  :)
 
I'm trying to connect to the internet with a wired connection. My PC is connected through an ethernet cable to a Linksys Wireless G Router WRT54G (currently acting as a switch) which is in turn connected (also via ethernet cable) to a Netgear DG834G router which is then connected to the outside world.
 
This setup is working on the same PC when I boot into Windows XP (64 bit).
 
I'm currently running Ubuntu off of a Live CD but I was under the impression that that doesn't matter. I was going to try to actually install Ubuntu but it said "For best results make sure you are connected to the internet" so I thought I'ld try getting the internet working first if possiible.
 
Here is the output of some commonly requested / useful sounding commands:
**ifConfig -a**
```
 
ubuntu@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1a:92:78:22:95  
          inet6 addr: fe80::21a:92ff:fe78:2295/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1 dropped:0 overruns:0 frame:1
          TX packets:0 errors:0 dropped:193 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:7815 (7.8 KB)
          Interrupt:47
 
eth1      Link encap:Ethernet  HWaddr 00:1a:92:78:2b:41  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:48 Base address:0xa000
 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:528 errors:0 dropped:0 overruns:0 frame:0
          TX packets:528 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:40600 (40.6 KB)  TX bytes:40600 (40.6 KB)

```**lshw -C network**
```
 
nothing

```**nm-tool**
```
 
ubuntu@ubuntu:~$ nm-tool
 
NetworkManager Tool
 
State: disconnected
 
- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             disconnected
  Default:           no
  HW Address:        00:1A:92:78:22:95
 
  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s
 
  Wired Properties
    Carrier:         on
 
 
- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        00:1A:92:78:2B:41
 
  Capabilities:
    Carrier Detect:  yes
 
  Wired Properties
    Carrier:         off

```**grep eth0**
```
 
ubuntu@ubuntu:~$ dmesg | grep eth0
[    3.880673] forcedeth 0000:00:11.0: ifname eth0, PHY OUI 0x5043 @ 19, addr 00:1a:92:78:22:95
[   74.944006] eth0: no IPv6 routers present
[ 2380.168006] eth0: no IPv6 routers present
[ 2403.376008] eth0: no IPv6 routers present
[FONT=Liberation Serif][ 2426.560005] eth0: no IPv6 routers present[/FONT]
```I have been trying to use Ubuntu for a few years now but every time I try I haven't been able to connect to the internet and after a few days of frustrating Googling I got disheartened and went back to using Windows for a year before deciding to try again :( but this time I'm determined to get Ubuntu working!
 
thankies,
Carl

Carl, I had the same frustrating problem and my solution was simple. I just went into the edit connections and deleted my wired connection. afterwards I plugged back in my 
ethernet and clicked the auto ethernet  and it worked instantly. I know all machines are different but hopefully this works for you

---

