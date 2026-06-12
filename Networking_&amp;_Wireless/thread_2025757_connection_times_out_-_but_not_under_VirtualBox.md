---
title: "connection times out - but not under VirtualBox"
date: 2012-07-14
forum: Networking &amp; Wireless
---

### Post by rebeltaz on 2012-07-14
Last week, AT&T screwed up my internet by trying to install U-verse. I was lied to about the whole package and the technician couldn't even get half of it installed anyway. I had them cancel that and reinitialize the DSL connection. That has been the biggest hassle ever.

When they finally got the net back up (after a week) all of my other systems see it just fine, but my laptop is so slow that most of the time it times out before the pages ever load.

The weird thing is that I am in Firefox now under VirtualBox on the same machine and it works fine!

I have removed the connections from network-manager and let it find them again, I have removed/reinstalled network-manager, I have removed/reinstalled firefox... I don't know what else to do.

It's not just the internet that is affected, though. The laptop times out while trying to load the webpage interface for the modem/router as well. Like I said, none of my other systems (three ubuntu and one WIndows7) have a problem with this. And it fine on the same machine under VirtualBox. That is what gets me!

Oh, and accessing files on another computer over the local network from this laptop is fine as well...

This also seems to affect command line programs as well - ie. wget

---

### Post by Kirk Schnable on 2012-07-14
Unless AT&T gave you a new DSL router when reestablishing your connection, I doubt very much that this is a router or network problem, since it works under certain circumstances.

This sounds to me like a connectivity problem or a driver problem.  How is this device connecting to your network? (Wired or wireless?)

Kirk

---

### Post by rebeltaz on 2012-07-14
> **Kirk Schnable said:**
> Unless AT&T gave you a new DSL router when reestablishing your connection, I doubt very much that this is a router or network problem, since it works under certain circumstances.

This sounds to me like a connectivity problem or a driver problem.  How is this device connecting to your network? (Wired or wireless?)

Kirk

Yeah... I didn't think so either. This is a wireless connection. Other wireless connections to the same router are ok.

---

### Post by Kirk Schnable on 2012-07-14
> **rebeltaz said:**
> Yeah... I didn't think so either. This is a wireless connection. Other wireless connections to the same router are ok.

Can you give me the output of:
```
ifconfig
```

```
iwconfig
```

If there are any signal strength problems or packets dropping those outputs will show them.

Kirk

---

### Post by rebeltaz on 2012-07-14
> **Kirk Schnable said:**
> Can you give me the output of:

```

derek@eMachines:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:c8:e5:90  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:580 (580.0 B)  TX bytes:580 (580.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:23:4d:8e:69:4d  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:4dff:fe8e:694d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5159855 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8190426 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1215634240 (1.2 GB)  TX bytes:2740743517 (2.7 GB)

```

```

derek@eMachines:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"home_server"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 08:86:3B:31:10:D6   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by Kirk Schnable on 2012-07-15
It looks like you have an IP, there were no dropped packets on your wireless interface, and your signal strength and signal quality are acceptable. 

When you have difficulty getting to the Internet and your router page, how are your ping times to those IPs?

Kirk

---

### Post by rebeltaz on 2012-07-15
> **Kirk Schnable said:**
> It looks like you have an IP, there were no dropped packets on your wireless interface, and your signal strength and signal quality are acceptable. 

When you have difficulty getting to the Internet and your router page, how are your ping times to those IPs?

Kirk

The ping times themselves are about right. The problem is that either the ping command takes up to a minute to actually respond to the first ping request, or a portion of the packets are lost.

```

derek@eMachines:~$ ping www.google.com -c 10
PING www.l.google.com (74.125.134.104) 56(84) bytes of data.
64 bytes from gg-in-f104.1e100.net (74.125.134.104): icmp_seq=1 ttl=42 time=31.3 ms
64 bytes from gg-in-f104.1e100.net (74.125.134.104): icmp_seq=2 ttl=42 time=32.4 ms
64 bytes from gg-in-f104.1e100.net (74.125.134.104): icmp_seq=3 ttl=42 time=31.6 ms

--- www.l.google.com ping statistics ---
10 packets transmitted, 3 received, 70% packet loss, time 9052ms
rtt min/avg/max/mdev = 31.328/31.822/32.442/0.463 ms

```

```

