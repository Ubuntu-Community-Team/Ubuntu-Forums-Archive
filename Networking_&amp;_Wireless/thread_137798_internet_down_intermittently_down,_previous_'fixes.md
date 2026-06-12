---
title: "internet down intermittently down, previous 'fixes' not working..."
date: 2006-02-28
forum: Networking &amp; Wireless
---

### Post by veighjay on 2006-02-28
hi

i had some wireless internet problems initially after installing ubuntu. did a lot of reading/searching, did lots of typing in shell and then it worked... for a while... it is now down, i have re-done all the things i tried before, still not working.... 

here are all the things i've done (not sure if i'm meant to be making such long posts, but am trying to be as informative as possible....)

oh, and i am a linux noob....

first, i checked/edited these files...

```
/etc/dhcp3/dhclient.conf

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
prepend domain-name-servers 212.74.112.66, 212.74.112.67;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
```

```
/etc/resolv.conf

nameserver 212.74.112.66
nameserver 212.74.112.67
```

```
lsmod | grep ipw

ipw2200                92680  0
firmware_class          9472  1 ipw2200
ieee80211              27012  1 ipw2200
ieee80211_crypt         5636  2 ipw2200,ieee80211
```

```
sudo lshw -C network
  *-network:0
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:58:eb:a2
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=half link=no multicast=yes port=MII speed=10MB/s
       resources: ioport:4000-40ff iomemory:d0201800-d02018ff irq:11
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:dd:13:34
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.0.6 firmware=ABG:9.0.1.5 (Oct 15 2004) link=no multicast=yes wireless=unassociated
       resources: iomemory:d0200000-d0200fff irq:10
```

```
lspci
0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02)
0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 855GME GMCH Host-to-AGP Bridge (Virtual PCI-to-PCI) (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
0000:02:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:02.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
0000:02:04.0 CardBus bridge: ENE Technology Inc CB710 Cardbus Controller
0000:02:04.1 FLASH memory: ENE Technology Inc: Unknown device 0530
0000:02:04.2 0805: ENE Technology Inc: Unknown device 0550
0000:02:04.3 FLASH memory: ENE Technology Inc: Unknown device 0520
```

```
sudo cardctl ident
Socket 0:
  no product info available
```

```
/etc/dhcp3/dhclient-script

# Modified for Debian. Matt Zimmerman and Eloy Paris, December 2003

# The alias handling in here probably still sucks. -mdz

#make_resolv_conf() {
# if [ -n "$new_domain_name" -o -n "$new_domain_name_servers" ]; then
# local new_resolv_conf=/etc/resolv.conf.dhclient-new
# rm -f $new_resolv_conf
#
# if [ -n "$new_domain_name" ]; then
# echo search $new_domain_name >> $new_resolv_conf
# else # keep 'old' search/domain scope
# egrep -i '^ *[:space:]*(search|domain)' /etc/resolv.conf >> \
# $new_resolv_conf
# fi
# 
# if [ -n "$new_domain_name_servers" ]; then
# for nameserver in $new_domain_name_servers; do
# echo nameserver $nameserver >>$new_resolv_conf
# done
# else # keep 'old' nameservers
# egrep -i '^ *[:space:]*nameserver' /etc/resolv.conf >> \
# $new_resolv_conf
# fi
#
# chown --reference=/etc/resolv.conf $new_resolv_conf
# chmod --reference=/etc/resolv.conf $new_resolv_conf
# mv $new_resolv_conf /etc/resolv.conf
# fi
#}
```

```
sudo gedit /etc/modprobe.d/aliases
alias net-pf-10 off #ipv6
```

(just realised that i put code tags around the command and the text file, but u know what i mean... )

they seemed ok (?)..
then i changed settings in the gui system>admin>networking, activating, deactivating, changing from dhcp to static ip... no difference...

then 

```
sudo ifconfig
eth1      Link encap:Ethernet  HWaddr 00:0E:35:DD:13:34
          inet6 addr: fe80::20e:35ff:fedd:1334/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:174 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2055 (2.0 KiB)  TX bytes:8424 (8.2 KiB)
          Interrupt:10 Base address:0x4000 Memory:d0200000-d0200fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:332775 (324.9 KiB)  TX bytes:332775 (324.9 KiB)
```

then 

```
sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"NETGEAR"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:6C:42:50:1A
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:XXXX-XXXX-XX   Security mode:open
          Power Management:off
          Link Quality=72/100  Signal level=-57 dBm  Noise level=-84 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

then i changed

/etc/network/interfaces

```
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth1

# The primary network interface
iface eth1 inet static
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid NETGEAR
	wireless-key open XXXX-XXXX-XX
	address 192.168.0.2
	netmask 255.255.255.0
	gateway 192.168.0.1

