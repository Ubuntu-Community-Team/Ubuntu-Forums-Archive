---
title: "Unable to Connect to DHCP Network"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by PerfectReign on 2009-09-08
I searched and did not find a like answer. I'm not sure if the issue is my network card/software or the router or the Active Directory server.

Here's what's going on.

I have a laptop running Ubuntu 9.04 with GNOME. I use network manager to setup my network, which is either wired (at work) or wireless (at home). At home, I have no issues connecting to my WPA password-protected hidden-ssid network.

At work, I cannot seem to connect, however. 

The laptop is two years old, has some broadcom wired Ethernet chip and more-or-less works. I originally had openSUSE 11.0 on the system and had similar issues with KNetworkManger. The DHCP lease would mostly work, then eventually not. (In fact, this is one of the reasons I switched to Ubunutu.) 

When I moved over to Ubunutu, I would regularly get a DHCP lease and have no issues connecting to the internet (over a bluecoat proxy) or network resources. 

More recently, however, I've been noticing that I'm often unable to grab a lease and - even when I do - get out to network resources.

What I'd typically do in the situation where I cannot connect is run dhclient. This had solved my problem in the past. Annoying, but workable.

Now - even when running dhclient, I get no valid response. Or rather, it seems I'd occasionally get a 192.16.x.x address or I get a valid address in my LAN but am unable to connect to machines outside of my immediate office. I have two Windows desktops in my office - one XP and one Vista. I can easily connect to either of those using SMB or http. However, I cannot access any network resources or other servers.

What could be going on?  I'll post ifconfig, dhclient and lshw information in subsequent posts.

---

