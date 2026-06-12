---
title: "Disconnected ethernet, 10.04"
date: 2012-02-03
forum: Networking &amp; Wireless
---

### Post by WileyGaia on 2012-02-03
Hi
I have lost my network connection. I think this is since I ran Updates. It was working perfectly until then.
I have trawled ubuntuforums from my mobile phone to try get some info, and have posted all outputs from terminal commands I found on other threads (below). 
Background info: desktop pc running 10.04
I have a wireless router connected to my pc by ethernet cable (since I don't have wireless on my pc)
I have an ADSL line connected to my router. I can pick up the wireless internet signal from my router on my mobile phone.
My motherboards ethernet port is dead, so I have an Ethernet card inserted, this was working perfectly up until an "Update".
I have tried replacing the Ethernet cable, to no avail.
To note:
I am working from a work computer now, and do not have access to my home pc (the one with the problem) until tonight again...
I am totally clueless on how to fix this. I am very much NOT a linux guru and do not actually understand any of this terminal stuff, I generally use GUI's for my day-to-day stuff.

Here are some terminal outputs:

```

_:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 1697
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:30:18:a8:46:0a
Sending on   LPF/eth0/00:30:18:a8:46:0a
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

_:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 12
       serial: 00:30:18:a8:46:0a
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:25 memory:fddfc000-fddfffff ioport:de00(size=256)

_:~$cat /etc/network/interfaces
auto lo
iface lo inet loopback

_:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 12
       serial: 00:30:18:a8:46:0a
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:25 memory:fddfc000-fddfffff ioport:de00(size=256)

_:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:30:18:a8:46:0a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

ifconfig eth1
eth1: error fetching interface information: Device not found

_:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:30:18:a8:46:0a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth0:avahi Link encap:Ethernet  HWaddr 00:30:18:a8:46:0a  
          inet addr:169.254.4.163  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

_:~$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 1703
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:30:18:a8:46:0a
Sending on   LPF/eth0/00:30:18:a8:46:0a
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

_:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 1809
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

_:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3249  0 
nls_cp437               4919  0 
vfat                    8933  0 
fat                    47767  1 vfat
binfmt_misc             6587  1 
snd_hda_codec_realtek   203440  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_usb_audio          75765  0 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  4 snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss
snd_usb_lib            15801  1 snd_usb_audio
snd_hwdep               5412  2 snd_hda_codec,snd_usb_audio
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               57438  0 
ppdev                   5259  0 
snd                    54244  18 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               34425  1 uvcvideo
i915                  289715  3 
drm_kms_helper         29329  1 i915
parport_pc             25962  1 
usbhid                 36110  0 
usb_storage            40033  0 
v4l1_compat            13251  2 uvcvideo,videodev
psmouse                63677  0 
serio_raw               3978  0 
hid                    67288  1 usbhid
soundcore               6620  1 snd
drm                   163747  4 i915,drm_kms_helper
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
intel_agp              24375  2 i915
agpgart                31724  2 drm,intel_agp
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
floppy                 53016  0 
sky2                   40807  0 

_:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        00:30:18:A8:46:0A

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


_:~/temp1/src$ cat /etc/resolv.conf
# Generated by NetworkManager
domain Belkin
search Belkin
nameserver 192.168.2.1
nameserver 8.8.8.8
nameserver 8.8.8.4

_:~/temp1/src$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Device [11ab:4357] (rev 12)
	Kernel driver in use: sky2
	Kernel modules: sky2

_:~/temp1/src$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
_:~/temp1/src$ dmesg | egrep 'r8|eth0'
[    0.787341] sky2 eth0: addr 00:30:18:a8:46:0a
[   25.159178] sky2 eth0: enabling interface
[   25.159358] ADDRCONF(NETDEV_UP): eth0: link is not ready
_:~/temp1/src$ cat /etc/NetworkManager/nm-system-settings.conf
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

no-auto-default=00:30:18:a8:46:0a,

[ifupdown]
managed=false


```

---

### Post by praseodym on 2012-02-03
Hi,

try this one, I dont know if it works (but it will also not harm):

```
sudo ifconfig eth0 mtu 1500
sudo /etc/init.d/networking restart
```
If its not working, checkbox all user rights in "users&groups", login again, checkbox "available to all users" and "connect automatically", remove the wired connections in "cable" and "DSL" (if any), and reboot.

---

### Post by barong234 on 2012-02-03
[QUOTE=]

```

_:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 1697
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:30:18:a8:46:0a
Sending on   LPF/eth0/00:30:18:a8:46:0a
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.



```[/QUOTE]

[SIZE=2][FONT=Verdana]It seems your dhclient not working and you're not getting any ip.[/FONT][/SIZE]

---

### Post by WileyGaia on 2012-02-04
> **praseodym said:**
> Hi,

try this one, I dont know if it works (but it will also not harm):

```
sudo ifconfig eth0 mtu 1500
sudo /etc/init.d/networking restart
```
If its not working, checkbox all user rights in "users&groups", login again, checkbox "available to all users" and "connect automatically", remove the wired connections in "cable" and "DSL" (if any), and reboot.
Did the 2 commands
The "Connect to wireless and ethernet" box was unchecked, so i ticked that and restarted.
Still no connection.
Where do i find "avalable to all users" and "connect automatically"? Pls excuse my ignorance

---

### Post by WileyGaia on 2012-02-04
> **praseodym said:**
> Hi,

try this one, I dont know if it works (but it will also not harm):

```
sudo ifconfig eth0 mtu 1500
sudo /etc/init.d/networking restart
```
If its not working, checkbox all user rights in "users&groups", login again, checkbox "available to all users" and "connect automatically", remove the wired connections in "cable" and "DSL" (if any), and reboot.
Did the 2 commands
The "Connect to wireless and ethernet" box was unchecked, so i ticked that and restarted.
Still no connection.
Where do i find "avalable to all users" and "connect automatically"? Pls excuse my ignorance

---

### Post by praseodym on 2012-02-04
You find "avalable to all users" and "connect automatically" in the network-manager-applet (right-click->Edit connection->Wireless->edit)

---

### Post by WileyGaia on 2012-02-04
ok how bizarre
so:
I now have a good WIRED connection YeeehAAAAH - there is a new "Auto eth1" in the network manager...
BUT
now my WIRELESS is no longer active.... mobile phone cannot detect it at all, will go check "router" url now that I have a wired connection.

I must say this Ubuntu stuff is mystifying to say the least... at least I don't have to surf and respond on my mobile phone anymore... that was painful - I wonder what is gonna happen next time a turn my pc on...?

---

### Post by praseodym on 2012-02-04
Hi,

wired is preferred if active. Unplug the cable?!

---

### Post by WileyGaia on 2012-02-06
Thanks praseodym for your assistance so far...
ok so now I am dumbfounded
That eth1 wired connection (but no wireless) came up for 1 session only...
I am back to square 1 now i.e. I am getting wireless from my router on my mobile phone, BUT now that eth1 wired connection has "gone" and I am "not connected" to the network
SO
I KNOW that my pc has the ability to get connected, now how do I tell it to do that every time?
Also:
> **praseodym said:**
> You find "avalable to all users" and "connect automatically" in the network-manager-applet (right-click->Edit connection->Wireless->edit)
I can't do this, because there is no entry at all in any of the "tabs" on network manager.
However - when the eth1 came up for that 1 session, eth1 was in the "wired" tab, and those 2 checkboxes were ticked...
Also:
I have contacted my DSL provider for them to check my line for faults, since that could be something I need to ensure is working properly (could take a few days, this is Africa)

---

### Post by praseodym on 2012-02-07
Please show

```
cat /etc/udev/rules.d/70-persistent-net.rules
ifconfig -a
```

---

### Post by WileyGaia on 2012-02-08
I am starting to suspect that my DSL line is faulty.
This may take a few days for the DSL provider to respond, since they are not renowned for their turnaround times... its what happens when there is a monopoly...

I will post the results of the 2 new commands as soon as I have verified my line.

Thanks again for your ongoing help :-) much appreciated

