---
title: "No connectivity, No eth0. Default /interfaces file required?"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by tehowe on 2009-06-23
Hello...

My router died a couple of weeks ago so I waded into the deep dark woods of the OS, machete in hand, no map to guide me. 

I plugged my modem in, found that there's some ancient PPPoe config program, ran that, ignored the warning to backup some file or other, and tried to get a direct connection to the modem running.

Erm. That didn't work. Now that I've a new router, there's no 'Auto eth0' in my Network Connections, either.

Mea culpa.

I've tried editing out the odd new lines in etc/network/interfaces so now it reads (commented lines for 'dsl-provider' entry excluded)

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

However on bootup there's no entry in the Gnome networks interface, and when I try to add one (even typing in the MAC address, I'm learning as I go lol) it doesn't work, and it doesn't stay put.

What have I done? :confused:

This is in Jaunty btw

---

### Post by MaindotC on 2009-06-23
Post the output of:
```

lspci | grep Network
lsusb
lshw -C network
ifconfig

#if you are using a wireless connection
iwconfig
iwlist scan

```

---

### Post by tehowe on 2009-06-23
> **strAlan said:**
> Post the output of:
```

lspci | grep Network
lsusb
lshw -C network
ifconfig

#if you are using a wireless connection
iwconfig
iwlist scan

```

> lspci | grep Network

nothing - tried from a few different directories to make sure

> lsusb

Bus 005 Device 002: ID 046d:c046 Logitech, Inc. RX1000 Laser Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04c1:009d U.S. Robotics (3Com) HomeConnect WebCam [vicam]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

> lshw -C network

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:50:fc:20:a9:80
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.194 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ea:9d:10:38:9a:77
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

> ifconfig

eth0      Link encap:Ethernet  HWaddr 00:50:fc:20:a9:80  
          inet addr:192.168.0.194  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:fcff:fe20:a980/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:670 errors:0 dropped:0 overruns:0 frame:0
          TX packets:148 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:58056 (58.0 KB)  TX bytes:12423 (12.4 KB)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3056 (3.0 KB)  TX bytes:3056 (3.0 KB)

---

### Post by MaindotC on 2009-06-23
> **tehowe said:**
> nothing - tried from a few different directories to make sure

*sigh* newbie please just post the output of lspci and while you're at it read the man page for any command I give you and you'll understand WHY I asked you to post that output.  If you did, then you wouldn't be talking about directories "to make sure" and you'd know what I'm looking for in lspci.

---

### Post by MaindotC on 2009-06-23
This is your wired interface.  How do I know?
> **tehowe said:**
> 
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0

Here's one way I can tell:
> 
       logical name: eth0
       version: 10

You could also match the following MAC address with whatever you read off of your network card:
> 
       serial: 00:50:fc:20:a9:80
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical

Here, it tells us what driver you are using (or in *nix world we call them "modules"). Verify that this module is the one that supports your card: 
> 
broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.194 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes


This is probably a firewire or bluetooth interface:
> 
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ea:9d:10:38:9a:77
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

As you can see, eth0, your wired interface, has been issued an IP address, so something must be giving your interface an address and I would imagine that's an access point, but you claimed you aren't using an access point, so perhaps this address is coming from the internet service provider - which I highly doubt because of the type of address issued but I'll let you explain your setup.  Try using complete sentences too - it really helps us understand how to help you!
> 
eth0      Link encap:Ethernet  HWaddr 00:50:fc:20:a9:80  
          inet addr:192.168.0.194  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:fcff:fe20:a980/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:670 errors:0 dropped:0 overruns:0 frame:0
          TX packets:148 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:58056 (58.0 KB)  TX bytes:12423 (12.4 KB)
          Interrupt:18 Base address:0xa000 


---

### Post by lswb on 2009-06-23
If I understand correctly, you have replaced the defective router. If so, try editing your /etc/network/interfaces file so the only contents are
```

auto lo
iface lo inet loopback

```

Then just try rebooting and see if Network Manager shows a successful connection.

---

