---
title: "No internet with DHCP"
date: 2006-05-22
forum: Networking &amp; Wireless
---

### Post by waffen on 2006-05-22
Hi,

I power off my laptop Compaq Presario 1700 and when I restart it, the internet connection not works.

I follow the instructions in this thread: 
[http://www.ubuntuforums.org/showthread.php?t=171694&highlight=error+dhcp]("http://www.ubuntuforums.org/showthread.php?t=171694&highlight=error+dhcp")

and post the results:

```

mario@laptop2:~$ cat /etc/network/interfaces
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
iface eth0 inet dhcp
auto eth0

=========================================================================

mario@laptop2:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:8B:AA:BA:46
          inet6 addr: fe80::250:8bff:feaa:ba46/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:13 dropped:0 overruns:0 carrier:29
          collisions:0 txqueuelen:1000
          RX bytes:364546 (356.0 KiB)  TX bytes:2430 (2.3 KiB)
          Interrupt:9 Base address:0x1400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12190 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12190 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1945344 (1.8 MiB)  TX bytes:1945344 (1.8 MiB)

=========================================================================

mario@laptop2:~$ sudo mii-tool
eth0: negotiated 100baseTx-FD, link ok

mario@laptop2:~$ ping 62.69.184.231
connect: Network is unreachable

mario@laptop2:~$ ping www.nu.nl
ping: unknown host www.nu.nl


```

When I click in the icon of red in the taskbar, the tab Support dont show the Internet Protocol IPv4 ....

Any idea???

Thanks!!

My config is Ubuntu Breezy 5.10 up to date ...

And I use a DHCP connection with a Navini modem conected to Satra swicth, in other swicth port I have a Thinkpad 600X laptop with Ubuntu Breezy and its works fine.

---

### Post by XAsmodeanX on 2006-05-30
Try looking in /etc and open the file resolv.conf and make sure that your nameservers are correct.  Some routers give a bogus nameserver (which is in fact the IP of the router) and that will hose things up.  If you see an ip that is your router then erase that line and save the file.  But remember, every time you get a new lease from the router it'll put that line back as your nameserver.

---

### Post by kh4nh on 2006-05-30
"eth0      Link encap:Ethernet  HWaddr 00:50:8B:AA:BA:46
          inet6 addr: fe80::250:8bff:feaa:ba46/64 Scope:Link"
I think you have ipv6 issue, disable it [https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4?highlight=%28ipv6%29]("https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4?highlight=%28ipv6%29")

---