derek@eMachines:~$ ping www.google.com -c 10
PING www.l.google.com (74.125.130.105) 56(84) bytes of data.
64 bytes from gh-in-f105.1e100.net (74.125.130.105): icmp_seq=1 ttl=42 time=31.6 ms
64 bytes from gh-in-f105.1e100.net (74.125.130.105): icmp_seq=2 ttl=42 time=31.3 ms
64 bytes from gh-in-f105.1e100.net (74.125.130.105): icmp_seq=3 ttl=42 time=32.0 ms
64 bytes from gh-in-f105.1e100.net (74.125.130.105): icmp_seq=5 ttl=42 time=31.6 ms
64 bytes from gh-in-f105.1e100.net (74.125.130.105): icmp_seq=7 ttl=42 time=31.8 ms
64 bytes from gh-in-f105.1e100.net (74.125.130.105): icmp_seq=9 ttl=42 time=34.4 ms
64 bytes from gh-in-f105.1e100.net (74.125.130.105): icmp_seq=10 ttl=42 time=31.6 ms

--- www.l.google.com ping statistics ---
10 packets transmitted, 7 received, 30% packet loss, time 9030ms
rtt min/avg/max/mdev = 31.340/32.098/34.493/1.011 ms

```

```

derek@eMachines:~$ ping www.google.com -c 10
PING www.l.google.com (74.125.137.99) 56(84) bytes of data.
64 bytes from yh-in-f99.1e100.net (74.125.137.99): icmp_seq=1 ttl=42 time=30.7 ms
64 bytes from yh-in-f99.1e100.net (74.125.137.99): icmp_seq=2 ttl=42 time=31.4 ms
64 bytes from yh-in-f99.1e100.net (74.125.137.99): icmp_seq=3 ttl=42 time=30.7 ms
64 bytes from yh-in-f99.1e100.net (74.125.137.99): icmp_seq=4 ttl=42 time=31.0 ms
64 bytes from yh-in-f99.1e100.net (74.125.137.99): icmp_seq=5 ttl=42 time=31.8 ms
64 bytes from yh-in-f99.1e100.net (74.125.137.99): icmp_seq=6 ttl=42 time=32.5 ms
64 bytes from yh-in-f99.1e100.net (74.125.137.99): icmp_seq=7 ttl=42 time=31.4 ms
64 bytes from yh-in-f99.1e100.net (74.125.137.99): icmp_seq=8 ttl=42 time=32.3 ms
64 bytes from yh-in-f99.1e100.net (74.125.137.99): icmp_seq=9 ttl=42 time=30.3 ms
64 bytes from yh-in-f99.1e100.net (74.125.137.99): icmp_seq=10 ttl=42 time=30.7 ms

--- www.l.google.com ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9013ms
rtt min/avg/max/mdev = 30.396/31.346/32.564/0.712 ms

```

```

derek@eMachines:~$ ping 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
64 bytes from 192.168.1.254: icmp_seq=6 ttl=255 time=0.931 ms
64 bytes from 192.168.1.254: icmp_seq=8 ttl=255 time=0.929 ms
64 bytes from 192.168.1.254: icmp_seq=10 ttl=255 time=1.02 ms
64 bytes from 192.168.1.254: icmp_seq=13 ttl=255 time=0.879 ms
64 bytes from 192.168.1.254: icmp_seq=14 ttl=255 time=0.913 ms
64 bytes from 192.168.1.254: icmp_seq=15 ttl=255 time=0.889 ms
64 bytes from 192.168.1.254: icmp_seq=16 ttl=255 time=0.885 ms
^C
--- 192.168.1.254 ping statistics ---
16 packets transmitted, 7 received, 56% packet loss, time 15090ms
rtt min/avg/max/mdev = 0.879/0.921/1.023/0.051 ms

```

```

