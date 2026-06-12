---
title: "Please help me so that I wont have to reinstall, again!"
date: 2009-10-02
forum: Networking &amp; Wireless
---

### Post by honey toast on 2009-10-02
Hi guys, 

I have an issue with my jaunty install. Yesterday, I was trying to optimize my system by purging "unnecessary" packages. I was reading someones post on how to do this and so I was following the steps. Silly me, I actually autoremoved 'ppp' , becauase the writer said that it was a package that supported dial up. Suddenly, I was unable to connect to the internet. I tried reinstalling ppp from synaptic, but I receieved fetch errors-duh. Since I have an HP 1030nr min, I only use wifi. 
So I reinstalled jaunty. I can connect to the internet. Only now, I think I have issues with my nic. Can someone please tell me what Im looking at? And does it appear to be normal?

ip link show:

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1480 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:24:81:40:bd:8c brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:24:2b:99:b1:80 brd ff:ff:ff:ff:ff:ff
4: pan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN 
    link/ether f2:2a:64:f5:9a:a6 brd ff:ff:ff:ff:ff:ff



WHy do I have all of those fields? Is that too many? Shouldn't I only have 1!?
I'm not inclined yet on how to read all of this stuff. I'm really trying though. I know all the basic terminal cmds :D
Can you please tell me if my system looks ok?



sudo lspci:


00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller


I'm connected to a cable access point, and all of my updates seem so incredibly slow at around 60kb/s!! Something has got to be wrong.
Here is another bit of information.Also whenever I try to update, all of my sessions time out due to 'fetch errors'. Plz help me to restore my system back to normal. Thanks

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:24:81:40:bd:8c  
          inet addr:71.197.206.189  Bcast:71.197.207.255  Mask:255.255.248.0
          inet6 addr: fe80::224:81ff:fe40:bd8c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1480  Metric:1
          RX packets:288431 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20635 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31072747 (31.0 MB)  TX bytes:3531670 (3.5 MB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:24:2b:99:b1:80  
          inet6 addr: fe80::224:2bff:fe99:b180/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

---

### Post by scorp123 on 2009-10-02
> **honey toast said:**
>  Can someone please tell me what Im looking at?  A list of network interfaces inside your system.

> **honey toast said:**
> 1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1480 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:24:81:40:bd:8c brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:24:2b:99:b1:80 brd ff:ff:ff:ff:ff:ff
4: pan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN 
    link/ether f2:2a:64:f5:9a:a6 brd ff:ff:ff:ff:ff:ff

WHy do I have all of those fields? Because you have one loopback interface, one ethernet interface, one wireless interface, and last but not least you seem to have Bluetooth turned on.

Loopback:
[http://en.wikipedia.org/wiki/Loopback#Virtual_network_interface](http://en.wikipedia.org/wiki/Loopback#Virtual_network_interface)

PAN:
[http://en.wikipedia.org/wiki/Personal_Area_Network](http://en.wikipedia.org/wiki/Personal_Area_Network)


> **honey toast said:**
>  Shouldn't I only have 1!?  I'd be worried if I only had one. There is only one scenario where this can happen: All real interfaces are dead (= fried electronics) and only the virtual loopback interface remains. So if you end up only having one network interface ... I'd be worried :D

> **honey toast said:**
>  ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:24:81:40:bd:8c  
          inet addr:**[COLOR="Red"]71.197.206.189[/COLOR]**  Bcast:71.197.207.255  Mask:255.255.248.0  You seem to receive an IP .... But I'm puzzled: Don't you have a router of some sorts? If that info up there is right your system is connected directly to the Internet.

Oh, and very important:

**_[COLOR="#ff0000"]KNOW WHAT YOU DO. ALWAYS.[/COLOR]_** [COLOR="#ff0000"]_Don't follow instructions blindly_ because someone posted something in the forum. Don't follow those instructions if you have no clue what you're doing. OK?[/COLOR]

---

### Post by Iowan on 2009-10-02
> **scorp123 said:**
>  Don't you have a router of some sorts? If that info up there is right your system is connected directly to the Internet.
 Since the question came up - how *are* you connected to internet? My HP laptop uses eth1 for wireless device. Check **lshw -C network** - much the same info you've provided, but limited to network devices. You might also check **route** (last line) to see what you are using for gateway.

---

### Post by honey toast on 2009-10-02
Well, thanks for the reply. I know that I shouldn't accept every bit of optimization advice. I am learning the hard way. I am happy that the both of you were able to investigate my network stats, and judging by your comments, I don't feel worried. 
Also, earlier today when I was having the majority of these problems is when the ubuntu update server was failing, but it I just tried to download something again and it worked rapidly. 


I am connected to the net via Ethernet cable modem. (wired)

---

### Post by doas777 on 2009-10-02
just fyi, the ubuntu repositories have been slow for the last 36 hours or so, primarilly due to karmic beta release. if you are basing your concern on the speed of those downloads, the problem is not on your end of the pipe. 
good luck

---

