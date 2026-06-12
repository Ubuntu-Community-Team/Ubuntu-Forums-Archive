---
title: "which package contain network RE-connect?"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by jiunhsien on 2009-01-21
I did not install ubuntu in the normal way. I setup a base command line system.

If I turn on the ADSL first, the system will connect to the internet.
If I turn on the ADSL later, the system will not connect to the internet.

I guess: the base command line system did not know to RE-connect. 
I guess I miss RE-connect package. 
Could you tell me which one to install?
I want RE-connect to internet automatically.


```

#aptitude search network

i A libqt4-network                  - Qt 4 network module                       
p   education-networked             - DebianEdu networked minimal packages      
p   gnome-network-admin             - GNOME Network Administration Tool         
p   kdenetwork-dbg                  - debugging symbols for kdenetwork          
p   kdenetwork-dev                  - development files for the KDE network modu
p   kdenetwork-doc-html             - KDE network documentation in HTML format  
p   kdenetwork-filesharing          - network filesharing configuration module f
p   kdenetwork-kfile-plugins        - torrent metainfo plugin for KDE           
p   kdenetwork                      - network-related apps from the official KDE
p   knetworkconf                    - KDE network configuration tool            
p   libcapsinetwork0c2a             - C++ network server library                
p   libcapsinetwork-dev             - C++ network server library, development fi
p   libghc6-network-dev             - Haskell network library for GHC           
p   libghc6-network-doc             - Haskell network library for GHC; documenta
p   libghc6-network-prof            - Haskell network library for GHC; profiling
p   libgnetwork1.0-0                - networking wrapper library using Glib/GObj
p   libgnetwork1.0-dev              - networking wrapper library using Glib/GObj
p   libhugs-network-bundled         - Networking-related facilities             
p   libnetwork-ipv4addr-perl        - Perl extension for manipulating IPv4 addre
p   libsfml-network1.deb3           - Simple and fast cross-platform multimedia 
p   network-config                  - Simple network configuration tool         
p   network-manager-dev             - network management framework (development 
p   network-manager-gnome           - network management framework (GNOME fronte
p   network-manager-kde             - KDE systray applet for controlling Network
p   network-manager                 - network management framework daemon       
p   network-manager-openvpn-gnome   - network management framework (OpenVPN plug
p   network-manager-openvpn         - network management framework (OpenVPN plug
p   network-manager-pptp-gnome      - network management framework (PPTP plugin)
p   network-manager-pptp            - network management framework (PPTP plugin)
p   network-manager-vpnc-gnome      - network management framework (VPNC plugin 
p   network-manager-vpnc            - network management framework (VPNC plugin 
p   networkstatus                   - KDE network status monitor                
p   python-networkx                 - tool to manipulate and study more than com
v   knetworkmanager                 -                                           
v   libgnetwork-dev                 -                                           
v   libhugs-network                 -                                           

```

The "/etc/init.d/networking restart" still can't RE-connect.
At last, it RE-connect to internet by "ifdown/ifup"

```
root:~# ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:0b:0c:0b:07:0d  
          inet6 addr: fe80::21b:fcff:feeb:17dd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:838 (838.0 B)
          Interrupt:220 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

root:~# /etc/init.d/networking restart
Reconfiguring network interfaces...There is already a pid file /var/run/dhclient.eth0.pid with pid 2199
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0b:0c:0b:07:0d
Sending on   LPF/eth0/00:0b:0c:0b:07:0d
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
done.
root:~# ifdown eth0
ifdown: interface eth0 not configured
root:~# ifup eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0b:0c:0b:07:0d
Sending on   LPF/eth0/00:0b:0c:0b:07:0d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.12 -- renewal in 106849 seconds.

```

---