---

### Post by WileyGaia on 2012-02-13
> **WileyGaia said:**
> I am starting to suspect that my DSL line is faulty.
This may take a few days for the DSL provider to respond, since they are not renowned for their turnaround times... its what happens when there is a monopoly...

I will post the results of the 2 new commands as soon as I have verified my line.

Thanks again for your ongoing help :-) much appreciated

Ok, AT LAST! The technician came to my home yesterday and has redone the whole thing, tested the line and verified that it is all good.

So, once again, I have my modem/router up and transmitting a WIRELESS signal, which I can receive on my mobile phone. BUT the WIRED PC is "disconnected".  

I may be off-track, but since I DID get a connection for 1 session on "eth1", this might have something to do with the fact that the ethernet port on my motherboard is "dead" and the ethernet card I have plugged in is not being recognised by the system? Excuse the beginner speculating here...:-)

I will post the results of 

cat /etc/udev/rules.d/70-persistent-net.rules
ifconfig -a

tonight when I get home

---

### Post by WileyGaia on 2012-02-13
> [quote]
~$ cat /etc/udev/rules.d/70-persistent-net.rules
#blahblahblah

#pci device 0x11ab:0x4357 (sky2)
subsystem=="net", action=="add", drivers=="?*", attr{address}=="00:30:18:a8:46:0a", attr{dev_id}=="0x0", attr{type}=="1", kernel=="eth*", name=="eth0"