auto eth1
```


still no change....

then checked...

```
sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:14:6C:42:50:1A
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rate:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=67/100  Signal level=-60 dBm
                    Extra: Last beacon: 15ms ago

sit0      Interface doesn't support scanning.
```


then i did the following (which i found on one of the threads...)

```
okid@ubuntu:~$ sudo ifconfig eth1 down
okid@ubuntu:~$ sudo ifconfig eth1 up
okid@ubuntu:~$ sudo iwconfig eth1 essid NETGEAR
okid@ubuntu:~$ sudo iwconfig eth1 key s:XXXXXXXXXX
okid@ubuntu:~$ sudo iwconfig eth1 ap 00:14:6C:42:50:1A
okid@ubuntu:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:0e:35:dd:13:34
Sending on   LPF/eth1/00:0e:35:dd:13:34
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

iwlist scan showed no changes after all this... one thing i do wonder about is the fact that encyption key says off in the iwlist scan despite the key i put in using iwconfig eth1 key......

i tried pinging google, this is what i got..

```
ping 68.115.71.53
PING 68.115.71.53 (68.115.71.53) 56(84) bytes of data.
From 192.168.0.2 icmp_seq=2 Destination Host Unreachable
From 192.168.0.2 icmp_seq=3 Destination Host Unreachable
	.
	.
	.
	.
From 192.168.0.2 icmp_seq=233 Destination Host Unreachable
From 192.168.0.2 icmp_seq=234 Destination Host Unreachable
	.
	.
	.
```
going on endlessly, ended up closing the terminal screen...



and here i am... back onto windows to get to this forum! (is that ironic at all?)

a couple of things i did notice- 
-when the internet was working, when i clicked on the network symbol in the top right tray, and the network screen came up, on the second tab (can't remember, is it system?) it used to say ip static and give the gateway, ip and subnet when the internet was workin... now that it's not, it just says ethernet and some ip address which i think was the same as the hardware address for the network card (i could be talking absolute bullshit here)...
-around the time it stopped working, i had been attempting to install gallery using 
sudo aptitude install gallery..
it seemed to go ok until it needed to start apache and apache2 (nfi what that means)... it seemed to take ages to restart one of them, i left comp overnight, no change next morning, so i just closed the terminal... 


my setup is
toshiba m30x satellite. intel pro/wireless2200.



any help v much appreciated. reading even the first paragraph of this post appreciated.

---

### Post by veighjay on 2006-02-28
well, before giving up, i thought i'd check one last time... now the mf works!

so, i did the following, hoping someone might be able to tell me what is going wrong... i did notice that this time the iwlist scan had encryption on... is it possible that settings i change take a while to 'kick in'? i did do 'sudo ifdown eth1/ifup eth1' after all the changes i made....

```
sudo iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:0F:B5:B3:60:46
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rate:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54
                    Quality=95/100  Signal level=-32 dBm
                    Extra: Last beacon: 675ms ago

sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:0e:35:dd:13:34
Sending on   LPF/eth1/00:0e:35:dd:13:34
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
ip length 576 disagrees with bytes received 580.
accepting packet with data after udp payload.
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
ip length 576 disagrees with bytes received 580.
accepting packet with data after udp payload.
DHCPACK from 192.168.0.1
/etc/dhcp3/dhclient-script: line 201: make_resolv_conf: command not found
bound to 192.168.0.2 -- renewal in 122172 seconds.

sudo iwconfig eth1
eth1      IEEE 802.11g  ESSID:"NETGEAR"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:B5:B3:60:46
          Bit Rate=24 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:0000-0EDC-BA   Security mode:restricted
          Power Management:off
          Link Quality=68/100  Signal level=-32 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:22

 sudo ifconfig
eth1      Link encap:Ethernet  HWaddr 00:0E:35:DD:13:34
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fedd:1334/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2740 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2073723 (1.9 MiB)  TX bytes:376729 (367.8 KiB)
          Interrupt:10 Base address:0x4000 Memory:d0200000-d0200fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3322 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3322 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:298779 (291.7 KiB)  TX bytes:298779 (291.7 KiB)

sudo gedit /etc/network/interfaces
# The primary network interface
iface eth1 inet static
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid NETGEAR
	wireless-key restricted 00000edcba
	address 192.168.0.2
	netmask 255.255.255.0
	gateway 192.168.0.1

auto eth1
```

---

### Post by veighjay on 2006-03-01
anyone?

---

### Post by veighjay on 2006-03-01
wow

after hours and fkn hours of troubleshooting, i think the problem was simply just different hostnames.... the ubuntu hostname was ubuntu, different to what i was using in windows..... unbelievable...

---