derek@eMachines:~$ ping 192.168.1.254 -c 10
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
64 bytes from 192.168.1.254: icmp_seq=1 ttl=255 time=0.970 ms
64 bytes from 192.168.1.254: icmp_seq=2 ttl=255 time=0.873 ms
64 bytes from 192.168.1.254: icmp_seq=3 ttl=255 time=0.917 ms
64 bytes from 192.168.1.254: icmp_seq=4 ttl=255 time=0.893 ms
64 bytes from 192.168.1.254: icmp_seq=5 ttl=255 time=0.875 ms
64 bytes from 192.168.1.254: icmp_seq=6 ttl=255 time=0.861 ms
64 bytes from 192.168.1.254: icmp_seq=7 ttl=255 time=0.850 ms
64 bytes from 192.168.1.254: icmp_seq=8 ttl=255 time=1.14 ms
64 bytes from 192.168.1.254: icmp_seq=9 ttl=255 time=0.858 ms
64 bytes from 192.168.1.254: icmp_seq=10 ttl=255 time=1.09 ms

--- 192.168.1.254 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9001ms
rtt min/avg/max/mdev = 0.850/0.933/1.140/0.104 ms

```

---

### Post by Kirk Schnable on 2012-07-15
The ping times look OK but you have tons of packet loss. 

Could you keep an eye on your iwconfig while this problem is happening? Look for drops in signal strength and quality. 

```
watch iwconfig
```

Kirk

---

### Post by rebeltaz on 2012-07-15
> **Kirk Schnable said:**
> The ping times look OK but you have tons of packet loss. 

Could you keep an eye on your iwconfig while this problem is happening? Look for drops in signal strength and quality. 

```
watch iwconfig
```

Kirk

Signal strength and quality look ok. It doesn't vary much from this - maybe point or two either way.

```

derek@eMachines:~$ ping www.google.com
PING www.l.google.com (74.125.137.99) 56(84) bytes of data.
64 bytes from yh-in-f99.1e100.net (74.125.137.99): icmp_seq=1 ttl=42 time=30.5 ms
64 bytes from yh-in-f99.1e100.net (74.125.137.99): icmp_seq=2 ttl=42 time=31.3 ms
64 bytes from yh-in-f99.1e100.net (74.125.137.99): icmp_seq=3 ttl=42 time=30.6 ms
64 bytes from yh-in-f99.1e100.net (74.125.137.99): icmp_seq=4 ttl=42 time=32.5 ms
64 bytes from yh-in-f99.1e100.net (74.125.137.99): icmp_seq=5 ttl=42 time=32.6 ms
^C
--- www.l.google.com ping statistics ---
31 packets transmitted, 5 received, 83% packet loss, time 30165ms
rtt min/avg/max/mdev = 30.539/31.546/32.693/0.950 ms

```

```

wlan0     IEEE 802.11bg  ESSID:"home_server"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 08:86:3B:31:10:D6   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by Kirk Schnable on 2012-07-15
> **rebeltaz said:**
> Signal strength and quality look ok. It doesn't vary much from this - maybe point or two either way.

```

derek@eMachines:~$ ping www.google.com
PING www.l.google.com (74.125.137.99) 56(84) bytes of data.
64 bytes from yh-in-f99.1e100.net (74.125.137.99): icmp_seq=1 ttl=42 time=30.5 ms
64 bytes from yh-in-f99.1e100.net (74.125.137.99): icmp_seq=2 ttl=42 time=31.3 ms
64 bytes from yh-in-f99.1e100.net (74.125.137.99): icmp_seq=3 ttl=42 time=30.6 ms
64 bytes from yh-in-f99.1e100.net (74.125.137.99): icmp_seq=4 ttl=42 time=32.5 ms
64 bytes from yh-in-f99.1e100.net (74.125.137.99): icmp_seq=5 ttl=42 time=32.6 ms
^C
--- www.l.google.com ping statistics ---
31 packets transmitted, 5 received, 83% packet loss, time 30165ms
rtt min/avg/max/mdev = 30.539/31.546/32.693/0.950 ms

```

