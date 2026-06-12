---
title: "Cable wired network not working with Ubuntu"
date: 2009-06-11
forum: Networking &amp; Wireless
---

### Post by Shinka.S on 2009-06-11
I have a desktop computer with 2 hard drives, one with WinXp and the other with Ubuntu 9.04 32bits, my wired internet connection works on WinXp but not on Ubuntu. I have a nForce 4 chipset with a D-Link DFE 538TX network card.

I got help from #ubuntu and I was asked to do; 

[COLOR=Blue]sudo su
updatedb [/COLOR]

And then in the folder with 8139cp.ko; 

[COLOR=Blue]modprobe -i 8139cp[/COLOR]

He said that "if it works you'll need to add it to /etc/modules I think so it will be insmoded every time your system starts" ==> how do I do that ?

Anyway it didn't work and the guy had to go to sleep, I have really no idea what to do next...

The result of [COLOR=Blue]ifconfig[/COLOR]

```
eth0      Link encap:Ethernet  HWaddr 00:22:b0:68:58:26  
          inet6 addr: fe80::222:b0ff:fe68:5826/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by carcar1 on 2009-06-11
Whats your problem plug in your Ethernet cable and it should use dhcp or manually configure your ip and you should be good.  It picks up your card so whats the problem?

---

### Post by Shinka.S on 2009-06-11
Everything is plugged, I'm writing this message from the WinXP partition, but from Ubuntu he tries to get connected and I receive a "No wired connection" message.

I tried to manually configured my IP but with no success. I got my IP/netmask/gateway from WinXP, putted it with gedit /etc/network/interfaces but it doesn't work.

And anyway, my IP isn't always the same, is it even possible to manually set the IP in this situation ?

---

### Post by andersbk on 2009-06-11
> **Shinka.S said:**
> Everything is plugged, I'm writing this message from the WinXP partition, but from Ubuntu he tries to get connected and I receive a "No wired connection" message.

I tried to manually configured my IP but with no success. I got my IP/netmask/gateway from WinXP, putted it with gedit /etc/network/interfaces but it doesn't work.

In a terminal type "lspci" and look for "Ethernet controller".

That will show what the linux kernel "thinks" you have.

Also look at the output of "dmesg". Look for eth0. If that shows the driver loading correctly, then maybe you just don't have dhcp client enabled?

edit: you can use System->Administration->Network tools in gnome to set the eth0 settings accordingly.

.

---

### Post by Shinka.S on 2009-06-11
Thanks for the help andersbk.

The result of [COLOR="Blue"]lspci -v;[/COLOR]

```

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
   Subsystem: ASUSTeK Computer Inc. Device 815a
   Flags: bus master, 66MHz, fast devsel, latency 0
   Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
   Subsystem: ASUSTeK Computer Inc. Device 815a
   Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
   Subsystem: ASUSTeK Computer Inc. Device 815a
   Flags: 66MHz, fast devsel, IRQ 5
   I/O ports at d800 [size=32]
   I/O ports at 4c00 [size=64]
   I/O ports at 4c40 [size=64]
   Capabilities: <access denied>
   Kernel driver in use: nForce2_smbus
   Kernel modules: i2c-nforce2

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10)
   Subsystem: ASUSTeK Computer Inc. Device 815a
   Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
   Memory at d5002000 (32-bit, non-prefetchable) [size=4K]
   Capabilities: <access denied>
   Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) (prog-if 20)
   Subsystem: ASUSTeK Computer Inc. Device 815a
   Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
   Memory at feb00000 (32-bit, non-prefetchable) [size=256]
   Capabilities: <access denied>
   Kernel driver in use: ehci_hcd

