---
title: "Unable to connect to internet using Wired internet connection"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by kanna1620 on 2010-01-11
Hi All,
I recently installed Ubuntu 9.10 on my Dell Inspiron 1545 64-bit laptop. Before that I used Windows7. In Windows, the internet connection worked perfectly well. But after installing Ubuntu, I am unable to connect to the internet. The network-manager applet finally says that "You are disconnected". When I do the "ifconfig", I got no IP address.

So, I installed Ubuntu 9.04 in the same system. But the problem persists.

I gone through many posts in this forum but nothing was useful.
Please help me getting my internet connection working.

Thanks in advance.

---

### Post by lrcaballero on 2010-01-11
I found this in the internet hope this can help....

[http://en.community.dell.com/forums/t/19085663.aspx](http://en.community.dell.com/forums/t/19085663.aspx)

To me it sounds like a network card problem..

Luis

---

### Post by kanna1620 on 2010-01-12
> **lrcaballero said:**
> 
To me it sounds like a network card problem..

Luis

Hi Luis,
Thanks for the quick reply. I dont understand why it is working in Windows and not working in Ubuntu. Please let me know how can I check whether it is really the Network Card Problem.

Thanks in advance.
Kanna.

---

### Post by Iowan on 2010-01-12
Wired or wireless (or both)? I think I've probably worn the good out of [this]("http://ubuntuforums.org/showthread.php?t=1156441") thread.

---

### Post by CrammitTheFrog on 2010-01-12
Are you using the same network config settings as you did with Windows?  Also, if you're trying to use the wireless, you will need to install the proprietary driver, I think.  If you're using the wired network, check if Ubuntu sees the network card.  It should tell you if it sees a network card dispite a driver being installed, I think.

---

### Post by kanna1620 on 2010-01-12
> **CrammitTheFrog said:**
> Are you using the same network config settings as you did with Windows?  Also, if you're trying to use the wireless, you will need to install the proprietary driver, I think.  If you're using the wired network, check if Ubuntu sees the network card.  It should tell you if it sees a network card dispite a driver being installed, I think.

Hi,
Thanks for the reply.
I am using a wired internet connection. I am using dual boot Windows7 and Ubuntu 9.04. Internet is working in Windows but not in Ubuntu. So, I think, the config settings are fine and are same as in Windows. Whenever I plug-in the internet cord into the system while in Ubuntu, the network manager applet goes round and round and finally says that "Wired Lan is disconnected. You are offline.".

Please let me know how to check whether Ubuntu recognized the network cord or not.

Thanks in advance.
- Kanna

---

### Post by CrammitTheFrog on 2010-01-12
Is the LED where you plug the network cable into the computer flashing green?  Double check your Windows network settings just to be sure.  Most networks are set to get their IPs and such automatically.  If this is the case, then Ubuntu autos to that network setting, I think.  Have you tried looking at the info in the network manager?  That's where I would start.

I'm sorry if I not much a help, I've been using Ubuntu for about 6 months now and have experienced my own huddles setting up a wireless network.

---

### Post by kanna1620 on 2010-01-13
> **CrammitTheFrog said:**
> Is the LED where you plug the network cable into the computer flashing green?  Double check your Windows network settings just to be sure.  Most networks are set to get their IPs and such automatically.  If this is the case, then Ubuntu autos to that network setting, I think.  Have you tried looking at the info in the network manager?  That's where I would start.

Hi,
The LED is flashing. No problem with the network card in Windows. It is perfectly working. I have been posting from Windows only.
> 
I'm sorry if I not much a help, I've been using Ubuntu for about 6 months now and have experienced my own huddles setting up a wireless network.

Thanks for your input.

---

### Post by kanna1620 on 2010-01-13
I have executed some networking commands. The output is:

1. ifconfig:
============
```
kanna@kanna-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:64:70:ed:45  
          inet addr:192.168.0.35  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::225:64ff:fe70:ed45/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4049 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:498602 (498.6 KB)  TX bytes:8469 (8.4 KB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 90:4c:e5:3a:b0:b5  
          inet6 addr: fe80::924c:e5ff:fe3a:b0b5/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:166 errors:0 dropped:0 overruns:0 frame:0
          TX packets:166 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12928 (12.9 KB)  TX bytes:12928 (12.9 KB)
```

2. PING
========
```
kanna@kanna-laptop:~$ ping google.com
ping: unknown host google.com
```

3. lshw
=======
```
kanna@kanna-laptop:~$ sudo lshw -C network
[sudo] password for kanna: 
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 90:4c:e5:3a:b0:b5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:70:ed:45
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 76:99:b4:cd:bb:2f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

4. ethtool
==========
```
kanna@kanna-laptop:~$ ethtool -i eth0
driver: sky2
version: 1.22
firmware-version: N/A
bus-info: 0000:09:00.0
```

5. dhclient
===========
```
kanna@kanna-laptop:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/pan0/76:99:b4:cd:bb:2f
Sending on   LPF/pan0/76:99:b4:cd:bb:2f
Listening on LPF/eth1/90:4c:e5:3a:b0:b5
Sending on   LPF/eth1/90:4c:e5:3a:b0:b5
Listening on LPF/eth0/00:25:64:70:ed:45
Sending on   LPF/eth0/00:25:64:70:ed:45
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
.
.
.
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

5. nm-tool
==========
```
kanna@kanna-laptop:~$ nm-tool
NetworkManager Tool
State: disconnected
** (process:4969): WARNING **: <WARN>  get_one_connection(): error: invalid connection: 'NMSettingConnection' / 'type' invalid: 3
- Device: eth0 -------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             disconnected
  Default:           no
  HW Address:        00:25:64:70:ED:45

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on


- Device: eth1 ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        90:4C:E5:3A:B0:B5

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    sudhir:          Infra, 00:1B:57:DD:E9:61, Freq 2412 MHz, Rate 0 Mb/s, Strength 20 WEP
```

Please let me know what is the issue. If you need more information, please let me know.

I dont want to go to Windows.

Please help me :(:(

---

### Post by roadtripdave on 2010-01-13
Do you use a router?  Have you made any adjustments in the past to its DHCP settings by chance?  In Ubuntu can you run  ```
lspci
``` in a terminal and post the output for Ethernet Controller as well.  Also posting or checking the output of the ```
dmesg
``` command might shine some light on the issue.  Or check the logs in /var/log .  A quick way of checking that directory could be something like ```
sudo grep -ri eth0 dmesg messages
```

Regards

---

### Post by kanna1620 on 2010-01-14
> **Iowan said:**
> Wired or wireless (or both)? I think I've probably worn the good out of [this]("http://ubuntuforums.org/showthread.php?t=1156441") thread.

Hi Iowan,

Followed the steps, but no luck. :(

---

### Post by kanna1620 on 2010-01-14
> **roadtripdave said:**
> Do you use a router?  Have you made any adjustments in the past to its DHCP settings by chance?  In Ubuntu can you run  ```
lspci
``` in a terminal and post the output for Ethernet Controller as well.  Also posting or checking the output of the ```
dmesg
``` command might shine some light on the issue.  Or check the logs in /var/log .  A quick way of checking that directory could be something like ```
sudo grep -ri eth0 dmesg messages
```

Regards

Hi radtripdave,
I dont use any router. Its is a direct connection. I have not made any changes to the DHCP settings. I ran the above commands, and the output is:
```

lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
Subsystem: Dell Device 02aa
Flags: bus master, fast devsel, latency 0
Capabilities: <access denied>
Kernel driver in use: agpgart-intel
Kernel modules: intel-agp
.
.
Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
	Subsystem: Dell Device 02aa
	Flags: bus master, fast devsel, latency 0, IRQ 2298
	Memory at f68fc000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at de00 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sky2
	Kernel modules: sky2

0c:00.0 
Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
	Subsystem: Dell Device 000c
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f69fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl

```

lspci
```

kanna@kanna-laptop:~$ lspci

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 
VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 
Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 
USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 
USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 
USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 
USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 
Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 
PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 
PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 
PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 
PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 
USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 
USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 
USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 
USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 
PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 
ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
```

dmesg:
```
kanna@kanna-laptop:~$ dmesg | grep eth

[    1.670439] Driver 'sd' needs updating - please use bus_type methods

[    1.670447] Driver 'sr' needs updating - please use bus_type methods

[    3.950975] sky2 eth0: addr 00:25:64:70:ed:45

[   10.377267] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.79.10

[   20.234077] sky2 eth0: enabling interface

[   20.234259] ADDRCONF(NETDEV_UP): eth0: link is not ready

[   21.701040] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both

[   21.701471] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

[   25.948045] eth1: no IPv6 routers present

00:1f.2 
SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 
SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 
Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 
Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```
After this, I have changed the /etc/resolv.conf to include the following lines to
nameserver 202.88.130.5
nameserver 202.88.130.67
I rebooted, but no luck.

dmesg output:
```
kanna@kanna-laptop:~$ dmesg | grep eth
[    1.670439] Driver 'sd' needs updating - please use bus_type methods
[    1.670447] Driver 'sr' needs updating - please use bus_type methods
[    3.950975] sky2 eth0: addr 00:25:64:70:ed:45
[   10.377267] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.79.10
[   20.234077] sky2 eth0: enabling interface
[   20.234259] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.701040] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   21.701471] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   25.948045] eth1: no IPv6 routers present

```

Please help me :( :(

---

### Post by changingstate on 2010-01-14
Can you run this command on the machine and post the results, please?

```
sudo route -n
```

---

### Post by roadtripdave on 2010-01-14
Hi Kanna,
  I'm very curious about your ip address from the ifconfig results posted, the 192.168.0.35 address just looks like a private network address to me.  Could you verify your ip address when on windows and see if it too is around or something like the above?

Regards,
Dave

---

### Post by Iowan on 2010-01-14
> **kanna1620 said:**
> Followed the steps, but no luck. :(I had my doubts that it would help, but just in case...

---

### Post by kanna1620 on 2010-01-14
> **Iowan said:**
> I had my doubts that it would help, but just in case...

Thank you, anyway Iowan :)

---

### Post by kanna1620 on 2010-01-14
> **roadtripdave said:**
> Hi Kanna,
  I'm very curious about your ip address from the ifconfig results posted, the 192.168.0.35 address just looks like a private network address to me.  Could you verify your ip address when on windows and see if it too is around or something like the above?

Regards,
Dave

Hi roadtripdave,
I think, it is because of a wireless network that my laptop accessed at that time. But at that time also I did not have internet working. I had once checked in Windows and remember the IP something like 202.190.X.XX.
Anyway, I would post the results once I go to my home.

---

### Post by kanna1620 on 2010-01-14
Hi All,

Today, I played with the /etc/dhcp3/dhclient.conf as suggested in [this post]("http://ubuntuforums.org/showthread.php?p=7276275#post7276275").
Now, all of a sudden, in Windows also it is not connecting to internet. :( :(.

I think I need to reinstall Windows and Ubuntu. :(

---

### Post by Iowan on 2010-01-14
Sometimes trying to restart from one OS to the other can result in drivers not being reset, but from a cold boot, they *should not* affect each other. Hope it's not a sign of failing component...

---

### Post by kanna1620 on 2010-01-14
> **Iowan said:**
> Sometimes trying to restart from one OS to the other can result in drivers not being reset, but from a cold boot, they *should not* affect each other. Hope it's not a sign of failing component...


What is ***Cold Boot***???

---

### Post by Iowan on 2010-01-14
Sorry... that'd be from a powered-down state (as opposed to the 3-finger salute... CTRL-ALT-Delete)

---

### Post by kanna1620 on 2010-01-14
> **roadtripdave said:**
> Hi Kanna,
  I'm very curious about your ip address from the ifconfig results posted, the 192.168.0.35 address just looks like a private network address to me.  Could you verify your ip address when on windows and see if it too is around or something like the above?

Regards,
Dave

Hi Dave,
The ipconfig results in Windows:
```
C:\Users\kanna>ipconfig

Windows IP Configuration


PPP adapter Broadband Connection 2:

   Connection-specific DNS Suffix  . :
   IPv4 Address. . . . . . . . . . . : 219.90.97.153
   Subnet Mask . . . . . . . . . . . : 255.255.255.255
   Default Gateway . . . . . . . . . : 0.0.0.0

Ethernet adapter Bluetooth Network Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Wireless LAN adapter Wireless Network Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::313b:cf83:2a30:4865%11
   Autoconfiguration IPv4 Address. . : 169.254.72.101
   Subnet Mask . . . . . . . . . . . : 255.255.0.0
   Default Gateway . . . . . . . . . : fe80::6ce5:86fa:4e48:c78b%11
```

Let me know if you need any other info.

---

### Post by kanna1620 on 2010-01-14
> **changingstate said:**
> Can you run this command on the machine and post the results, please?

```
sudo route -n
```

Hi Changingstate,
The output is:
```

kanna@kanna-laptop:~$ sudo route -n
[sudo] password for kanna: 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```

Let me know if you need any more info.

---

### Post by roadtripdave on 2010-01-14
Ok, now that ip from windows looks better, something pretty similar to it should be coming up in Ubuntu but since its not maybe you can check the Network Connections settings.  Go to System -> Preferences -> Network Connections . Under the Wired tab you should see your eth0 connection.  Select it and click edit and click on the IPv4 Settings tab.  You should be seeing something similar to the image below.  If its something different adjust it to Automatic, apply it and try connecting again.  Let us know how it goes..

---

### Post by kanna1620 on 2010-01-14
> **roadtripdave said:**
> Go to System -> Preferences -> Network Connections . Under the Wired tab you should see your eth0 connection.  Select it and click edit and click on the IPv4 Settings tab.  You should be seeing something similar to the image below.  If its something different adjust it to Automatic, apply it and try connecting again.  Let us know how it goes..

I have done that Dave. But no use :(

---

### Post by roadtripdave on 2010-01-14
Do you remember if the internet worked when you used the Ubuntu Live CD by chance?  If not maybe try that...  Put in the live cd and see if the internet works.?  If this doesn't work, maybe I need to know more info about your setup.  Are you using DSL or Cable?  Do you have only a DSL/Cable modem with an ethernet cable going from it to your computer?  This will just help give me more of an idea on your setup.

Regards,
Dave

---

### Post by kanna1620 on 2010-01-14
> **roadtripdave said:**
> Do you remember if the internet worked when you used the Ubuntu Live CD by chance?  If not maybe try that...  Put in the live cd and see if the internet works.?  If this doesn't work, maybe I need to know more info about your setup.  Are you using DSL or Cable?  Do you have only a DSL/Cable modem with an ethernet cable going from it to your computer?  This will just help give me more of an idea on your setup.

Regards,
Dave

I have tried that also. (Live CD). That also didnt work. I am using Cable. Not DSL. No modem or what so ever. From my ISP I have a direct connection through CAT5 Cable.

Thanks in advance.

---

### Post by roadtripdave on 2010-01-14
Ok I'm hoping we might have found something here.  I've been looking into more information on PPPoE and think you should try this as it looks like this is how you windows connection is setup.  Open a terminal and type the following:
```
sudo pppoeconf
```

After it detects your network adapters select yes and hit enter and it'll do some automatic searching.. HOPEFULLY if we're lucky it'll detect things automatically :) , wishful thinking but worth a shot. 

Dave

---

### Post by sgosnell on 2010-01-15
Your wpa-supplicant isn't working.  Notice this part: ```
Listening on LPF/pan0/76:99:b4:cd:bb:2f
Sending on   LPF/pan0/76:99:b4:cd:bb:2f
Listening on LPF/eth1/90:4c:e5:3a:b0:b5
Sending on   LPF/eth1/90:4c:e5:3a:b0:b5
Listening on LPF/eth0/00:25:64:70:ed:45
Sending on   LPF/eth0/00:25:64:70:ed:45
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
.
.
.
No DHCPOFFERS received.
No working leases in persistent database - sleeping.  
```

This is usually caused by incorrect security settings when trying to connect to a wireless router, but it appears that it sometimes happens with ethernet.  See [this thread](http://ubuntuforums.org/showthread.php?t=1021585) and make sure you read the other threads linked in one of the posts.  Different solutions by different people with different hardware.  Good luck.

---

### Post by kanna1620 on 2010-01-15
> **roadtripdave said:**
> Ok I'm hoping we might have found something here.  I've been looking into more information on PPPoE and think you should try this as it looks like this is how you windows connection is setup.  Open a terminal and type the following:
```
sudo pppoeconf
```

After it detects your network adapters select yes and hit enter and it'll do some automatic searching.. HOPEFULLY if we're lucky it'll detect things automatically :) , wishful thinking but worth a shot. 

Dave

I have done this also. But no connection :(

---

### Post by roadtripdave on 2010-01-15
The only other thing I can think of would be to see if you can check the PPP connection settings in Windows.  Go to network connections and right click PPP and go to properties.  Look to see how its setup because this may be key.  If there's any manual settings entered, these will ultimately have to be configured in Ubuntu somehow as well I'd suspect.

Regards,
Dave

---

### Post by kanna1620 on 2010-01-15
> **roadtripdave said:**
> The only other thing I can think of would be to see if you can check the PPP connection settings in Windows.  Go to network connections and right click PPP and go to properties.  Look to see how its setup because this may be key.  If there's any manual settings entered, these will ultimately have to be configured in Ubuntu somehow as well I'd suspect.

Regards,
Dave

Hi Dave,
Everything is set to "automatic" in Windows. I use Windows7.

---

### Post by roadtripdave on 2010-01-15
After thinking about this it seems that pppoe is not installed by default on Ubuntu...as far as I know, so we probably should have done that first.  I'm using 9.10 and it didn't so... Use the below line to install.

```
sudo apt-get install pppoe
```If prompted during the install on whether or not to overwrite a config file I'd enter 'Y' to accept the new one.  Reboot and then run the below again and see what happens.

```
sudo pppoeconf
```Hope that helps..

A Link to check out.. old but still applies I think [http://ubuntuforums.org/archive/index.php/t-138.html](http://ubuntuforums.org/archive/index.php/t-138.html)

Dave

---

### Post by kanna1620 on 2010-01-15
> **roadtripdave said:**
> After thinking about this it seems that pppoe is not installed by default on Ubuntu...as far as I know, so we probably should have done that first.  I'm using 9.10 and it didn't so... Use the below line to install.
Dave

I am using Ubuntu 9.04 and pppoeconf is already installed. I have used it to configure the network. But no luck.

---

### Post by sgosnell on 2010-01-15
One more thing I can think of - right-click on the network icon in the panel, select Edit Connections, go to the Wired tab, and add a new wired connection, with the proper settings, and see if that helps.  Make sure "Use 802.1x security" is not checked, and the IPv4 settings are automatic DHCP.

---

### Post by roadtripdave on 2010-01-15
Hi Kanna,  The pppoe appliction is actually different from pppoeconf.  Yes pppoeconf is already there but not the pppoe application.  For that you need to grab it using apt-get or synaptic package manager.  The apt-get method is in my previous post.

Regards,
Dave

---

### Post by kanna1620 on 2010-01-15
> **roadtripdave said:**
> Hi Kanna,  The pppoe appliction is actually different from pppoeconf.  Yes pppoeconf is already there but not the pppoe application.  For that you need to grab it using apt-get or synaptic package manager.  The apt-get method is in my previous post.

Regards,
Dave

I can use this method if I have an active internet connection, which is not my case :(
Please help me :(

---

### Post by kanna1620 on 2010-01-15
> **sgosnell said:**
> One more thing I can think of - right-click on the network icon in the panel, select Edit Connections, go to the Wired tab, and add a new wired connection, with the proper settings, and see if that helps.  Make sure "Use 802.1x security" is not checked, and the IPv4 settings are automatic DHCP.

I have already done for many times NO luck :(

---

### Post by kanna1620 on 2010-01-15
> **roadtripdave said:**
> Hi Kanna,  The pppoe appliction is actually different from pppoeconf.  Yes pppoeconf is already there but not the pppoe application.  For that you need to grab it using apt-get or synaptic package manager.  The apt-get method is in my previous post.

Regards,
Dave

Hi Dave,
I can download the .deb package in Windows and can install it in Ubuntu. Could you please tell me where can I get it in the internet. (The link to package location in the repository)

Thanks.

---

### Post by roadtripdave on 2010-01-16
Wow, sorry about that.. alright so here is the link to download the pppoe application.

[http://packages.ubuntu.com/jaunty/i386/pppoe/download](http://packages.ubuntu.com/jaunty/i386/pppoe/download)

Then run it in Ubuntu and run pppoeconf after the install.

Regards

---

### Post by kanna1620 on 2010-01-17
> **roadtripdave said:**
> Wow, sorry about that.. alright so here is the link to download the pppoe application.

[http://packages.ubuntu.com/jaunty/i386/pppoe/download](http://packages.ubuntu.com/jaunty/i386/pppoe/download)

Then run it in Ubuntu and run pppoeconf after the install.

Regards

Hi Dave,
Thanks, I am going to download them for my Ubuntu 9.10. I have installed 9.10 in the hope of getting internet connection working. But no luck. :(. I will let you know once I install the above package.

Thanks.

---

### Post by kanna1620 on 2010-01-20
> **roadtripdave said:**
> Wow, sorry about that.. alright so here is the link to download the pppoe application.

[http://packages.ubuntu.com/jaunty/i386/pppoe/download](http://packages.ubuntu.com/jaunty/i386/pppoe/download)

Then run it in Ubuntu and run pppoeconf after the install.

Regards

Hi Dave,
I have installed the above package and it worked :):D. The connection is slow, but it is working. Dont know if I logoff and login again what happens. Lets see what happens. Thank you very much for your help. If it works after reboot also we can close this thread :)

Thanks,

---

### Post by kanna1620 on 2010-01-21
> **kanna1620 said:**
> Hi Dave,
I have installed the above package and it worked :):D. The connection is slow, but it is working. Dont know if I logoff and login again what happens. Lets see what happens. Thank you very much for your help. If it works after reboot also we can close this thread :)

Thanks,

Hi Dave,

The connection is working for a few minutes only :confused: I dont know what is happening. For a few minutes the connection is active and then it was dead. Unable to browse the net. Repeated the "pppoe" thing. But no result. Also it was very slow.

Please help me.

---

