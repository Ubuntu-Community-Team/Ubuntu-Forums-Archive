---
title: "belkin f5d7010 with rt2500 chip"
date: 2006-03-08
forum: Networking &amp; Wireless
---

### Post by elp on 2006-03-08
I am a newbie with linux
Wireless is loaded in system, admin, network, using wifi-radar shows proper connection and wireless lights are on.
I can not get connected to internet.
elp7@ubuntu:~$ sudo route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0

elp7@ubuntu:~$ iwconfig ra0
ra0       RT2500 Wireless  ESSID:"2WIRE966"
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-192 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

elp7@ubuntu:~$ iwlist ra0 scan
ra0       Scan completed :
          Cell 01 - Address: 00:0D:72:AD:7A:09
                    Mode:Managed
                    ESSID:"2WIRE493"
                    Encryption key:on
                    Channel:6
                    Quality:0/100  Signal level:-71 dBm  Noise level:-192 dBm
          Cell 02 - Address: 00:14:95:41:43:9A
                    Mode:Managed
                    ESSID:"2WIRE966"
                    Encryption key:on
                    Channel:6
                    Quality:0/100  Signal level:-29 dBm  Noise level:-192 dBm
          elp7@ubuntu:~$ sudo dhclient ra0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/ra0/00:11:50:64:f0:d4
Sending on   LPF/ra0/00:11:50:64:f0:d4
Sending on   Socket/fallback
DHCPREQUEST on ra0 to 255.255.255.255 port 67
DHCPREQUEST on ra0 to 255.255.255.255 port 67
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
Trying recorded lease 192.168.0.102
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

essid=2WIRE966, wepkey=8300103966, dns=192.168.1.254 I am using sbc-yahoo-dsl (2wire.com) router.

thanks

---

### Post by roachk71 on 2006-03-08
[LEFT]Do you have your DNS addresses set using the DNS tab in the network settings panel? Sometimes you can't automatically get the DNS addresses through a DHCP lease, and this usually solves the issue.

I have a version 5 F5D7010 card; what's your version?

I'm asking this because if it's a version 5 (or 5000 as printed on the back label,) you just might have to compile a custom kernel along with the latest ndiswrapper to get that one to work. If so, please check out the top two links below, and follow all of the directions carefully. And be sure to remove the Windows driver first, since the format's changed. Oh, and the version 5 has an Atheros AR5211, in case you're wondering.

I couldn't get a reliable connection until I did.
[/LEFT]

---

### Post by elp on 2006-03-08
dsn is 192.168.1.254 as system, admin, network dsn tab shows, I do not use ndiswrapper since ubuntu recognized the wireless (belkin f5d7010 v3001 with rt2500 chip).

---

### Post by roachk71 on 2006-03-09
[LEFT]192.168.1.254? This looks like the broadcast address from the card to the router. What I'm talking about is/are the DNS server addresses from your ISP.

It certainly looks like an issue with insufficient information from the router's DHCP server. My old router would either default to using 192.168.1.1 (the router's IP address on its own LAN,) or the broadcast address, usually 192.168.1.254 or 192.168.1.255, depending on the link quality and speed. These happened with an older Linksys router.

You're lucky, at least, to have a more compatible card than this one initially was! ;)

Just remove that incorrect address and use either 192.168.1.1, or the DNS addresses supplied by your ISP, and all should be well.

If all isn't well, try using a static IP address for your card, keeping the ISP's DNS addresses. In that case, the router's not set up for DHCP, and you'll need them anyway.
[/LEFT]

---