00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2) (prog-if 8a [Master SecP PriP])
   Subsystem: ASUSTeK Computer Inc. (Wrong ID) Device 815a
   Flags: bus master, 66MHz, fast devsel, latency 0
   [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
   [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
   [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
   [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
   I/O ports at f000 [size=16]
   Capabilities: <access denied>
   Kernel driver in use: pata_amd

00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
   Subsystem: ASUSTeK Computer Inc. Device 815a
   Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
   I/O ports at 09f0 [size=8]
   I/O ports at 0bf0 [size=4]
   I/O ports at 0970 [size=8]
   I/O ports at 0b70 [size=4]
   I/O ports at d400 [size=16]
   Memory at d5001000 (32-bit, non-prefetchable) [size=4K]
   Capabilities: <access denied>
   Kernel driver in use: sata_nv

00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
   Subsystem: ASUSTeK Computer Inc. Device 815a
   Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
   I/O ports at 09e0 [size=8]
   I/O ports at 0be0 [size=4]
   I/O ports at 0960 [size=8]
   I/O ports at 0b60 [size=4]
   I/O ports at c000 [size=16]
   Memory at d5000000 (32-bit, non-prefetchable) [size=4K]
   Capabilities: <access denied>
   Kernel driver in use: sata_nv

00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) (prog-if 01)
   Flags: bus master, 66MHz, fast devsel, latency 0
   Bus: primary=00, secondary=05, subordinate=05, sec-latency=128
   I/O behind bridge: 0000a000-0000afff
   Memory behind bridge: d3000000-d4ffffff
   Prefetchable memory behind bridge: 68000000-680fffff

00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
   Flags: bus master, fast devsel, latency 0
   Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
   Capabilities: <access denied>
   Kernel driver in use: pcieport-driver
   Kernel modules: shpchp

00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
   Flags: bus master, fast devsel, latency 0
   Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
   Capabilities: <access denied>
   Kernel driver in use: pcieport-driver
   Kernel modules: shpchp

00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
   Flags: bus master, fast devsel, latency 0
   Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
   Capabilities: <access denied>
   Kernel driver in use: pcieport-driver
   Kernel modules: shpchp

00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
   Flags: bus master, fast devsel, latency 0
   Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
   I/O behind bridge: 00009000-00009fff
   Memory behind bridge: d0000000-d2ffffff
   Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
   Capabilities: <access denied>
   Kernel driver in use: pcieport-driver
   Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
   Flags: fast devsel
   Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
   Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
   Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
   Flags: fast devsel
   Kernel driver in use: k8temp
   Kernel modules: k8temp

01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)
   Subsystem: ASUSTeK Computer Inc. Device 8231
   Flags: bus master, fast devsel, latency 0, IRQ 5
   Memory at d0000000 (32-bit, non-prefetchable) [size=16M]
   Memory at c0000000 (64-bit, prefetchable) [size=256M]
   Memory at d1000000 (64-bit, non-prefetchable) [size=16M]
   I/O ports at 9000 [size=128]
   Expansion ROM at d2000000 [disabled] [size=128K]
   Capabilities: <access denied>
   Kernel modules: nvidiafb

05:06.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
   Subsystem: Creative Labs Device 1006
   Flags: bus master, medium devsel, latency 32, IRQ 16
   Kernel modules: snd-ca0106

05:08.0 Ethernet controller: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 86)
   Subsystem: D-Link System Inc Device 1407
   Flags: bus master, stepping, medium devsel, latency 32, IRQ 18
   I/O ports at a400 [size=256]
   Memory at d4000000 (32-bit, non-prefetchable) [size=256]
   Expansion ROM at 68000000 [disabled] [size=64K]
   Capabilities: <access denied>
   Kernel driver in use: via-rhine
   Kernel modules: via-rhine
   I/O ports at a000 [size=32]
   Capabilities: <access denied>
   Kernel driver in use: CA0106
   Kernel modules: snd-ca0106

05:08.0 Ethernet controller: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 86)
   Subsystem: D-Link System Inc Device 1407
   Flags: bus master, stepping, medium devsel, latency 32, IRQ 18
   I/O ports at a400 [size=256]
   Memory at d4000000 (32-bit, non-prefetchable) [size=256]
   Expansion ROM at 68000000 [disabled] [size=64K]
   Capabilities: <access denied>
   Kernel driver in use: via-rhine
   Kernel modules: via-rhine

```

And the result from

[COLOR="blue"]sudo su
gedit /etc/network/interfaces[/COLOR]

```
auto lo
iface lo inet loopback
```

...And;

[COLOR="blue"]dhclient eth0[/COLOR]

```
dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:22:b0:68:58:26
Sending on   LPF/eth0/00:22:b0:68:58:26
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

I tried to manually set my IP (with the help of someone of course I know nothing about networks). I was told to find my IP/Subnetwork/Gateway using my WinXP partition and then;