#pci device 0x1106:0x3106 (via-rhine)
subsystem=="net", action=="add", drivers=="?*", attr{address}=="5c:d9:98:bd:6c:b5", attr{dev_id}=="0x0", attr{type}=="1", kernel=="eth*", name=="eth1"

[/quote]

[/quote][/quote]

---

### Post by WileyGaia on 2012-02-13
> [quote]
~$ cat /etc/udev/rules.d/70-persistent-net.rules
#blahblahblah

#pci device 0x11ab:0x4357 (sky2)
subsystem=="net", action=="add", drivers=="?*", attr{address}=="00:30:18:a8:46:0a", attr{dev_id}=="0x0", attr{type}=="1", kernel=="eth*", name=="eth0"


#pci device 0x1106:0x3106 (via-rhine)
subsystem=="net", action=="add", drivers=="?*", attr{address}=="5c:d9:98:bd:6c:b5", attr{dev_id}=="0x0", attr{type}=="1", kernel=="eth*", name=="eth1"

[/quote]

[/quote][/quote]

---

### Post by WileyGaia on 2012-02-13
So this via-rhine is the ethernet card i have plugged in... the sky2 must be the on-board ethernet port, which died on me, which is why i got the card

---

### Post by WileyGaia on 2012-02-13
> [quote]
~$ cat /etc/udev/rules.d/70-persistent-net.rules
#blahblahblah

#pci device 0x11ab:0x4357 (sky2)
subsystem=="net", action=="add", drivers=="?*", attr{address}=="00:30:18:a8:46:0a", attr{dev_id}=="0x0", attr{type}=="1", kernel=="eth*", name=="eth0"


#pci device 0x1106:0x3106 (via-rhine)
subsystem=="net", action=="add", drivers=="?*", attr{address}=="5c:d9:98:bd:6c:b5", attr{dev_id}=="0x0", attr{type}=="1", kernel=="eth*", name=="eth1"

[/quote]

[/quote][/quote]

---

