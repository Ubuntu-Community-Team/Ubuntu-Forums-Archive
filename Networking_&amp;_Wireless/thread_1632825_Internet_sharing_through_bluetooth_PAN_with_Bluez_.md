---
title: "Internet sharing through bluetooth PAN with Bluez 4.x"
date: 2010-11-28
forum: Networking &amp; Wireless
---

### Post by mawe3661 on 2010-11-28
[SOLVED]

However, the instruction in this post is erroneous - see the link in the latest post #3 - I will try to clean up this soon



I would like to have help with configuring a server connected to internet as an internet access point. The server has a bluetooth dongle, and I would like to connect one or two laptops to the internet over bluetooth and the server. 

The server is running debian and has Bluez 4.x installed. The laptops are with Ubuntu 10.10.

I found this gide which is for Gentoo - [http://en.gentoo-wiki.com/wiki/Bluetooth_Network_Aggregation_Point](http://en.gentoo-wiki.com/wiki/Bluetooth_Network_Aggregation_Point)

I've set up the bluetooth configuration on the server, but has not been able to pair my laptop with the server. I don't know if the fault lies in server bluetooth config or the client. I have been able to add the server as a bluetooth PAN, but when I try connect (network manager) I can't.

My first question: What steps are necessary to succeed in pairing two devices with Bluez 4.x?

When pairing has been completed, I am not sure how to set up the bridging of network devices on the server to complete internet access. All I know that I have to set up /etc/bluetooth/network.conf and /etc/network/interfaces the right way. Any help leading in the right direction would be much appreciated!!

Provided I get answers I will write as detailed guide as possible when I succeed to help others. Thanks in advance! 

I'd be happy to supply any conf file of importance.

---

### Post by mawe3661 on 2010-11-29
Ok, I managed it.

To start with, I found another guide: [http://www.linux.com/learn/tutorials/346552-personal-area-networking-with-bluetooth](http://www.linux.com/learn/tutorials/346552-personal-area-networking-with-bluetooth)

My set up. I have a server connected to the internet through a router. On the server there is a bluetooth dongle which I would like to share internet to other computers in my home. In my case, the server is running debian and my clients (laptops) Ubuntu 10.10.

To sum up my experience, there are the following steps:

1. Install software
2. Set up bluetooth on server
3. Set up network bridging on server
4. Pair the devices (both on server and client side)

1. Install software
You need bluez and bridge-utils. If you come across a script called simple-agent in descriptions on web pages you will find it in /usr/share/doc/bluez/examples/ . The README file tells what extra python packages you need to get it working. There are some useful scripts in there.

2. Set up bluetooth on the server
Read the guide above. Here are the files I have changed manually:

```
root@stereo:/var/lib/bluetooth/00:10:60:D1:44:A8# ls
classes  features  lastused  manufacturers  pincodes
config	 lastseen  linkkeys  names	    trusts
root@stereo:/var/lib/bluetooth/00:10:60:D1:44:A8# cat config
name stereo-0
class 0x4a0a21
mode discoverable
root@stereo:/var/lib/bluetooth/00:10:60:D1:44:A8# cat pincodes 
34:C3:AC:AB:66:42 0000
00:03:7A:FD:26:40 0000
root@stereo:/var/lib/bluetooth/00:10:60:D1:44:A8# cat trusts 
34:C3:AC:AB:66:42 [all]
00:03:7A:FD:26:40 [all]
root@stereo:/var/lib/bluetooth/00:10:60:D1:44:A8#
``` 

The class string (0x4a0a21) seem to live its own life. There is a descritption about it in the page above. The other two files - put adresses of bluetooth cards in there. This is a rather blunt configuration, but you can tweak it later if you like.

Now other files:

```
root@stereo:/etc/bluetooth# ls
audio.conf  main.conf	  network.service  serial.conf
input.conf  network.conf  rfcomm.conf
root@stereo:/etc/bluetooth# cat main.conf 
[General]

# List of plugins that should not be loaded on bluetoothd startup
#DisablePlugins = network,input

# Default adaper name
# %h - substituted for hostname
# %d - substituted for adapter id
Name = %h-%d

# Default device class. Only the major and minor device class bits are
# considered.
Class = 0x020100

# How long to stay in discoverable mode before going back to non-discoverable
# The value is in seconds. Default is 180, i.e. 3 minutes.
# 0 = disable timer, i.e. stay discoverable forever
DiscoverableTimeout = 0

# How long to stay in pairable mode before going back to non-discoverable
# The value is in seconds. Default is 0.
# 0 = disable timer, i.e. stay pairable forever
PairableTimeout = 0

# Use some other page timeout than the controller default one
# which is 16384 (10 seconds).
PageTimeout = 8192

# Discover scheduler interval used in Adapter.DiscoverDevices
# The value is in seconds. Defaults is 0 to use controller scheduler.
DiscoverSchedulerInterval = 0

# What value should be assumed for the adapter Powered property when
# SetProperty(Powered, ...) hasn't been called yet. Defaults to true
InitiallyPowered = true

# Remember the previously stored Powered state when initializing adapters
RememberPowered = true

# Use vendor, product and version information for DID profile support.
# The values are separated by ":" and VID, PID and version.
#DeviceID = 1234:5678:abcd

# Do reverse service discovery for previously unknown devices that connect to
# us. This option is really only needed for qualification since the BITE tester
# doesn't like us doing reverse SDP for some test cases (though there could in
# theory be other useful purposes for this too). Defaults to true.
ReverseServiceDiscovery = true

# Enable name resolving after inquiry. Set it to 'false' if you don't need
# remote devices name and want shorter discovery cycle. Defaults to 'true'.
NameResolving = true

# Enable runtime persistency of debug link keys. Default is false which
# makes debug link keys valid only for the duration of the connection
# that they were created for.
DebugKeys = false
root@stereo:/etc/bluetooth# cat network.conf 
# Configuration file for the network service

# This section contains options which are not specific to any
# particular interface
[General]

# Disable link encryption: default=false
DisableSecurity=true

[PANU Role]

# Network interface name for PANU for connections. default:bnep%d
# (up to 16 characters)
#Interface=

# PAN user connection interface up script. default:none
Script=avahi-autoipd

[GN Role]

# Network Interface name for Group Network server. default:pan0
#Interface=

# Group Network connection interface up script. default:none
Script=avahi-autoipd

[NAP Role]

# Network Interface name for Network Access Point server. default:pan1
Interface=bridge0

# Network Access Point connection interface up script. default:none
Script=dhclient
root@stereo:/etc/bluetooth# cat network.service 
[Bluetooth Service]
Identifier=network
Name=Network service
Description=Bluetooth Personal Area Network service
Autostart=true
root@stereo:/etc/bluetooth#
``` 

This follows the above web page pretty well, so I'll elaborate if there are questions I can answer. 

3. Set up network bridging on server
This I found was the tricky part, since I find bridging a bit confusing. Anyway, here is my set-up (still on server)

```
root@stereo:/etc/network# ls
if-down.d	if-pre-up.d  interfaces      run
if-post-down.d	if-up.d      interfaces.bak
root@stereo:/etc/network# cat interfaces
auto eth0
iface eth0 inet manual

auto bridge0
iface bridge0 inet dhcp
  pre-up ifconfig eth0 down
  pre-up brctl addbr bridge0
  pre-up brctl addif bridge0 eth0
  pre-up ifconfig eth0 up
  post-down ifconfig eth0 down
  post-down brctl delif bridge0 eth0

auto pan1
iface pan1 inet manual
  pre-up brctl addbr bridge0
  pre-up brctl addif bridge0 $IFACE
  up ifconfig $IFACE 0.0.0.0 up
  down ifconfig $IFACE down
  post-down brctl delif bridge0 $IFACE

# The loopback network interface
auto lo
iface lo inet loopback
root@stereo:/etc/network#
``` 


And I also changed the following file:

```

root@stereo:/etc/default# head dhcpcd 
# Config file for dhcpcd. Note that you have to edit the interface
# name below, or duplicate the configuration for different interfaces.
# If you are editing this file just to get DNS servers set by DHCP,
# then you should consider installing the resolvconf package instead.

case ${INTERFACE} in
bridge0) 

root@stereo:/etc/default# 
```

Where it now reads bridge0 it previously read eth0.


4. Pair the devices (both on server and client side)
Now, I had problems paring the devices from the built in tool in Ubuntu (client side), so I edited "trusts" and "pincodes" in /var/lib/bluetooth/xx:xx:xx:xx:xx in the same way as on the server. After that I could connect!!!

---

### Post by mawe3661 on 2010-12-05
Se better description on this post: [http://forum.doozan.com/read.php?2,2698](http://forum.doozan.com/read.php?2,2698)

---

