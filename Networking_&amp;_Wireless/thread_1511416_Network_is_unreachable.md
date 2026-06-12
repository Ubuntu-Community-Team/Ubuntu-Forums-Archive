---
title: "Network is unreachable"
date: 2010-06-16
forum: Networking &amp; Wireless
---

### Post by kuproverto on 2010-06-16
When I try to ping any IP on my LAN the message Network is unreachable is shown.

On my LAN I have an Ubuntu 9.10 machine, an XP machine and a printer. These are connected to a router then to a cable modem. The Ubuntu machine has a shared directory which is mapped to a drive letter in XP.

A few days ago, the printer was inaccessible from either machine. On the Ubuntu machine, I reinstalled the printer and noticed the IP address had changed. The printer then worked from both machines.

Also, a few days ago, the shared directory on the Ubuntu machine was inaccessible from the XP machine with Disconnected Network Drive being displayed.

Today, the XP machine still can't connect to the shared directory on the Ubuntu machine and the printer is now inaccessible once more. Connection to the Internet is not affected. 

The Ubuntu machine can't access the printer, the Internet or the LAN.

Here's what I've done so far:

Rebooted both computers, the modem, router and printer. No change.

From a Terminal in Ubuntu, run the command sudo dhclient eth0. Results below.

```
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1d:7d:7f:19:27
Sending on   LPF/eth0/00:1d:7d:7f:19:27
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * Reloading /etc/samba/smb.conf smbd only
   ...done.

```


run the command ifconfig -a. Results below.

```
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:7f:19:27  
          inet6 addr: fe80::21d:7dff:fe7f:1927/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:540 (540.0 B)  TX bytes:4572 (4.5 KB)
          Interrupt:27 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:71 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10637 (10.6 KB)  TX bytes:10637 (10.6 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
run the command sudo lshw -C network. Results below

```
 *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:7d:7f:19:27
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:c000(size=256) memory:e5010000-e5010fff(prefetchable) memory:e5000000-e500ffff(prefetchable) memory:e5020000-e502ffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

Run the live CDs for both Ubuntu versions 9.10 and 10.04 then tried to connect to the Internet. No luck.

I've used the Terminal to ping as clicking on the Ping tab in System | Administration | Network Tools closes that tool. Clicking on any of the other tabs doesn't close it.

From the Devices tab in Network Tools with eth0 specified as Network device:

IPv6 has a value for an IP address, Netmask/Prefix and Scope. IPv4 has 0.0.0.0

MTU is 1500


I installed 9.10 when it was released and have had zero problems with it until 10.04 was released. Since then, via the updates I presume, 9.10 has had all kinds of problems most of which I've been able to fix or find a work around for. This one has me stumped though, so any help is appreciated.

---

### Post by jonobr on 2010-06-17
Hello

The first thing I notice from your detailed outline (nice job on that BTW) :p
is that you mention your devices are going to router and then to a cable modem.

Then your output shows that the machine is not getting any responses from a DHCP request and it appears your enet card is not getting an IP address.

If you are connected to a router, then this could be an issue.
Routers do not pass broadcasts such as a DHCP request unless told specifcally to do so. In cisco an IP helper statement would be used to forward bootp and dhcp requests.

If your machine is trying to get an IP address through the router it may be blocked from doing so.

If , as I suspect, you have a switch and not a router, this will take a broadcast recieved and forward to all ports active on the switch.
Typically your DHCP server will respond with an address for your machine.

So a few questions I would have are 
whats providing the IP addresses and doing DHCP?
Have you allowed enough IP addresses and are they being correctly released?
what is the exact device your using at the center?

You mentioned that you want to reinstall the sowftware, however, I am guessing you had a static IP address that worked, and have gone to DHCP and it now doesnt.
Your now thinking you were at fault , but I think your being hard on yourself.


Cheers

---

### Post by CharlesA on 2010-06-17
Passing DHCP requests doesn't matter since the router is (usually) the one assigning IP addresses. I would check the router to see if the DHCP leases are full. I've had a server running in a VM decide to suck up all the available DHCP address pool, all of them were assigned to the same MAC (I don't know how that works.)

First thing to do would be to check the router. :)

---

### Post by kuproverto on 2010-06-17
Thanks for the replies.

I do have a router, it's a motorola. I also have a switch which I use because the router doesn't have enough ports.

I presume the router is providing the IPs. I just plugged all the devices in and everything worked. 

Looking at the router software, in the LAN clients list, only the XP machine is listed. I added the Ubuntu machine as a static IP but it still doesn't work. Also, this new entry for the Ubuntu machine doesn't show up in the list of DHCP clients.

I can't find anywhere showing me any DHCP lease information other than the lease time.

---

### Post by jonobr on 2010-06-17
Hello


When you create a static IP on the ubuntu machine then it wont show up in the DHCPO clients.

With the static IP applied, could you show the result of ifconfig again?

