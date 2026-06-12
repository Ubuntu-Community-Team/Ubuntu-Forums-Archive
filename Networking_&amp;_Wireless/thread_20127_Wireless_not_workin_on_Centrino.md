---
title: "Wireless not workin on Centrino"
date: 2005-03-15
forum: Networking &amp; Wireless
---

### Post by lerrup on 2005-03-15
I have just installed the preview release on my samsung, centrino based laptop, and the wlan is not working.

Both warty and previous hoary releases and handled it without a sweat and so I am very confused about this - it would not install via wireless and so I am worried that it is something fairly fundamental.

I have also replaced etc/network/interfaces with my previous, working hoary file and it still doesn't want to know.

I realise from the forums that I am not alone, but has anyone out there found a reason for this, or even better a solution?

Running iwconfig gives:

lo no wireless extensions.

eth0 no wireless extensions.

eth1 unassociated ESSID:"home network"
Mode:Managed Channel=0 Access Point: 00:00:00:00:00:00
Bit Rate=0 kb/s Tx-Power=20 dBm
RTS thr:off Fragment thr:off
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sit0 no wireless extensions.

Any ideas about this?

---

### Post by alastair on 2005-03-15
Well, the driver's loaded and seems to give you a decent wireless interface "eth1". I guess the problem is justt getting it to "associate" with your AP.

What is the relevant interfaces file section? 
Do you use DHCP?
What is printed in the log file /var/log/syslog when the setup is attempted?

---

### Post by lerrup on 2005-03-15
My interfaces file is as follows:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth1

# The primary network interface
iface eth1 inet dhcp
# wireless-* options are implemented by the wireless-tools package
wireless-mode managed
wireless-essid any
wireless_essid blooming hopeless

auto eth1

iface eth0 inet dhcp

auto eth0


I do use DHCP, but maybe not for long.

/var/log/sys looks like this:

Mar 15 20:36:27 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Mar 15 20:36:34 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Mar 15 20:36:42 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Mar 15 20:36:49 localhost dhclient: No DHCPOFFERS received.
Mar 15 20:36:49 localhost dhclient: No working leases in persistent database - sleeping.
Mar 15 20:37:29 localhost kernel: ACPI: acpi_ec_space_handler: bit_width should be 8
Mar 15 20:37:29 localhost last message repeated 9 times
Mar 15 20:38:29 localhost last message repeated 9 times
Mar 15 20:39:29 localhost last message repeated 10 times
Mar 15 20:40:29 localhost last message repeated 9 times

---

### Post by alastair on 2005-03-15
This is a pain sometimes - and hard to diagnose remotely. I have centrino (ipw2100/thinkpad) and things work OK generally though.

You have the device - good.
It is up and seems to be working - good.

You are almost there.

Is the ESSID broadcast?
Do you know the AP's MAC address?

Perhaps try a manual config i.e.

iwconfig eth1 ap <AP MAC>
iwconfig eth1 key restricted <KEY>

Perhaps try a static IP address?

Check using iwconfig and ifconfig.

---

### Post by lerrup on 2005-03-16
Thanks, I'll try what you suggest.

ifconfig gives:

eth0      Link encap:Ethernet  HWaddr 00:00:F0:89:A3:ED
          inet addr:192.168.123.192  Bcast:192.168.123.255  Mask:255.255.255.0
          inet6 addr: fe80::200:f0ff:fe89:a3ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14555 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34138 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:18740975 (17.8 MiB)  TX bytes:2380207 (2.2 MiB)
          Interrupt:10

eth1      Link encap:Ethernet  HWaddr 00:0E:35:1E:F1:9F
          inet6 addr: fe80::20e:35ff:fe1e:f19f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24091 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10621 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0x6000 Memory:d0002000-d0002fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

---

### Post by lerrup on 2005-03-21
I have managed to solve this.  

In the end I reinstalled the whole system, but I had to reset my router to its defaults and then it worked.  I know have a system with some security, well WEP, and a unique, ESSID.

Excellent, but no I don't understand.

---