### Post by WileyGaia on 2012-02-13
wiley@starseed:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:30:18:a8:46:0a  
          inet6 addr: fe80::230:18ff:fea8:460a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:168 (168.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

---

### Post by WileyGaia on 2012-02-13
wiley@starseed:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:30:18:a8:46:0a  
          inet6 addr: fe80::230:18ff:fea8:460a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:168 (168.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

---

### Post by WileyGaia on 2012-02-13
*%%$##@!!!
Sorry for all the double posts, driving this from my mobile phone is close to torture...

---

### Post by praseodym on 2012-02-13
These are two wired cards, arent they? Wireless is internal USB? Check

> lsusb
Did you insert the Login/PW in your router interface?

---

### Post by WileyGaia on 2012-02-13
> **praseodym said:**
> These are two wired cards, arent they? Wireless is internal USB? Check


Did you insert the Login/PW in your router interface?

Yes, there is an onboard ethernet port (dead) and so i have bought and plugged in an ethernet card.
Wireless is not applicable, since my pc does not have wireless. I merely use the wireless signal from my router for my mobile phone (posting this from mobile phone connected to wireless)

---

### Post by WileyGaia on 2012-02-13
I did configure the router with password prior to the connection being lost

---

### Post by praseodym on 2012-02-13
Did you check the MAC-address filter in your router?

---

### Post by WileyGaia on 2012-02-14
Whoah!!! I have a connection this morning!
Its an "eth1" connection, it is seeing the router!
I have not changed anything!
So HOW/WHY?
And what do I do when I turn my pc on tonight and it has "lost" the connection again?

some detail:
```

wiley@starseed:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:30:18:a8:46:0a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 5c:d9:98:bd:6c:b5  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::5ed9:98ff:febd:6cb5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15060 (15.0 KB)  TX bytes:7979 (7.9 KB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wiley@starseed:~$ cat /etc/resolv.conf route -n
     1	# Generated by NetworkManager
     2	domain Belkin
     3	search Belkin
     4	nameserver 192.168.2.1
cat: route: No such file or directory
wiley@starseed:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

wiley@starseed:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        00:30:18:A8:46:0A

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: eth1  [Auto eth1] ----------------------------------------------------
  Type:              Wired
  Driver:            via-rhine
  State:             connected
  Default:           yes
  HW Address:        5C:D9:98:BD:6C:B5

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1


wiley@starseed:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
snd_hda_codec_realtek   203440  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_usb_audio          75765  1 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  4 snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss
snd_usb_lib            15801  1 snd_usb_audio
snd_hwdep               5412  2 snd_hda_codec,snd_usb_audio
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i915                  289715  3 
uvcvideo               57438  0 
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5259  0 
drm_kms_helper         29329  1 i915
videodev               34425  1 uvcvideo
usbhid                 36110  0 
snd                    54244  20 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l1_compat            13251  2 uvcvideo,videodev
parport_pc             25962  1 
hid                    67288  1 usbhid
intel_agp              24375  2 i915
drm                   163747  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
psmouse                63677  0 
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 intel_agp,drm
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
floppy                 53016  0 
via_rhine              19154  0 
mii                     4381  1 via_rhine
sky2                   40807  0 
wiley@starseed:~$ 

```

---

### Post by WileyGaia on 2012-02-14
some more outputs while I have it up - gotta go to work soon, so will see what happens tonight when I get home...
```

wiley@starseed:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Device [11ab:4357] (rev 12)
	Kernel driver in use: sky2
	Kernel modules: sky2
02:01.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] [1106:3106] (rev 8b)
	Kernel driver in use: via-rhine
	Kernel modules: via-rhine

wiley@starseed:~$ cat /etc/resolv.conf
# Generated by NetworkManager
domain Belkin
search Belkin
nameserver 192.168.2.1


wiley@starseed:~$ sudo lshw -C network
[sudo] password for wiley: 
  *-network               
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 12
       serial: 00:30:18:a8:46:0a
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:25 memory:fddfc000-fddfffff ioport:de00(size=256)
  *-network
       description: Ethernet interface
       product: VT6105/VT6106S [Rhine-III]
       vendor: VIA Technologies, Inc.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth1
       version: 8b
       serial: 5c:d9:98:bd:6c:b5
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.2.5 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
       resources: irq:16 ioport:ee00(size=256) memory:fdcff000-fdcff0ff


```

---

### Post by WileyGaia on 2012-02-14
well well well
I still have my connection tonight :-)

---