```

wlan0     IEEE 802.11bg  ESSID:"home_server"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 08:86:3B:31:10:D6   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Hmm, -59dBm is well within acceptable ranges for WiFi connections, and I'd consider a quality of 51/70 to be acceptable too.

I'm not sure I have an explanation for your problem yet.  Are you certain that you haven't done any software updates on your Ubuntu machine since AT&T was there working on your connection?  This seems like it could be a driver issue with your wireless card to me, but if you haven't updated it lately, there's not much reasson for it to break like this.

I know you said other wireless clients are working fine, but it might be worthwhile to run continuous pings side-by-side and see if you can find any pattern of packet loss on both clients.  Some devices and protocols handle dropped packets better than others.

There's something else that this looks like to me.  Wireless is a token-ring style topology, with the AP doing a certain interval of polling.  This could happen due to incorrect polling taking place.  I've seen issues like this in wireless point to multipoint links such as Motorola Canopy networks, when the GPS sync module goes bad and the device can't do accurate timing anymore.  Obviously it is different with WiFi, but I suppose it's possible to have a problem like that on WiFi.  When there's a polling problem on a Canopy network, the problem can sometimes be bandaged by pushing tons of data through the connection, to give your client higher polling priority.

^ Long story short.  Try downloading a large file, maybe a Ubuntu ISO, and see if the packet loss improves while the connection is pushing a lot of data.  

Kirk

---

### Post by rebeltaz on 2012-07-15
> **Kirk Schnable said:**
> Hmm, -59dBm is well within acceptable ranges for WiFi connections, and I'd consider a quality of 51/70 to be acceptable too.

I'm not sure I have an explanation for your problem yet.  Are you certain that you haven't done any software updates on your Ubuntu machine since AT&T was there working on your connection?  This seems like it could be a driver issue with your wireless card to me, but if you haven't updated it lately, there's not much reasson for it to break like this.

I know you said other wireless clients are working fine, but it might be worthwhile to run continuous pings side-by-side and see if you can find any pattern of packet loss on both clients.  Some devices and protocols handle dropped packets better than others.

There's something else that this looks like to me.  Wireless is a token-ring style topology, with the AP doing a certain interval of polling.  This could happen due to incorrect polling taking place.  I've seen issues like this in wireless point to multipoint links such as Motorola Canopy networks, when the GPS sync module goes bad and the device can't do accurate timing anymore.  Obviously it is different with WiFi, but I suppose it's possible to have a problem like that on WiFi.  When there's a polling problem on a Canopy network, the problem can sometimes be bandaged by pushing tons of data through the connection, to give your client higher polling priority.

^ Long story short.  Try downloading a large file, maybe a Ubuntu ISO, and see if the packet loss improves while the connection is pushing a lot of data.  

Kirk

I actually did download the Ubuntu 10.04 ISO last night in case I had to reinstall this system. I tried once through Firefox/Ubuntu, but it kept dropping the download speed to a point where it reported that it was going to take over two days to finish. I downloaded the same file through Firefox/WindowsXP in VirtualBox on the same machine and it finished in under 30 minutes. 

I have done the side-by-side ping tests against anther laptop running Windows 7 over the same wireless connection and there is absolutely no packet loss on that computer.

And I haven't updated any files since I didn't have a network connection. Update Manager did try to update IceTea after I got the connection back, but what with the timeouts and lost packets, the update was unable to complete. 

I'm telling you... when I have problems - they're doozies!

---

### Post by Kirk Schnable on 2012-07-15
Can you give me the output of:
```
lspci -v
```

I'd like to see if there might be driver related issues.

Kirk

---

### Post by rebeltaz on 2012-07-15
> **Kirk Schnable said:**
> Can you give me the output of:
```
lspci -v
```

I'd like to see if there might be driver related issues.

Kirk

```

derek@eMachines:~$ sudo lspci -v
[sudo] password for derek: 
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Gateway 2000 Device 016d
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Gateway 2000 Device 016d
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Memory at 90000000 (64-bit, non-prefetchable) [size=4M]
	Memory at 80000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 5110 [size=8]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [d0] Power Management version 3
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Gateway 2000 Device 016d
	Flags: bus master, fast devsel, latency 0
	Memory at 93500000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: [d0] Power Management version 3

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Gateway 2000 Device 016d
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 50e0 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Gateway 2000 Device 016d
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 50c0 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Gateway 2000 Device 016d
	Flags: bus master, medium devsel, latency 0, IRQ 21
	Memory at 96705c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCIe advanced features <?>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Gateway 2000 Device 016d
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at 96700000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: 95700000-966fffff
	Prefetchable memory behind bridge: 0000000090400000-00000000913fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Gateway 2000 Device 016d
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: 94600000-956fffff
	Prefetchable memory behind bridge: 0000000091400000-00000000923fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Gateway 2000 Device 016d
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00001000-00002fff
	Memory behind bridge: 93600000-945fffff
	Prefetchable memory behind bridge: 0000000092400000-00000000934fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Gateway 2000 Device 016d
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Gateway 2000 Device 016d
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 50a0 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Gateway 2000 Device 016d
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 5080 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Gateway 2000 Device 016d
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 5060 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Subsystem: Gateway 2000 Device 016d
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 5040 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Gateway 2000 Device 016d
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at 96705800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCIe advanced features <?>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=32
	Capabilities: [50] Subsystem: Gateway 2000 Device 016d

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: Gateway 2000 Device 016d
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Gateway 2000 Device 016d
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 28
	I/O ports at 5108 [size=8]
	I/O ports at 511c [size=4]
	I/O ports at 5100 [size=8]
	I/O ports at 5118 [size=4]
	I/O ports at 5020 [size=32]
	Memory at 96705000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/4 Enable+
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA <?>
	Capabilities: [b0] PCIe advanced features <?>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: Gateway 2000 Device 016d
	Flags: medium devsel, IRQ 11
	Memory at 96706000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 5000 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
	Subsystem: Gateway 2000 Device 016d
	Flags: fast devsel, IRQ 11
	Memory at 96704000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: [50] Power Management version 3

04:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
	Subsystem: AMBIT Microsystem Corp. Device 0428
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at 94600000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [60] Express Legacy Endpoint, MSI 00
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Kernel driver in use: ath5k
	Kernel modules: ath5k

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Gateway 2000 Device 016d
	Flags: bus master, fast devsel, latency 0, IRQ 27
	I/O ports at 1000 [size=256]
	Memory at 92410000 (64-bit, prefetchable) [size=4K]
	Memory at 92400000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at 92420000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Mask- TabSize=2
	Capabilities: [d0] Vital Product Data <?>
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
	Kernel driver in use: r8169
	Kernel modules: r8169


```

---

### Post by Kirk Schnable on 2012-07-15
Alright, it looks like you're using [B]ath5k[/CODE] kernel module for your wireless.

Can you get me:
```
modinfo ath5k
```

And

```
uname -r
```

I'm still puzzled as to why it works in VirtualBox, as that should still go through the Ubuntu driver to get out to the WiFi.  But let's look at your module version and go from there.

Kirk

---

### Post by rebeltaz on 2012-07-15
> **Kirk Schnable said:**
> Alright, it looks like you're using [B]ath5k[/CODE] kernel module for your wireless.

Can you get me:
```
modinfo ath5k
```

And

```
uname -r
```

I'm still puzzled as to why it works in VirtualBox, as that should still go through the Ubuntu driver to get out to the WiFi.  But let's look at your module version and go from there.

Kirk

```

derek@eMachines:~$ modinfo ath5k
filename:       /lib/modules/2.6.32-41-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
version:        0.6.0 (EXPERIMENTAL)
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     E4844FBE7F1B69B18941233
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000014sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000011sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000207sv*sd*bc*sc*i*
depends:        mac80211,led-class,cfg80211,ath
vermagic:       2.6.32-41-generic SMP mod_unload modversions 586 
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           all_channels:Expose all channels the device can use. (bool)

```

```

derek@eMachines:~$ uname -r
2.6.32-41-generic

```

The fact that it works under VirtualBox is confusing me as well. I assumed that it still relied on the native linux connection for access.

---

### Post by Kirk Schnable on 2012-07-15
Check this information out, you might find something of use here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

Also, would you be willing to try a 12.04 Live CD and see if the issue is fixed on the new kernel?  That might give us a point of reference in regard of what to do next.

Kirk

---

### Post by rebeltaz on 2012-07-15
> **Kirk Schnable said:**
> Check this information out, you might find something of use here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

Also, would you be willing to try a 12.04 Live CD and see if the issue is fixed on the new kernel?  That might give us a point of reference in regard of what to do next.

Kirk

I tried the suggestions on the link you provided, but they didn't help. 

Since I already had the image for the 10.04 (and I really don't like the new interface of 11+) I booted with that. I am using it right now to type this and it is the fastest I have ever seen!

I thought maybe running the same commands now (under the live disc) might help?

```

