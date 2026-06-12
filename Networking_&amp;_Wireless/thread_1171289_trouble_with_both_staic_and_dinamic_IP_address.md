---
title: "trouble with both staic and dinamic IP address"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by sliver99 on 2009-05-27
HI all,
In my nb i´ve a dual boot ubuntu 8.04.2 with vista.
Under vista networking is working fine$.
Ubuntu can´t get in no way an IP address from the router. I´ve tried both dhcp or static (using vista address) but i can´t ping default gateway.

It´s 1 week i read old post in this forum but i can´t find any working solution.

here´s what i´ve done (Starting using static address)

```
me@ubuntu ~ $ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.2.32
netmask 255.255.255.0
gateway 192.168.2.1

me@ubuntu ~ $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:92:bc:02:be  
          inet addr:192.168.2.32  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10161 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10161 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:577428 (563.8 KB)  TX bytes:577428 (563.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:c5:06:6d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-C5-06-6D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

me@ubuntu ~ $ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.2.1     0.0.$0.0         UG    100    0        0 eth0
```

I ping degault gateway but i get host unreachble.

so I switch configuration using network manager. I set up dhcp and i get:

> me@ubuntu ~ $ sudo /etc/init.d/networking restart
[sudo] password for me: 
 * Reconfiguring network interfaces...                                                                                                                       There is already a pid file /var/run/dhclient.eth0.pid with pid 12439
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:1a:92:bc:02:be
Sending on   LPF/eth0/00:1a:92:bc:02:be
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.178.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:1a:92:bc:02:be
Sending on   LPF/eth0/00:1a:92:bc:02:be
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                                                                                                      [ OK ]
me@ubuntu ~ $ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:1a:92:bc:02:be  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 Base address:0x6000 

me@ubuntu ~ $ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0
me@ubuntu ~ $ 


I ping the df gw and i get the same result.

does anyone have any idea or can point me in the right direction to solve this issue?

PS: If it´s important, i have uninstalled apache2 and vmware on my nb. I currently have virtualbox.

thanks anyone

---

### Post by albinootje on 2009-05-27
> **sliver99 said:**
> 
Ubuntu can´t get in no way an IP address from the router. 

Please post the output of the following :
```

lspci
lshw -C network

```
Some network cards need to have different settings in MS-Windows concerning wake-on-lan, before the NIC can work in Linux. (Sad, but true).

---

### Post by sliver99 on 2009-05-27
> **albinootje said:**
> Please post the output of the following :
```

lspci
lshw -C network

```
Some network cards need to have different settings in MS-Windows concerning wake-on-lan, before the NIC can work in Linux. (Sad, but true).

Thanks for your answer.
Here the output:
> 
me@ubuntu ~ $ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
06:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
06:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
06:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
me@ubuntu ~ $ lshw -C network
WARNING: you should run this program as super-user.
me@ubuntu ~ $ sudo lshw -C network
[sudo] password for me: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1a:92:bc:02:be
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:c5:06:6d
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 00:76:62:6e:65:74
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

---

### Post by albinootje on 2009-05-27
Thanks for the output, see here :