[COLOR="blue"]sudo su
ifconfig eth0 X.X.X.X
ifconfig eth0 netmask X.X.X.X
ifconfig eth0 broadcast X.X.X.X[/COLOR]

With X.X.X.X being the real values of course. But after a networkd restart I got; 

```

* Reconfiguring network interfaces...
SIOCADDRT: No such process
Failed to bring up eth0.
But I tried another gateway (ending with 1) and I got;

```

```

* Reconfiguring network interfaces...
SIOCDELRT: No such process
grep: /etc/resolv.conf: No such file or directory
before doing NFS mounts]: waiting for interface eth0

```

I want to emphasize that; 

(1) My cable works just fine, I'm on WinXP, on the same computer, and my connection works perfectly.

(2) It's not a problem between Linux and my cable, as I had a laptop computer connected to the same cable connection, and it worked fine, I just plug it and it works !

So it seems to be a problem between linux and my D-Link DFE-538TX network card.

---

### Post by cariboo on 2009-06-11
Is the proper driver install for your nic?

Could you paste the output of:

```
sudo lshw -C network
```

in your next post.

---

### Post by Shinka.S on 2009-06-11
[COLOR="Blue"]sudo lshw -C network[/COLOR]

```
 *-network               
       description: Ethernet interface
       product: VT6105/VT6106S [Rhine-III]
       vendor: VIA Technologies, Inc.
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 86
       serial: 00:22:b0:68:58:26
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2e:11:8f:ae:aa:3f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

### Post by iReboot on 2009-06-11
I have more or less the same problem.

The output of sudo lshw -C network is the same on my computer.

I can bring up eth0 and pan0 on the network tools menu, but I can't see any way to configure them.

---

### Post by superprash2003 on 2009-06-12
post contents of /etc/dhcp3/dhclient.conf file

---

### Post by andersbk on 2009-06-12
Look at your lspci output and your lshw -C network output.

Kernel is telling you that the ethernet controller is a VIA Rhine chipset.

A quick bit of googling shows that this chipset has been troublesome in linux for some time.

Take a look at this thread. Similar problems to yours.

[http://ubuntuforums.org/showthread.php?t=897982&highlight=via-rhine](http://ubuntuforums.org/showthread.php?t=897982&highlight=via-rhine)

.

---

### Post by Shinka.S on 2009-06-12
> **superprash2003 said:**
> post contents of /etc/dhcp3/dhclient.conf file

```
# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, domain-search, host-name,
	netbios-name-servers, netbios-scope, interface-mtu,
	rfc3442-classless-static-routes, ntp-servers;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
```

---

### Post by Shinka.S on 2009-06-12
> **andersbk said:**
> Look at your lspci output and your lshw -C network output.

Kernel is telling you that the ethernet controller is a VIA Rhine chipset.

A quick bit of googling shows that this chipset has been troublesome in linux for some time.

Take a look at this thread. Similar problems to yours.

[http://ubuntuforums.org/showthread.php?t=897982&highlight=via-rhine](http://ubuntuforums.org/showthread.php?t=897982&highlight=via-rhine)

.

Thank you very much I'm going to look at it ! Quickly I tried the command [COLOR="Blue"]mii-tool -F 10baseT-HD[/COLOR] at the end of the discussion, it didn't work, but I'll take a look at the entire discussion tomorrow morning.

---

### Post by superprash2003 on 2009-06-13
you could try this , it may solve your DHCP issue [http://www.prash-babu.com/2009/05/how-to-fix-ip-by-dhcp-issue-in-ubuntu.html](http://www.prash-babu.com/2009/05/how-to-fix-ip-by-dhcp-issue-in-ubuntu.html)

---

### Post by Shinka.S on 2009-06-13
It's not an Ubuntu-specific problem, I've tried openSUSE, Mint and Ubuntu 9.04, it's definitely a problem between Linux and my Network card.

---

### Post by Shinka.S on 2009-06-24
I got a new network card. Everything is working fine.

---

### Post by hapheston on 2009-06-24
I m a new user of Ubuntu
m currently using 9.04 and too have vista loaded in my system. for connecting to internet in vista i used to create icons that would take my broadband password and user id and i could browse my internet. but m unable to do the same in ubuntu. can someone plz help me through this...??

---