ubuntu@ubuntu:~$ sudo lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Gateway 2000 Device 016d
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Gateway 2000 Device 016d
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Memory at 90000000 (64-bit, non-prefetchable) [size=4M]
	Memory at 80000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 5110 [size=8]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [d0] Power Management version 3
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Gateway 2000 Device 016d
	Flags: bus master, fast devsel, latency 0
	Memory at 93500000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: [d0] Power Management version 3

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Gateway 2000 Device 016d
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 50e0 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Gateway 2000 Device 016d
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 50c0 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Gateway 2000 Device 016d
	Flags: bus master, medium devsel, latency 0, IRQ 21
	Memory at 96705c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCIe advanced features <?>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Gateway 2000 Device 016d
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at 96700000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: 95700000-966fffff
	Prefetchable memory behind bridge: 0000000090400000-00000000913fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Gateway 2000 Device 016d
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: 94600000-956fffff
	Prefetchable memory behind bridge: 0000000091400000-00000000923fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Gateway 2000 Device 016d
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00001000-00002fff
	Memory behind bridge: 93600000-945fffff
	Prefetchable memory behind bridge: 0000000092400000-00000000934fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Gateway 2000 Device 016d
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Gateway 2000 Device 016d
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 50a0 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Gateway 2000 Device 016d
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 5080 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Gateway 2000 Device 016d
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 5060 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Subsystem: Gateway 2000 Device 016d
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 5040 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Gateway 2000 Device 016d
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at 96705800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCIe advanced features <?>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=32
	Capabilities: [50] Subsystem: Gateway 2000 Device 016d

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: Gateway 2000 Device 016d
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Gateway 2000 Device 016d
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 28
	I/O ports at 5108 [size=8]
	I/O ports at 511c [size=4]
	I/O ports at 5100 [size=8]
	I/O ports at 5118 [size=4]
	I/O ports at 5020 [size=32]
	Memory at 96705000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/4 Enable+
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA <?>
	Capabilities: [b0] PCIe advanced features <?>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: Gateway 2000 Device 016d
	Flags: medium devsel, IRQ 11
	Memory at 96706000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 5000 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
	Subsystem: Gateway 2000 Device 016d
	Flags: fast devsel, IRQ 11
	Memory at 96704000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: [50] Power Management version 3

04:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
	Subsystem: AMBIT Microsystem Corp. Device 0428
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at 94600000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [60] Express Legacy Endpoint, MSI 00
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Kernel driver in use: ath5k
	Kernel modules: ath5k

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Gateway 2000 Device 016d
	Flags: bus master, fast devsel, latency 0, IRQ 27
	I/O ports at 1000 [size=256]
	Memory at 92410000 (64-bit, prefetchable) [size=4K]
	Memory at 92400000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at 92420000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Mask- TabSize=2
	Capabilities: [d0] Vital Product Data <?>
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
	Kernel driver in use: r8169
	Kernel modules: r8169

```

```

ubuntu@ubuntu:~$ modinfo ath5k
filename:       /lib/modules/2.6.32-38-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
version:        0.6.0 (EXPERIMENTAL)
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     E4844FBE7F1B69B18941233
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000014sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000011sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000207sv*sd*bc*sc*i*
depends:        mac80211,led-class,cfg80211,ath
vermagic:       2.6.32-38-generic SMP mod_unload modversions 586 
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           all_channels:Expose all channels the device can use. (bool)

```

```

ubuntu@ubuntu:~$ uname -r
2.6.32-38-generic

```

---

### Post by rebeltaz on 2012-07-18
So... I think I have this fixed. Let me start by saying that I have a Belkin N150 router set up as an Access Point for the Motorola Netopia DSL modem/router. When the u-verse "technician" came out to install u-verse, **absolutely nothing** was changed in either the Netopia or the Belkin router configurations. The "technician" did connect the set-top TV box to the Belkin though, which is, somehow, where all my troubles began.

Since one of my Roku devices was also having connections issues, just for the heck of it, I did a factory reset on the Belkin router and reconfigured it as an access point - just like it was. 

As soon as I did that, this laptop has a steady connection, little to no dropped packets and a speedy response time. 

I do not know _what_ connecting the u-verse box to the Belkin did, but whatever it did, it screwed up **something**!

---

### Post by rebeltaz on 2012-07-23
In case anyone is curious about my trials and tribulations at the hands of AT&T U-Verse these past weeks, you can read my review/diatribe here:

[http://www.robotsandcomputers.com/phpBB3/viewtopic.php?f=4&t=419](http://www.robotsandcomputers.com/phpBB3/viewtopic.php?f=4&t=419)

---