### Post by fsck0ff on 2006-03-09
So 
1st you don't have a DHCP lease, so this is a problem. Try 
sudo ifconfig ra0 ip.add.re.ss ne.tm.a.sk (here you put your ip and netmask, if it works, we'll check later the DHCP thingie)
sudo ifconfig ra0 up
2nd your route is messed up, afaik you shoud have the default route through ra0 interface, not eth0
Can you paste the /etc/network/interfaces file also.

---

### Post by elp on 2006-03-09
roachk71
thanks for reply I got the dns from sbc.yahoo.com/dsl 68.94.156.1 and 68.94.157.1 but to no avail as your instructions.

---

### Post by elp on 2006-03-09
fsck0ff 
thanks for reply too
Since I have to go between windows Xp and ubuntu I will try your instruction and post it.

---

### Post by elp on 2006-03-09
fsck0ff 
here is what I did according to your instruction:

elp7@ubuntu:~$ sudo ifconfig ra0 ip.192.168.1.68 255.255.255.0
ip.192.168.1.68: Host name lookup failure
ifconfig: `--help' gives usage information.

elp7@ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

mapping hotplug
        script grep
        map eth0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
# The primary network interface

iface eth0 inet dhcp



























iface ra0 inet static
wireless-essid 2WIRE966
wireless-key s:8300-1039-66
address 192.168.1.0
netmask 255.255.255.0
gateway 192.168.1.254





auto eth0
elp7@ubuntu:~$
any thing else I should do please.

---

### Post by fsck0ff on 2006-03-09
the correct line should be
sudo ifconfig ra0 192.168.1.68 255.255.255.0
:>
apart from that use smt like

iface ra0 inet static
wireless-essid 2WIRE966
wireless-key s:8300-1039-66
address 192.168.1.68
netmask 255.255.255.0
gateway 192.168.1.254

in /etc/network/interfaces

---

### Post by elp on 2006-03-09
when I try the first command I get
elp7@ubuntu:~$ sudo ifconfig ra0 192.168.1.68 255.255.255.0
SIOCSIFADDR: Invalid argument
elp7@ubuntu:~$
 
and I copy-paste the static info. to /etc/network/interfaces now it shows like this.

elp7@ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

mapping hotplug
        script grep
        map eth0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
# The primary network interface

iface eth0 inet dhcp

iface ra0 inet static
wireless-essid 2WIRE966
wireless-key s:8300-1039-66
address 192.168.1.68
netmask 255.255.255.0
gateway 192.168.1.254





auto eth0
elp7@ubuntu:~$

more help.

---

### Post by fsck0ff on 2006-03-09
hmm
after you have this in your interfaces file
try with
sudo ifup ra0
and after that paste 
ifconfig -a

---

### Post by elp on 2006-03-09
elp7@ubuntu:~$ sudo ifup ra0
SIOCADDRT: Network is unreachable
Failed to bring up ra0.
elp7@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:09:08:78
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20113 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14320 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:18457562 (17.6 MiB)  TX bytes:2703894 (2.5 MiB)
          Interrupt:19 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3298444 (3.1 MiB)  TX bytes:3298444 (3.1 MiB)

ra0       Link encap:Ethernet  HWaddr 00:11:50:64:F0:D4
          inet addr:192.168.1.0  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:199 errors:0 dropped:0 overruns:0 frame:0
          TX packets:201 errors:1 dropped:1 overruns:0 carrier:0
          collisions:3 txqueuelen:1000
          RX bytes:14546 (14.2 KiB)  TX bytes:7744 (7.5 KiB)
          Interrupt:17

elp7@ubuntu:~$

---

### Post by elp on 2006-03-09
just extra info. when I go to internet wifi-radar it shows the wireless is connected to "2wire966" and the light on the wireless are flashing.

---

### Post by elp on 2006-03-09
1- more info: when I use wired connection the wifi-radar show wireless is connected with ip 192.168.1.64 and the lights are flashing on the wireless eventhough I did not activate the wireless. when I activate the wireless alone wifi-radar shows ip as 127.0.0.1.
2- wired connection only modifies the dns from 68.94.156.1 and 68.94.157.1 tp 192.168.1.254 and domian to gateway.2wire.net.

---

### Post by fsck0ff on 2006-03-09
so in my /etc/network/interfaces I have the following
(all lines that have to deal with eth0 (my network card) are commented, because I am only using wireless)

auto ra0
iface ra0 inet static
address 192.168.33.102 (change this to actual IP)
netmask 255.255.255.0
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up iwconfig ra0 essid myessid (change to actual SSID)
pre-up iwconfig ra0 mode Managed
pre-up iwconfig ra0 channel 11 (you should change this to your channel)
pre-up iwconfig ra0 key ***** (enter your key here)
pre-up ifconfig ra0 up
network 192.168.33.0 (change to your network)
gateway 192.168.33.1 (change to your gateway)
dns-nameservers 192.168.33.1 (change to your dns)

after entering this reboot and give ifconfig and route information

---

### Post by elp on 2006-03-09
I did change the interfaces according to your instruction when rebooted the system it froze after login username and password but the lights on the wireless were flashing.

elp7@ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

#mapping hotplug
#       script grep
#       map eth0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
# The primary network interface

#iface eth0 inet dhcp

auto ra0
iface ra0 inet static
address 192.168.1.64
netmask 255.255.255.0
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up iwconfig ra0 essid 2WIRE966
pre-up iwconfig ra0 mode Managed
pre-up iwconfig ra0 channel 6
pre-up iwconfig ra0 key 8300103966
pre-up ifconfig ra0 up
network 192.168.1.0
gateway 192.168.1.254
dns-nameservers 68.94.156.1







#auto eth0

elp7@ubuntu:~$

elp7@ubuntu:~$ sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:09:08:78
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:376 errors:0 dropped:0 overruns:0 frame:0
          TX packets:259 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:442256 (431.8 KiB)  TX bytes:22733 (22.2 KiB)
          Interrupt:19 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3071 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3071 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:280521 (273.9 KiB)  TX bytes:280521 (273.9 KiB)

ra0       Link encap:Ethernet  HWaddr 00:11:50:64:F0:D4
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:185 errors:0 dropped:0 overruns:0 frame:0
          TX packets:465 errors:0 dropped:0 overruns:0 carrier:0
          collisions:8 txqueuelen:1000
          RX bytes:12580 (12.2 KiB)  TX bytes:18192 (17.7 KiB)
          Interrupt:17 Base address:0x8000

elp7@ubuntu:~$elp7@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 ra0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 ra0
elp7@ubuntu:~$
 please help.

---

### Post by roachk71 on 2006-03-10
[LEFT]Hmmm... This one's a real doozy.

Judging by that hang behavior, there are only three other causes I can think of at the moment:

1: an IRQ conflict (I know, sounds impossible with all of the improvements PCI provides, but some devices don't like their interrupts shared,) or

2: a chipset (and/or driver) as yet unsupported by ndiswrapper or the restricted modules (one of which is madwifi; I wonder if you've tried that yet?), or

3: poor IRQ routing support in the machine (mine has this problem somewhat; I bought a TI-based card a while back, and it froze the PC as well due to bad IRQ routing. That card even worked badly under Windows.)

You might want to check in your machine's BIOS settings and try to re-assign IRQs, if the BIOS allows for it. By the way, 17 is a rather odd IRQ for a network card of just about any type. I believe the card I'm using now has IRQ 10 assigned to it; most are within the 7-12 range.

Just be careful your settings don't overlap with other ports, like serial, parallel and video.

The bad routing issue is a hardware shortcoming: the ACPI is used in place of an APIC chip for interrupt routing, and most of the time, can't handle IRQs above 15. It's like we're returning to the dark ages of the XT...

I'm not sure if the Ubuntu kernels support the option, but you could also try pci=biosirq in your /boot/grub/menu.lst file, like this example:
```

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/mapper/Ubuntu-root pci=biosirq ro (replace the /mapper... with your root partition name)

``` and run update-grub, then reboot.
 
Let me know how it all works out.
[/LEFT]

---

### Post by fsck0ff on 2006-03-10
In my opinion now it should be working :)
the only problem that I can see is that you have eth0 with assigned ip, which should not happen, so I suggest you do a
sudo ifconfig eth0 down
and after that try pinging some address

ra0 Link encap:Ethernet HWaddr 00:11:50:64:F04
inet addr:192.168.1.64 Bcast:192.168.1.255 Mask:255.255.255.0
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:185 errors:0 dropped:0 overruns:0 frame:0
TX packets:465 errors:0 dropped:0 overruns:0 carrier:0
collisions:8 txqueuelen:1000
RX bytes:12580 (12.2 KiB) TX bytes:18192 (17.7 KiB)
Interrupt:17 Base address:0x8000

this shows that there is some traffic going from and to the wireless interface, so I really think it should work

and about the freeze, you were in gdm, entered your user and password and it froze?
or you did a console login?
How did you pasted this stuff then :)

---

### Post by roachk71 on 2006-03-10
[LEFT]I'd have to agree; Having two ports assigned without bridging also creates a very annoying problem. Thanks for reminding me. :cool:
[/LEFT]

---