### Post by tehowe on 2009-06-24
> **strAlan said:**
> *sigh* newbie please just post the output of lspci and while you're at it read the man page for any command I give you and you'll understand WHY I asked you to post that output.  If you did, then you wouldn't be talking about directories "to make sure" and you'd know what I'm looking for in lspci.

Sorry, by 'nothing', what I meant was nothing, no output, was returned in the terminal... I entered the lspci command and modifiers as requested and the terminal returned with its ordinary prompt - that's all. I'll try to parse some  of that other info tonight, thanks. It *is* odd that there's an IP address, but nothing in Network Connections. Maybe the kernel, bash, however one refers to the text-based *nix layer, knows about the connection, but it's not being passed to Gnome somehow...

> As you can see, eth0, your wired interface, has been issued an IP address, so something must be giving your interface an address and I would imagine that's an access point, but you claimed you aren't using an access point, so perhaps this address is coming from the internet service provider - which I highly doubt because of the type of address issued but I'll let you explain your setup. Try using complete sentences too - it really helps us understand how to help you!The ethernet card is simply hooked into my DLink router, which is connected to a G-Net DSL modem. There's also a notebook on this router, and there are no connectivity issues with it. The other port you noticed is probably the soundcard's firewire interface.

> **lswb said:**
> If I understand correctly, you have replaced the defective router. If so, try editing your /etc/network/interfaces file so the only contents are
```

auto lo
iface lo inet loopback

```Then just try rebooting and see if Network Manager shows a successful connection.

I'll try that as well. Cheers... I know the answer to this can't be 'reinstall Ubuntu' =)

---

### Post by MaindotC on 2009-06-24
> **tehowe said:**
> Sorry, by 'nothing', what I meant was nothing, no output, was returned in the terminal... 

I know - and if you read the man page you could see that you could just use "lscpi" with no flags and find the output that said something about "network".  If you ran "lspci" and had no output at all then you'd be operating on a machine that no one on this forum could support.

Definitely no need to reinstall Ubuntu - this is a simple network issue.  I doubt you need to reboot - I couldn't find it in the "interfaces" man page but I believe you can just run:
```

sudo /etc/init.d/networking restart

```
But even if have rebooted, when you show a connection test connectivity by pinging your access point (which you refer to as a router), another machine on your local network, and something outside your network like google.com.  Let us know the results.

---

### Post by tehowe on 2009-06-28
> **lswb said:**
> 
```

auto lo
iface lo inet loopback

```Then just try rebooting and see if Network Manager shows a successful connection.

And there was much rejoicing! Would have replied sooner but now there's a bad line to the service provider I need to deal with as well. At least we know the PC is back in shape.

 [quote=strAlan]
you could just use "lscpi" with no flags and find the output that said something about "network". If you ran "lspci" and had no output at all then you'd be operating on a machine that no one on this forum could support.

Definitely no need to reinstall Ubuntu - this is a simple network issue. I doubt you need to reboot - I couldn't find it in the "interfaces" man page but I believe you can just run:
 ```

sudo /etc/init.d/networking restart

```But even if have rebooted, when you show a connection test connectivity by pinging your access point (which you refer to as a router), another machine on your local network, and something outside your network like google.com. Let us know the results.[/quote]

Here, for interest's sake, is the lspci output. I think I see how this piped grep thing works now. =D

00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 USB Controller: NEC Corporation USB (rev 43)
02:02.1 USB Controller: NEC Corporation USB (rev 43)
02:02.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
02:04.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
02:04.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
02:04.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port

And for good measure, the ping stats just to make sure everything looks ok...

PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=0.198 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.187 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=0.189 ms

PING google.com (74.125.45.100) 56(84) bytes of data.
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=1 ttl=56 time=76.7 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=2 ttl=56 time=100 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=3 ttl=56 time=49.4 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=4 ttl=56 time=82.8 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=5 ttl=56 time=50.3 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=6 ttl=56 time=59.1 ms
--- google.com ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5006ms
rtt min/avg/max/mdev = 49.425/69.807/100.292/18.519 ms

Thanks for your help!

---

### Post by MaindotC on 2009-06-29
Ok you can ping what appears to be your AP and you have name resolution.  You're good to go!

---