### Post by PerfectReign on 2009-09-08
Here is the ifconfig output from my system when I've successfully conneted to the LAN. I still - however - cannot access computers elsewhere in the building outside of my immediate office.

   [FONT=Courier New][COLOR=Blue]kai@r2d2:~$ /sbin/ifconfig -a[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]eth0      Link encap:Ethernet  HWaddr 00:16:d4:a7:6d:64  [/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          inet addr:10.166.135.61  Bcast:10.1.135.255  Mask:255.255.255.0[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          inet6 addr: fe80::216:d4ff:fea7:6d64/64 Scope:Link[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          RX packets:89 errors:0 dropped:0 overruns:0 frame:0[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          collisions:0 txqueuelen:1000 [/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          RX bytes:8287 (8.2 KB)  TX bytes:10143 (10.1 KB)[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          Interrupt:16 [/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue] [/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]lo        Link encap:Local Loopback  [/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          inet addr:127.0.0.1  Mask:255.0.0.0[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          inet6 addr: ::1/128 Scope:Host[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          RX packets:228 errors:0 dropped:0 overruns:0 frame:0[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          TX packets:228 errors:0 dropped:0 overruns:0 carrier:0[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          collisions:0 txqueuelen:0 [/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          RX bytes:18289 (18.2 KB)  TX bytes:18289 (18.2 KB)[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue] [/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]pan0      Link encap:Ethernet  HWaddr a2:c8:e3:de:88:47  [/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          inet6 addr: fe80::a0c8:e3ff:fede:8847/64 Scope:Link[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          collisions:0 txqueuelen:0 [/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          RX bytes:0 (0.0 B)  TX bytes:3204 (3.2 KB)[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue] [/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  [/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          inet6 addr: fe80::800:27ff:fe00:0/64 Scope:Link[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          collisions:0 txqueuelen:1000 [/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          RX bytes:0 (0.0 B)  TX bytes:3204 (3.2 KB)[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue] [/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  [/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          inet addr:192.168.52.129  Bcast:192.168.52.255  Mask:255.255.255.0[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          RX packets:9 errors:0 dropped:0 overruns:0 frame:0[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          TX packets:330 errors:0 dropped:0 overruns:0 carrier:0[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          collisions:0 txqueuelen:1000 [/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue] [/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  [/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          RX packets:16 errors:0 dropped:0 overruns:0 frame:0[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          TX packets:153 errors:0 dropped:0 overruns:0 carrier:0[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          collisions:0 txqueuelen:1000 [/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue] [/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]wlan0     Link encap:Ethernet  HWaddr 00:19:d2:d3:42:e1  [/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          UP BROADCAST MULTICAST  MTU:1500  Metric:1[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          collisions:0 txqueuelen:1000 [/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue] [/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]wmaster0  Link encap:UNSPEC  HWaddr 00-19-D2-D3-42-E1-00-00-00-00-00-00-00-00-00-00  [/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          collisions:0 txqueuelen:1000 [/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/COLOR][/FONT]

---

### Post by PerfectReign on 2009-09-08
Here is the output from lshw...


   [FONT=Courier New][COLOR=Blue]kai@r2d2:~$ sudo lshw -C network[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]  *-network               [/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       description: Ethernet interface[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       product: NetXtreme BCM5753M Gigabit Ethernet PCI Express[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       vendor: Broadcom Corporation[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       physical id: 0[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       bus info: pci@0000:08:00.0[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       logical name: eth0[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       version: 21[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       serial: 00:16:d4:a7:6d:64[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       size: 1GB/s[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       capacity: 1GB/s[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       width: 64 bits[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       clock: 33MHz[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5753m-v3.56 ip=10.1.135.61 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=1GB/s[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]  *-network[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       description: Wireless interface[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       product: PRO/Wireless 3945ABG [Golan] Network Connection[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       vendor: Intel Corporation[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       physical id: 0[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       bus info: pci@0000:10:00.0[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       logical name: wmaster0[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       version: 02[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       serial: 00:19:d2:d3:42:e1[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       width: 32 bits[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       clock: 33MHz[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]  *-network:0[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       description: Ethernet interface[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       physical id: 1[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       logical name: vboxnet0[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       serial: 0a:00:27:00:00:00[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       capabilities: ethernet physical[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       configuration: broadcast=yes multicast=yes[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]  *-network:1[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       description: Ethernet interface[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       physical id: 2[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       logical name: pan0[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       serial: a2:c8:e3:de:88:47[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       capabilities: ethernet physical[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes[/COLOR][/FONT]
    [FONT=Courier New][COLOR=Blue]kai@r2d2:~$ [/COLOR][/FONT]

---

### Post by PerfectReign on 2009-09-08
Here is the output from dhclient when it gives me a 192.168.x.x ip address. I re-run a few times and I finally get a 10.1.135.x address.


   [FONT=Courier New][COLOR=Blue]kai@r2d2:~$ sudo dhclient[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]There is already a pid file /var/run/dhclient.pid with pid 5486[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]killed old client process, removed PID file[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]Internet Systems Consortium DHCP Client V3.1.1[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]Copyright 2004-2008 Internet Systems Consortium.[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]All rights reserved.[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue] [/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]wmaster0: unknown hardware address type 801[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]/etc/dhcp3/dhclient.conf line 26: no option named rfc3442-classless-static-routes in space dhcp[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]                rfc3442-classless-static-routes,[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]        ^[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]/etc/dhcp3/dhclient.conf line 26: ntp-servers: expected option name.[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]                rfc3442-classless-static-routes, ntp-servers;[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]                                                     ^[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]wmaster0: unknown hardware address type 801[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]Listening on LPF/pan0/36:63:20:f6:a1:ad[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]Sending on   LPF/pan0/36:63:20:f6:a1:ad[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]Listening on LPF/vboxnet0/0a:00:27:00:00:00[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]Sending on   LPF/vboxnet0/0a:00:27:00:00:00[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]Listening on LPF/vmnet8/00:50:56:c0:00:08[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]Sending on   LPF/vmnet8/00:50:56:c0:00:08[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]Listening on LPF/wlan0/00:19:d2:d3:42:e1[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]Sending on   LPF/wlan0/00:19:d2:d3:42:e1[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]Listening on LPF/wmaster0/[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]Sending on   LPF/wmaster0/[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]Listening on LPF/vmnet1/00:50:56:c0:00:01[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]Sending on   LPF/vmnet1/00:50:56:c0:00:01[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]Listening on LPF/eth0/00:16:d4:a7:6d:64[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]Sending on   LPF/eth0/00:16:d4:a7:6d:64[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]Sending on   Socket/fallback[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 6[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]DHCPDISCOVER on vboxnet0 to 255.255.255.255 port 67 interval 8[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]DHCPDISCOVER on vmnet8 to 255.255.255.255 port 67 interval 7[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]DHCPREQUEST of 192.168.0.101 on wlan0 to 255.255.255.255 port 67[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]DHCPOFFER of 192.168.112.129 from 192.168.112.254[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]DHCPREQUEST of 192.168.112.129 on vmnet8 to 255.255.255.255 port 67[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]DHCPACK of 192.168.112.129 from 192.168.112.254[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]resolvconf: Error: /etc/resolv.conf must be a symlink[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]resolvconf: Error: /etc/resolv.conf must be a symlink[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]Continuing at dhclient3,wired,lan[/COLOR][/FONT]
  [FONT=Courier New][COLOR=Blue]bound to 192.168.112.129 -- renewal in 800 seconds.[/COLOR][/FONT]

---

### Post by Iowan on 2009-09-08
> **PerfectReign said:**
>    [FONT=Courier New][COLOR=Blue]kai@r2d2:~$ /sbin/ifconfig -a
  eth0      Link encap:Ethernet  HWaddr 00:16:d4:a7:6d:64 
            inet addr:[COLOR="Red"]10.166.135.61[/COLOR]  Bcast:[COLOR="Red"]10.1.135.255[/COLOR]  Mask:[COLOR="Red"]255.255.255.0[/COLOR]
            inet6 addr: fe80::216:d4ff:fea7:6d64/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:89 errors:0 dropped:0 overruns:0 frame:0[
            TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 [/COLOR][/FONT]
  This looks like a problem - unless there was a typo in posting the information, the broadcast address is outside the subnet.
Have you edited /etc/dhcp3/dhclient.conf line 26 to get rid of the errors? (Post it if you'd like...

---

### Post by PerfectReign on 2009-09-08
> **Iowan said:**
> This looks like a problem - unless there was a typo in posting the information, the broadcast address is outside the subnet.
Have you edited /etc/dhcp3/dhclient.conf line 26 to get rid of the errors? (Post it if you'd like...

Sorry, my bad. I posted that trying to get rid of the .166 and change it to .1 for the post.


[SIZE=2]Here it is right now:
[/SIZE][FONT=Courier New][SIZE=2][COLOR=Blue]
[/COLOR][/SIZE][/FONT]    [FONT=Courier New][SIZE=2][COLOR=Blue]kai@r2d2:~$ /sbin/ifconfig eth0[/COLOR][/SIZE][/FONT]
    [FONT=Courier New][SIZE=2][COLOR=Blue]eth0      Link encap:Ethernet  HWaddr 00:16:d4:a7:6d:64  [/COLOR][/SIZE][/FONT]
    [FONT=Courier New][SIZE=2][COLOR=Blue]          inet addr:10.166.135.61  Bcast:10.166.135.255  Mask:255.255.255.0[/COLOR][/SIZE][/FONT]
    [FONT=Courier New][SIZE=2][COLOR=Blue]          inet6 addr: fe80::216:d4ff:fea7:6d64/64 Scope:Link[/COLOR][/SIZE][/FONT]
    [FONT=Courier New][SIZE=2][COLOR=Blue]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/COLOR][/SIZE][/FONT]
    [FONT=Courier New][SIZE=2][COLOR=Blue]          RX packets:9677 errors:0 dropped:0 overruns:0 frame:0[/COLOR][/SIZE][/FONT]
    [FONT=Courier New][SIZE=2][COLOR=Blue]          TX packets:162 errors:0 dropped:0 overruns:0 carrier:0[/COLOR][/SIZE][/FONT]
    [FONT=Courier New][SIZE=2][COLOR=Blue]          collisions:0 txqueuelen:1000 [/COLOR][/SIZE][/FONT]
    [FONT=Courier New][SIZE=2][COLOR=Blue]          RX bytes:937916 (937.9 KB)  TX bytes:19021 (19.0 KB)[/COLOR][/SIZE][/FONT]
    [FONT=Courier New][SIZE=2][COLOR=Blue]          Interrupt:16 [/COLOR][/SIZE][/FONT]
  
  [SIZE=2]

Line 26?  I have line 16 commented out:

[/SIZE]    [FONT=Courier New][SIZE=2][COLOR=Blue]# kp20090827 - commented out per[/COLOR][/SIZE][/FONT]
    [FONT=Courier New][SIZE=2][COLOR=Blue]# [http://ubuntuforums.org/showthread.php?t=1156441](http://ubuntuforums.org/showthread.php?t=1156441)[/COLOR][/SIZE][/FONT]
    [FONT=Courier New][SIZE=2][COLOR=Blue]# option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;[/COLOR][/SIZE][/FONT]
[FONT=Courier New][SIZE=2][COLOR=Blue]send host-name "<hostname>";[/COLOR][/SIZE][/FONT]    [FONT=Courier New][SIZE=2][COLOR=Blue]#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;[/COLOR][/SIZE][/FONT]
    [FONT=Courier New][SIZE=2][COLOR=Blue]#send dhcp-lease-time 3600;[/COLOR][/SIZE][/FONT]
    [FONT=Courier New][SIZE=2][COLOR=Blue]#supersede domain-name "fugue.com home.vix.com";[/COLOR][/SIZE][/FONT]
    [FONT=Courier New][SIZE=2][COLOR=Blue]#prepend domain-name-servers 127.0.0.1;[/COLOR][/SIZE][/FONT]
    [FONT=Courier New][SIZE=2][COLOR=Blue]request subnet-mask, broadcast-address, time-offset, routers,[/COLOR][/SIZE][/FONT]
    [FONT=Courier New][SIZE=2][COLOR=Blue]                domain-name, domain-name-servers, domain-search, host-name,[/COLOR][/SIZE][/FONT]
    [FONT=Courier New][SIZE=2][COLOR=Blue]                netbios-name-servers, netbios-scope, interface-mtu,[/COLOR][/SIZE][/FONT]
    [FONT=Courier New][SIZE=2][COLOR=Blue]                rfc3442-classless-static-routes, ntp-servers;[/COLOR][/SIZE][/FONT]
    [FONT=Courier New][SIZE=2][COLOR=Blue]#require subnet-mask, domain-name-servers;[/COLOR][/SIZE][/FONT]
    [FONT=Courier New][SIZE=2][COLOR=Blue]#timeout 60;[/COLOR][/SIZE][/FONT]
    [FONT=Courier New][SIZE=2][COLOR=Blue]#retry 60;[/COLOR][/SIZE][/FONT]
    [FONT=Courier New][SIZE=2][COLOR=Blue]#reboot 10;[/COLOR][/SIZE][/FONT]
    [FONT=Courier New][SIZE=2][COLOR=Blue]#select-timeout 5;[/COLOR][/SIZE][/FONT]
    [FONT=Courier New][SIZE=2][COLOR=Blue]#initial-interval 2;[/COLOR][/SIZE][/FONT]
  [COLOR=Blue]

[/COLOR]

---

### Post by PerfectReign on 2009-09-08
Okay, figured it out.

Turns out that one line (which I had previously commented out) was a definition line and the other was a implementation. I commented out the second line. There was some goofy line breaks making the lines more than they should be. There was an updated thread which I hadn't read: [http://ubuntuforums.org/showthread.php?p=7276275#post7276275](http://ubuntuforums.org/showthread.php?p=7276275#post7276275)

This has teh answer.

I'm all good now.

I'll check tomorrow when I plug my laptop  back in.

The lines now read:

[FONT=Courier New][COLOR=Blue]# kp20090827 - commented out per
# [http://ubuntuforums.org/showthread.php?t=1156441](http://ubuntuforums.org/showthread.php?t=1156441)
# option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
# kp20090908 - commented out.
# request subnet-mask, broadcast-address, time-offset, routers, domain-name, domain-name-servers, domain-search, host-name, netbios-name-servers, netbios-scope, interface-mtu, rfc3442-classless-static-routes, ntp-servers;

[/COLOR][/FONT]

---

### Post by Iowan on 2009-09-08
If you comment out that line, you'll need to modify this line:```
 rfc3442-classless-static-routes, ntp-servers;
```If you want to keep a copy, duplicate it and comment it:```
 #rfc3442-classless-static-routes, ntp-servers;
 ntp-servers;
```You will probably need some of the other information in that "request" line.


Hmmm... you seem to have found the solution whilst I was typing... glad you fixed it!

---

### Post by PerfectReign on 2009-09-09
Okay, very cool. I think I've got it then. I'll fire it up in the AM at work and see what happens. 

Like usual, I had no issues connecting to my home net this afternoon. Both my Ubuntu machines and my wife's Vista machine seem to live in perfect harmony.

---

### Post by PerfectReign on 2009-09-09
Okay, no luck.

I turned on the system, and was given a bogus IP address:
[FONT=Courier New][COLOR=Blue]
kai@r2d2:~$ /sbin/ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:16:d4:a7:6d:64  
          inet addr:159.83.251.99  Bcast:159.83.251.127  Mask:255.255.255.192
          inet6 addr: fe80::216:d4ff:fea7:6d64/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:142 errors:0 dropped:0 overruns:0 frame:0
          TX packets:209 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12063 (12.0 KB)  TX bytes:17195 (17.1 KB)
          Interrupt:16 [/COLOR][/FONT]
Running dhclient gave me an appropriate address. However, why does it say 
/etc/resolf.conf must be a symlink?

[FONT=Courier New][COLOR=Blue]kai@r2d2:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:16:d4:a7:6d:64
Sending on   LPF/eth0/00:16:d4:a7:6d:64
Sending on   Socket/fallback
DHCPREQUEST of 10.166.135.61 on eth0 to 255.255.255.255 port 67
DHCPACK of 10.166.135.61 from 10.166.135.2
resolvconf: Error: /etc/resolv.conf must be a symlink
Terminated
kai@r2d2:~$ resolvconf: Error: /etc/resolv.conf must be a symlink
Moving from netstart to dhclient3,wired,lan[/COLOR][/FONT]

---

### Post by Iowan on 2009-09-09
> **PerfectReign said:**
>  However, why does it say /etc/resolf.conf must be a symlink?
I'm still looking for an answer to that one...
I presume your */etc/network/interfaces* file has only configuration information for "lo"?

---

### Post by PerfectReign on 2009-09-09
Never even knew about that file...

[FONT=Courier New][COLOR=Blue]auto lo
iface lo inet loopback[/COLOR][/FONT]

---

### Post by Iowan on 2009-09-10
Found [this]("http://n0b3l1a.blogspot.com/2009/02/resolvconf-error-etcresolvconf-must-be.html").
[Another]("http://ubuntuforums.org/showthread.php?t=88525") one.
[Bug report]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/324233").
[One more]("http://whatdoesthiserrormean.com/errors/2838").

In fact, searching for "resolvconf: Error: /etc/resolv.conf must be a symlink" yielded several possible links.

---