[http://wiki.archlinux.org/index.php/Configuring_network#Realtek_No_Link_.2F_WOL_issue](http://wiki.archlinux.org/index.php/Configuring_network#Realtek_No_Link_.2F_WOL_issue)

Try method 2.

---

### Post by superprash2003 on 2009-05-27
post contents of /etc/dhcp3/dhclient.conf

---

### Post by sliver99 on 2009-05-27
@albinootje

I´ve tried the ´unclean shutdown workaround´ as i´ve vista with a new driver but nothing changes.

@superprash2003

here below my /etc/dhcp3/dhclient.conf

please note that i´ve tried some days ago to use

> send host-name "ubuntu";

instead of

> send host-name "<hostname>";

> # Configuration file for /sbin/dhclient, which is included in Debian's
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

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
timeout 30;
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
prepend domain-name-servers 208.67.222.222,208.67.220.220;


---

### Post by Iowan on 2009-05-27
Back in the first post, it appeared that eth0 had an IP address. I presume the "$" in genmask was a typo of some sort.  Pinging gateway by name or address? If name, try address - if that works, check */etc/resolv.conf*.

---

### Post by sliver99 on 2009-05-27
> **Iowan said:**
> Back in the first post, it appeared that eth0 had an IP address. I presume the "$" in genmask was a typo of some sort.  Pinging gateway by name or address? If name, try address - if that works, check */etc/resolv.conf*.

I've not understood what are you referring to, i've copied and pasted the output. Anyway I ping using the IP address, i.e:

> sudo ping 192.168.2.1

i get destination unreachable.


here my resolv.conf
> 
nameserver 208.67.222.222
nameserver 208.67.222.220

---

### Post by Iowan on 2009-05-27
You answered the questions I asked... though I'm still a bit confused as to the state of your machine  - what are current results of **ifconfig -a** and current contents of */etc/network/interfaces*?  Initial post had IP address of 192.168.2.32 for eth0, later results showed eth0 with no address.

---

### Post by albinootje on 2009-05-27
> **Iowan said:**
> Initial post had IP address of 192.168.2.32 for eth0, later results showed eth0 with no address.

That would make sense after trying dhclient, no dhcp offers, no ip address.

I would be much more interested in the output (screenshot) of "ipconfig /all" from the MS-Windows partition. Can the OP please provide that, as well as a screenshot of the wake-on-lan NIC settings in MS-Windows.

---

### Post by sliver99 on 2009-05-28
Yesterday night i´ve tried to connect using a friend of mine connection at his house, i´$ve only runned after boot:

> sudo /etc/init.d/networking restart

and i get quikly the address. This morning i´m returned @ my home but i´ve still my problems.No way to get the address. i´ve also tried to change the cable but still networking didn´t work.

> **albinootje said:**
> That would make sense after trying dhclient, no dhcp offers, no ip address.

Yes, in my first post i´ve started using static address then switched to dhcp. NOW i´m still using dhcp.

> **albinootje said:**
> I would be much more interested in the output (screenshot) of "ipconfig /all" from the MS-Windows partition. Can the OP please provide that, as well as a screenshot of the wake-on-lan NIC settings in MS-Windows.

I hope italian isn´t a problem:
ipconfig /all on vista32:
> Microsoft Windows [Versione 6.0.6001]
Copyright (c) 2006 Microsoft Corporation. Tutti i diritti riservati.

C:\Users\frz>ipconfig /all

Configurazione IP di Windows

   Nome host . . . . . . . . . . . . . . : fraz
   Suffisso DNS primario . . . . . . . . :
   Tipo nodo . . . . . . . . . . . . . . : Ibrido
   Routing IP abilitato. . . . . . . . . : No
   Proxy WINS abilitato . . . . . . . .  : No

Scheda Ethernet Connessione di rete Bluetooth:

   Stato supporto. . . . . . . . . . . . : Supporto disconnesso
   Suffisso DNS specifico per connessione:
   Descrizione . . . . . . . . . . . . . : Dispositivo Bluetooth (Personal Area
Network)
   Indirizzo fisico. . . . . . . . . . . : 00-1A-92-7A-7A-13
   DHCP abilitato. . . . . . . . . . . . : Sì
   Configurazione automatica abilitata   : Sì

Scheda LAN wireless Connessione rete wireless:

   Stato supporto. . . . . . . . . . . . : Supporto disconnesso
   Suffisso DNS specifico per connessione:
   Descrizione . . . . . . . . . . . . . : Intel(R) PRO/Wireless 3945ABG Networ
 Connection
   Indirizzo fisico. . . . . . . . . . . : 00-18-DE-C5-06-6D
   DHCP abilitato. . . . . . . . . . . . : Sì
   Configurazione automatica abilitata   : Sì

Scheda Ethernet Connessione alla rete locale (LAN):

   Suffisso DNS specifico per connessione:
   Descrizione . . . . . . . . . . . . . : Realtek RTL8168/8111 Family PCI-E Gi
abit Ethernet NIC (NDIS 6.0)
   Indirizzo fisico. . . . . . . . . . . : 00-1A-92-BC-02-BE
   DHCP abilitato. . . . . . . . . . . . : Sì
   Configurazione automatica abilitata   : Sì
   Indirizzo IPv6 locale rispetto al collegamento . : fe80::15f9:6db0:359d:8c2b
8(Preferenziale)
   Indirizzo IPv4. . . . . . . . . . . . : 192.168.2.34(Preferenziale)
   Subnet mask . . . . . . . . . . . . . : 255.255.255.0
   Lease ottenuto. . . . . . . . . . . . : giovedì 28 maggio 2009 9.58.22
   Scadenza lease . . . . . . . . . . .  : venerdì 29 maggio 2009 9.58.22
   Gateway predefinito . . . . . . . . . : 192.168.2.1
   Server DHCP . . . . . . . . . . . . . : 192.168.2.1
   Server DNS . . . . . . . . . . . . .  : 208.67.222.222
                                           208.67.220.220
   NetBIOS su TCP/IP . . . . . . . . . . : Attivato

Scheda Tunnel Connessione alla rete locale (LAN)* 6:

   Stato supporto. . . . . . . . . . . . : Supporto disconnesso
   Suffisso DNS specifico per connessione:
   Descrizione . . . . . . . . . . . . . : isatap.{9B4FB82A-9C0A-48D3-A048-18DE
37DCF5B}
   Indirizzo fisico. . . . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP abilitato. . . . . . . . . . . . : No
   Configurazione automatica abilitata   : Sì

Scheda Tunnel Connessione alla rete locale (LAN)* 7:

   Suffisso DNS specifico per connessione:
   Descrizione . . . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Indirizzo fisico. . . . . . . . . . . : 02-00-54-55-4E-01
   DHCP abilitato. . . . . . . . . . . . : No
   Configurazione automatica abilitata   : Sì
   Indirizzo IPv6 . . . . . . . . . . . . . . . . . : 2001:0:d5c7:a2d6:20aa:494
af78:3e04(Preferenziale)
   Indirizzo IPv6 locale rispetto al collegamento . : fe80::20aa:494:af78:3e04%
2(Preferenziale)
   Gateway predefinito . . . . . . . . . : ::
   NetBIOS su TCP/IP . . . . . . . . . . : Disattivato

Scheda Tunnel Connessione alla rete locale (LAN)* 10:

   Stato supporto. . . . . . . . . . . . : Supporto disconnesso
   Suffisso DNS specifico per connessione:
   Descrizione . . . . . . . . . . . . . : isatap.{B9C24F49-0942-46A5-A32F-4AD2
D1331B5}
   Indirizzo fisico. . . . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP abilitato. . . . . . . . . . . . : No
   Configurazione automatica abilitata   : Sì

Scheda Tunnel Connessione alla rete locale (LAN)* 11:

   Stato supporto. . . . . . . . . . . . : Supporto disconnesso
   Suffisso DNS specifico per connessione:
   Descrizione . . . . . . . . . . . . . : isatap.{AA9F1F98-6FFA-4485-829E-9677
7CD3B41}
   Indirizzo fisico. . . . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP abilitato. . . . . . . . . . . . : No
   Configurazione automatica abilitata   : Sì

Scheda Tunnel Connessione alla rete locale (LAN)* 12:

   Stato supporto. . . . . . . . . . . . : Supporto disconnesso
   Suffisso DNS specifico per connessione:
   Descrizione . . . . . . . . . . . . . : 6TO4 Adapter
   Indirizzo fisico. . . . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP abilitato. . . . . . . . . . . . : No
   Configurazione automatica abilitata   : Sì


and here the requested screenshot:
[http://img40.imageshack.us/img40/998/woltac.jpg](http://img40.imageshack.us/img40/998/woltac.jpg)
(abilitato means enabled)

As suggested in the link you posted i´ve tried to "perform an ungraceful restart/shutdown thus not giving the Windows driver a chance to disable LAN."

I don´t know if it´s usefull but here´s the output of nm-tool
> NetworkManager Tool

State: connected

- Device: wlan0 ----------------------------------------------------------------
  NM Path:           /org/freedesktop/NetworkManager/Devices/wlan0
  Type:              802.11 Wireless
  Driver:            iwl3945
  Active:            no
  HW Address:        00:18:DE:C5:06:6D

  Capabilities:
    Supported:       yes

  Wireless Settings
    Scanning:        yes
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Networks (* = Current Network)
...


Here´s also the other requested output:

ifconfig -a
> eth0      Link encap:Ethernet  HWaddr 00:1a:92:bc:02:be  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 

eth0:avahi Link encap:Ethernet  HWaddr 00:1a:92:bc:02:be  
          inet addr:169.254.7.49  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:219 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:232969 (227.5 KB)  TX bytes:232969 (227.5 KB)

vboxnet0  Link encap:Ethernet  HWaddr 00:76:62:6e:65:74  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:c5:06:6d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-C5-06-6D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


and /etc/network/interfaces
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

I´m still reading around forums but still i don´t find a way to understand if my ubuntu "knows" of "feel" when the cable is plugged (or if a cable is plugged).
Is there any way?
thank you again for your help.

---

### Post by albinootje on 2009-05-28
> **sliver99 said:**
> This morning i´m returned @ my home but i´ve still my problems.No way to get the address.

So, you took your laptop to a friend's place, and there it worked ?
Very good that you did this, it makes searching for the solution easier.

Well, with some providers you need to restart the router before you get an ip address on your Linux box, from what I've read before on this forum. Can you try that ?

---

### Post by sliver99 on 2009-05-28
i can't believe...
it worked, i don't know wky but it worked!!!

do you also know if should i reboot my router every time i switch from windows to linux??

anyway thanks again :D

---

