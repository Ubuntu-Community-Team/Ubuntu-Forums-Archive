---
title: "network connection but no internet"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by frenchiewhite on 2009-11-05
hi guys...
I am using an eeepc 1000h and just updated ubuntu remix to 9.10.
Since then I still have a network connection (wired and wireless) but no internet connection. Firefox tells me that page can't be loaded (all other browsers,too), mail evolution doesn't work... nothing does.. and I'm practically a noob... :'( please help.

---

### Post by deparvius on 2009-11-05
Do you know how to open a terminal?  If not google it, it will make a valuable troubleshooting tool and a great introduction to the power of unix/linux.

In the terminal, please type the commands

ifconfig

sudo lshw -C network

Which will describe your network interfaces setup.  If you notice any peculiarities, note them here or if you cannot interpret post the result by USB key transfer to a computer with internet.

I'm having many problems with the new Network Manager myself, but at least this is a place to start.

---

### Post by Iowan on 2009-11-05
I'm on a Windows box at the moment, but it seems like the (a) terminal should be accessible via Applications>Accessories>Terminal.

---

### Post by frenchiewhite on 2009-11-06
Actually I'm not as big of a noob as that. But I always had my bf to fix my stuff... now I have to learn to fix my stuff "on my own" :)
thank you guys, and I hope I didn't post too much here:
[B]
ifconfig:

[/B]eth0      Link encap:Ethernet  HWaddr 00:23:54:93:bc:8c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

ra0       Link encap:Ethernet  HWaddr 00:22:43:5d:51:d6  
          inet addr:10.0.1.3  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:43ff:fe5d:51d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:965890 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9760 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:213223379 (213.2 MB)  TX bytes:10231 (10.2 KB)
          Interrupt:19 [B]


sudo lshw -C network:

 [/B]*-network               
       description: Ethernet interface
       product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:23:54:93:bc:8c
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair
       resources: irq:27 memory:fbfc0000-fbffffff ioport:ec00(size=128)
  *-network
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: ra0
       version: 00
       serial: 00:22:43:5d:51:d6
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 ip=10.0.1.3 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:19 memory:fbef0000-fbefffff

---

### Post by Iowan on 2009-11-06
A couple more things to check...
**route -n** - the last line should show your (default) gateway.
*/etc/resolv.conf* should show your DNS nameservers.

---

### Post by frenchiewhite on 2009-11-12
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
192.168.123.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0 
169.254.0.0     0.0.0.0         255.255.0.0        U     0      0        0 eth0 
0.0.0.0    192.168.123.254     0.0.0.0            UG    0      0        0 eth0 
route -n /etc/resolv.conf 
Usage: route [-nNvee] [-FC] [<AF>]           List kernel routing tables 
       route [-v] [-FC] {add|del|flush} ...  Modify routing table for AF. 
 
       route {-h|--help} [<AF>]              Detailed usage syntax for specified AF. 
       route {-V|--version}                  Display version/author and exit. 
 
        -v, --verbose            be verbose 
        -n, --numeric            don't resolve names 
        -e, --extend             display other/more information 
        -F, --fib                display Forwarding Information Base (default) 
        -C, --cache              display routing cache instead of FIB 
 
  <AF>=Use '-A <af>' or '--<af>'; default: inet 
  List of possible address families (which support routing): 
    inet (DARPA Internet) inet6 (IPv6) ax25 (AMPR AX.25)  
    netrom (AMPR NET/ROM) ipx (Novell IPX) ddp (Appletalk DDP)  
    x25 (CCITT X.25)  


and now???

---

### Post by Iowan on 2009-11-12
> **frenchiewhite said:**
> route -n /etc/resolv.conf Sorry, my bad... Try **cat /etc/resolv.conf** or **less /etc/resolv.conf**. 

Interesting... Default gateway is 192.168.123.254 on eth0 - which has no IP address. Wireless (ra0) has an IP address, but no routes.  Now if I knew what to do to fix it...

Which interface *should* be working - are you trying to connect wired or wireless (or would you care - as long as it worked)?

---

### Post by frenchiewhite on 2009-11-13
actually I need both to work. because it's a netbook, it's kinda it's purpose :)

---

### Post by frenchiewhite on 2009-11-13
so if I type in what you told me, first is
# Generated by NetworkManager

and second is the same
but with a blinking [B][End] 
**[FONT=Arial]at the end[/FONT]**
[/B]

---

### Post by Iowan on 2009-11-13
I gave you a couple of options - they should have returned the same information.  The file being (essentially) empty is one reason you're having internet problems.  Short term, you might try putting in [these]("https://store.opendns.com/setup/device/ubuntu/") addresses. If that miraculously fixes everything, we won't need to discover why one interface is active, but the gateway is on the other one.

---

### Post by frenchiewhite on 2009-11-18
it still doesn't work... but I'm still trying. maybe I didn't see a small thing here .

---

### Post by frenchiewhite on 2009-11-19
weirdest thing is that skype works, but other stuff doesnt ?!

---