Also, the model number of the motorola would be good to see if there are issues with DHCP address allocation

---

### Post by kuproverto on 2010-06-17
I created the static IP from within the router software.

Here's the ifconfig results again:

```
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:7f:19:27  
          inet6 addr: fe80::21d:7dff:fe7f:1927/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:90 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5400 (5.4 KB)  TX bytes:3546 (3.5 KB)
          Interrupt:27 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```

The router is a motorola VT2442. It's provided by Vonage to be used with my VOIP phone.

---

### Post by jonobr on 2010-06-17
Hello


Yourt Ifconfig shows that the thing is not receiveing an address from your network.

When you say you assigned a static IP in your motorola, Im not sure what this means?

Im guessing [If you look at the manual here]("http://broadband.motorola.com/consumers/products/VT2400/downloads/VT2442_User_Manual_US_UK.pdf") you have the option B type network as shown on page 9.
If thats the case, then im figuring yoiur motorola should get an IP from your dsl, via DHCP.
Unless the ISP has given you an IP address then the motorola should not have a static.

Then you need to figure IP address allocation to your connected machines.
Lan configuration on page 21 shows how you set that up.

You should confirm that you have DHCP server radial button checked and an range of addresses defined to allocate to your machines.
Recommend you check that the defaults havent changed and if they have then let us know what they are

Cheers

---

### Post by kuproverto on 2010-06-17
I assigned a static IP by entering the details into the LAN Clients section of the router software. Page 34 of the manual shows this.
It didn't work so I deleted it again as I'm sure an IP should be assigned dynamically.

I do have the type of network shown on page 9. The only difference is I have a switch attached as well as there aren't enough ports on the motorola router for all the Ethernet cables I need to plug in.

My ISP has not given me a static IP.

I have the Enable DHCP Server radio button checked. A range of addresses is specified.

I'm somewhat puzzled. Why would the DHCP server stop leasing IPs to certain machines on the LAN? Why did the IP of the printer change recently? Is the problem with the router, could it be with Samba or could it be due to an Ubuntu software update? I've noticed other updated features are more 10.04 like than 9.10.

I have an old machine which I'll install 9.10 onto then try to connect to the LAN and Internet.

Also, some more info. From the XP box I can ping the IP of the router but can't ping the IP of either the printer or the Ubuntu machine.

---

### Post by kuproverto on 2010-06-17
Quick update.

My old machine already has a beta version of 10.04 installed. I hooked it up to the network and I can connect to the Internet. An IP was assigned and the machine appeared in the list of DHCP clients on the router software.

So, presumably, this means the problem is located somewhere in my 9.10 machine?

---

### Post by jonobr on 2010-06-17
It does show your problem is not the router.

Is this a different nic? I am wondering if your bic is sending bootp requests but not hearing any back?

---

### Post by kuproverto on 2010-06-17
I've made no hardware changes to any of the machines. Recently the only events to have happened are the usual Ubuntu etc software updates, all of which I install and I looked at 10.04 on my XP box using the live CD.

(I also looked at the live CDs of both 9.10 and 10.04 on the Ubuntu machine but that was after the problems started.)

---

### Post by JKyleOKC on 2010-06-17
I think your problem might be related to the one I describe [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1511394") involving the r8168B chip. Try both lspci and lshw to see if your machine is even recognizing the adapter's presence.

Frequent loss of the connection seems to be a recurrent problem with this hardware, dating back at least to mid-2008, and so far I've not seen any sign of a solution. I had partial success by manually adding the r8169 driver via modprobe, but the connection vanished again some six hours later. The most reliable cure I found in two days of searching was to power the machine down, then physically unplug its power cable and leave it out for at least 15 seconds. Upon restoring power and rebooting, the chip would be recognized and connectivity would return -- but only for a very few minutes!

I'm still running 8.04, but just to test things out I burned a live CD of 10.04 and fired it up; again, the adapter with the 8168B chip wasn't recognized.

I'll follow here and hope you can find a solution!

---

### Post by kuproverto on 2010-06-17
I'd considered the NIC after having read some posts describing loss of connectivity. Tomorrow, I'll install both the cards currently installed in my back-up 10.04 machine. One is a Realtak and the other a 3Com. Both work fine.

---

### Post by kuproverto on 2010-06-19
Another update.

On my spare machine, running 10.04, I did apt-get update and apt-get upgrade, rebooted the machine then connected to the Internet. A few minutes later, Internet connectivity was lost. It came back after another reboot but it seems strange that both machines lost connection after a software update.

I still have to try the spare NICs in the main machine. If that doesn't work I'll have reinstall the OS.

---

### Post by kuproverto on 2010-06-20
Final update.

Installed the 3com card. Didn't solve the problem.

Over the last few days I've spent many hours trying to resolve this issue to no avail.

Tomorrow I'll reinstall and be very careful with my updates in future.

---

