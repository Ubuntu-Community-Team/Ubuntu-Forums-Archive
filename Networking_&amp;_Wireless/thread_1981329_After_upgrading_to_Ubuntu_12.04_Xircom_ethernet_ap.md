---
title: "After upgrading to Ubuntu 12.04 Xircom ethernet appears as device not ready"
date: 2012-05-16
forum: Networking &amp; Wireless
---

### Post by jobseeker71 on 2012-05-16
After upgrading Ubuntu desktop from 11.10 the wired connection has stopped working. The Xircom cardbus ethernet 10/100 worked happily in previous version of Ubuntu but under 12.04 the device is not ready within network manager.

The /etc/network/interfaces file only contains
[I]an@a-laptop:/etc/network$ more interfaces
auto lo
iface lo inet loopback[/I]

The /etc/NetworkManager/NetworkManager.conf file only contains :
[I]an@a-laptop:/etc/NetworkManager$ more NetworkManager.conf 

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=00:11:25:2E:1B:29,00:10:A4:75:BE:7C,

[ifupdown]
managed=true[/I]

Results of ifconfig : 
[I]an@a-laptop:/etc/NetworkManager$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:11:25:2e:1b:29  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:0e:35:98:62:8d  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Memory:c0210000-c0210fff 

eth2      Link encap:Ethernet  HWaddr 00:10:a4:75:be:7c  
          inet6 addr: fe80::210:a4ff:fe75:be7c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:123895 (123.8 KB)  TX bytes:6510 (6.5 KB)
          Interrupt:11 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:401 errors:0 dropped:0 overruns:0 frame:0
          TX packets:401 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:32808 (32.8 KB)  TX bytes:32808 (32.8 KB [/I]

Results from ispci : 
[I]an@a-laptop:/etc/NetworkManager$ lspci -nn | tail -n3
02:01.0 Ethernet controller [0200]: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) [8086:101e] (rev 03)
02:02.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
03:00.0 Ethernet controller [0200]: Xircom Cardbus Ethernet 10/100 [115d:0003] (rev 03) [/I] <-- this is eth2

Results from dmesg 
[I]an@a-laptop:/etc/NetworkManager$ dmesg | grep eth2
[   40.291122] xircom_cb 0000:03:00.0: eth2: Xircom cardbus revision 3 at irq 11
[   40.306545] xircom_cb 0000:03:00.0: eth2: xircom cardbus adaptor found, using irq 11
[   43.126062] xircom_cb 0000:03:00.0: eth2: Link status has changed 
[   43.126070] xircom_cb 0000:03:00.0: eth2: Link is 100 mbit [/I] 

Results from syslog
[I]an@a-laptop:/etc/NetworkManager$ sudo cat /var/log/syslog | grep etwork | tail -n20
[sudo] password for an: 
May 16 20:26:27 a-laptop NetworkManager[686]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May 16 20:26:27 a-laptop NetworkManager[686]: <info> (eth1): bringing up device.
May 16 20:26:27 a-laptop NetworkManager[686]: <info> (eth1): deactivating device (reason 'managed') [2]
May 16 20:26:27 a-laptop NetworkManager[686]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0/net/eth1, iface: eth1)
May 16 20:26:27 a-laptop NetworkManager[686]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0/net/eth1, iface: eth1): no ifupdown configuration found.
May 16 20:26:27 a-laptop NetworkManager[686]: <warn> failed to allocate link cache: (-10) Operation not supported
May 16 20:26:27 a-laptop NetworkManager[686]: <info> (eth2): driver 'xircom_cb' does not support carrier detection.
May 16 20:26:27 a-laptop NetworkManager[686]: <error> [1337196387.578750] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth2): unable to read permanent MAC address (error 95)
May 16 20:26:27 a-laptop NetworkManager[686]: <info> (eth2): new Ethernet device (driver: 'xircom_cb' ifindex: 4)
May 16 20:26:27 a-laptop NetworkManager[686]: <info> (eth2): exported as /org/freedesktop/NetworkManager/Devices/2
May 16 20:26:27 a-laptop NetworkManager[686]: <info> (eth2): now managed
May 16 20:26:27 a-laptop NetworkManager[686]: <info> (eth2): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May 16 20:26:27 a-laptop NetworkManager[686]: <info> (eth2): bringing up device.
May 16 20:26:27 a-laptop NetworkManager[686]: nm_netlink_monitor_get_flags_sync: assertion `self != NULL' failed
May 16 20:26:27 a-laptop NetworkManager[686]: <warn> (eth2): couldn't get carrier state: (-1) unknown
May 16 20:26:27 a-laptop NetworkManager[686]: <info> (eth2): carrier now OFF (device state 20, deferring action for 4 seconds)
May 16 20:26:27 a-laptop NetworkManager[686]: <info> (eth2): preparing device.
May 16 20:26:27 a-laptop NetworkManager[686]: <info> (eth2): deactivating device (reason 'managed') [2]
May 16 20:26:27 a-laptop NetworkManager[686]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:00.0/0000:03:00.0/net/eth2, iface: eth2)
May 16 20:26:27 a-laptop NetworkManager[686]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:00.0/0000:03:00.0/net/eth2, iface: eth2): no ifupdown configuration found.[/I]

---

### Post by jobseeker71 on 2012-05-17
could anyone help with what to do next ? please

---

### Post by AnnMatt on 2012-08-30
Hello,
did you find a solution for the problem? 
I think the root-cause might be, that maybe the XIRCOM-Driver does not support "carrier detection" which seems to be required by NetWork Manager 0.9.4 (see [https://bugzilla.redhat.com/show_bug.cgi?id=816719](https://bugzilla.redhat.com/show_bug.cgi?id=816719) which also shows the same error-messages: NetworkManager[838]: nm_netlink_monitor_get_flags_sync: assertion `self != NULL' failed
NetworkManager[838]: <warn> (p5p1): couldn't get carrier state: (-1) unknown))

