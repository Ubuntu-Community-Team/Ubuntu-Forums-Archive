---
title: "Can't get to my servers... no path to host?"
date: 2006-04-25
forum: Networking &amp; Wireless
---

### Post by charlesread2006 on 2006-04-25
Hey everybody!

I have just installed Ubuntu, I like it, the install went well, very little hands on config.  

I run my own email and web servers, they are perfectly reachable from the outside world... check it out: [http://charlesread.com](http://charlesread.com).  But I can't reach my domains from linux... that is I can't ping them, can't view them in Firefox, can't talk to my mail servers through Thunderbird.  I can get to the servers from other OS's but I can't get to them under linux... what am I missing?  Could somebody poke around and see where my problem is?  

Any assistance is greatly appreciated!

Thanks in advance!

-Charles Read

---

### Post by mips on 2006-04-25
Can you ping the servers IP address ?

Are you on the same LAN as your servers ?

1. Please disable IPv6 and reboot:
```
sudo mv /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko.bak
sudo depmod -a
```
2. Please post output of **ifconfig eth0**
3. Please post output of **lspci | grep Eth**
4. Please post output of **route -n**
5. Please post output of **cat /etc/resolv.conf**
6. Please post output of **cat /etc/network/interfaces**

---

### Post by charlesread2006 on 2006-04-25
Not on the same lan...

Heres what pinging shows:

root@ubuntu:/home/charles# ping -c 3 charlesread.com
PING charlesread.com (207.145.0.8) 56(84) bytes of data.
From ip-207-145-0-6.atl.megapath.net (207.145.0.6) icmp_seq=1 Destination Host Unreachable
From ip-207-145-0-6.atl.megapath.net (207.145.0.6) icmp_seq=2 Destination Host Unreachable
From ip-207-145-0-6.atl.megapath.net (207.145.0.6) icmp_seq=3 Destination Host Unreachable

--- charlesread.com ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 1999ms
, pipe 3

heres ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:0F:B0:C1:91:C1
          inet addr:207.145.0.6  Bcast:207.145.0.15  Mask:255.255.255.240
          inet6 addr: fe80::20f:b0ff:fec1:91c1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6437 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6437 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:356059 (347.7 KiB)  TX bytes:356059 (347.7 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:14:A5:72:4F:0D
          inet addr:168.28.48.223  Bcast:168.28.48.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fe72:4f0d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1090 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1533354 (1.4 MiB)  TX bytes:146049 (142.6 KiB)
          Memory:c0200000-c0201fff

heres iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"Marut"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:01:F4:EC:3F:1F
          Bit Rate=11 Mb/s   Tx-Power:25 dBm
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-67 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

heres route -n:

root@ubuntu:/home/charles# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
207.145.0.0     0.0.0.0         255.255.255.240 U     0      0        0 eth0
168.28.48.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         168.28.48.1     0.0.0.0         UG    0      0        0 wlan0
0.0.0.0         207.145.0.1     0.0.0.0         UG    0      0        0 eth0

heres /etc/resolv.conf:

root@ubuntu:/home/charles# cat /etc/resolv.conf
search clayton.edu
nameserver 168.28.240.113
nameserver 168.28.240.114

heres /etc/network/interfaces:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet static
        address 207.145.0.6
        netmask 255.255.255.240
        network 207.145.0.0
        broadcast 207.145.0.15
        gateway 207.145.0.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 64.7.11.2
        dns-search atl.megapath.net

iface wlan0 inet dhcp
wireless-essid Read Family Base Station

auto eth0




I REALLY APPRECIATE IT!

-CHARLES READ

---

### Post by mips on 2006-04-25
Can you ping 207.145.0.6  &  207.145.0.1 ?

From the looks of things you have no traffic going through eth0. Try bringing the interface down & then back up again.

Where does the wireless work to ?

I'm confused. You say your PC is not on the same LAN but yet from the configs it looks like it is ???
knoppix@2[knoppix]$ ping charlesread.com
PING charlesread.com ( 207.145.0.8 )  : 56 data bytes
64 bytes from 207.145.0.8: icmp_seq=0 ttl=45 time=417.5 ms

Which puts your PC on the same LAN if it has an address of 207.145.0.6 ???

---

### Post by mips on 2006-05-02
Any feedback ?

---