---

### Post by AnnMatt on 2012-09-22
I found the following solution:
I completely removed Network Manager (I did this before I found this post...)  and to set up a fixed configuration for my network card: 
[http://www.liberiangeek.net/2010/08/disable-network-manager-ubuntu-10-04-lucid-lynx-configure-network-interface-traditionally/](http://www.liberiangeek.net/2010/08/disable-network-manager-ubuntu-10-04-lucid-lynx-configure-network-interface-traditionally/)

To setup the DNS for the card, I followed [http://wiki.debian.org/NetworkConfiguration](http://wiki.debian.org/NetworkConfiguration) by adding the line "dns-nameservers 12.34.56.78 12.34.56.79" (without quotes) to /etc/network/interfaces.

Now my xircom-Card works fine...

---

### Post by dragonfly41 on 2012-09-24
I followed the suggestions above but still can't get internet connection.
I'm trying to bring an old Dell Inspiron 5000e notebook out of retirement and install Lubuntu.

I want to test internet connection on Lubuntu 12.04 live cd before installing Lubuntu on internal drive.   
There is a Xircom CBE2-100 Adapter as the ethernet port.  
I found that the Xircom driver in use is xircom_cb

The only step I didn't follow was to totally remove Network Manager before going through the edits.

Is a reboot required before the network changes kick in?  The live CD does not retain changes so I have to reintroduce changes at every bootup.

Here is the output seen from[COLOR=Navy]** lspci**[/COLOR] .. see Xircom Cardbus Ethernet 10/100 detected on last line.


[COLOR=Navy]lubuntu@lubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:04.0 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:04.1 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)
00:10.0 Communication controller: LSI Corporation WinModem 56k (rev 01)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Rage Mobility M3 AGP 2x (rev 02)
**02:00.0 Ethernet controller: Xircom Cardbus Ethernet 10/100 (rev 03)**[/COLOR]


Any other points I should look at to get internet connection .. initially in live CD mode?

---

### Post by dragonfly41 on 2012-09-24
Still troubleshooting the Xircom failure to make network connection 

Running [COLOR=Navy]dmesg[/COLOR] command I noted the same error <warn> ... 

[COLOR=Navy]NetworkManager[838]: <warn> (p5p1): **couldn't get carrier state**: (-1) unknown))[/COLOR]

This clue led me to this site .. also listed above by AnnMatt

[https://bugzilla.redhat.com/show_bug.cgi?id=816719](https://bugzilla.redhat.com/show_bug.cgi?id=816719)

see comment 6 in above ..

Although this is a Fedora bug is there an updated Ubuntu NetworkManager-0.9.4.0.8 which will detect carrier state and get [COLOR=Navy]Xircom Cardbus Ethernet 10/100[/COLOR] to work?

---

