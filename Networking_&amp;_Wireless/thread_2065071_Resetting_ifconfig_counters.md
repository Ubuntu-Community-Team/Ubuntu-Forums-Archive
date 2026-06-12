---
title: "Resetting ifconfig counters"
date: 2012-10-01
forum: Networking &amp; Wireless
---

### Post by agzathot on 2012-10-01
Hello guys i have a strange issue with my eth0 from time to time the ifconfig counters got very large numbers:

example:
[SIZE=1]eth0      Link encap:Ethernet  HWaddr xxe:xx:xx:xx:xx  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:263281495183500 errors:1579715814780738 dropped:526571580301590 overruns:263285790150795 frame:1316428950753975
          TX packets:263285790150795 errors:1053143160603180 dropped:0 overruns:263285790150795 carrier:526571580301590
          collisions:1316428950753975 txqueuelen:1000 
          RX bytes:263285790150795 (263.2 TB)  TX bytes:263285790150795 (263.2 TB)
          Interrupt:42 [/SIZE]

and when this happens i lost network connection, the only way so far i have found is to reset linux, i have try "sudo ifconfig eth0 down / up" but gto same issue, is there a way to flush the ifconfig counters ?

what can be causing the eth0 got to RX & TX 263.2 TB when is not even connected ?

any clue what to check ?

---

### Post by Sergius14 on 2012-10-01
Humm, I think the only way to do this is unloading the Network Module (driver) and reloading.

I don't know if Ubuntu has the Network Drivers as Kernel modules...


Give a Look to this aproach (rmmod, insmod) and post back to us what you find out!

---

### Post by oldfred on 2012-10-01
Removed HW address. Those are supposed to be unique but can be spoofed. 

Do you have a mix of fixed and DHCP addresses? It seems like there may be a duplicate address. Or you have a fixed that is in the DHCP range? If someone has a duplicate then only when the other one is on, then it is an issue??

---

### Post by agzathot on 2012-10-02
ty for the hints guys, actually this happens when using an 4G adapter no eth0 connected :s

---

### Post by Sergius14 on 2012-10-03
Should be the same...

Eth, wl, lo, is just a naming convention to quickly identify the netword card type.

---

### Post by jonobr on 2012-10-03
Hello


Im guessing the reason for your high counters is that the errors are unusually high on that interface requiring packets to be resent.

This could be caused by an incorrectly negotiated  speed or connection type (duplex/half duplex etc).

Autoneg on some cards is falkey and is best set to what the other end is doing.
You can check your eth card by using ethtool
You may need to install it.

Run it by using 

```
sudo ethtool eth0 
```
It shoudl tell you what your able to do and what the other end is doing.

Watch for mismatches between the two

---

### Post by agzathot on 2012-10-03
the strange issue is that i almost dont use cable network, use either Wlan or 4G and still eth0 keeps getting big counters

right now im using wifi since morning and still im geting this:

[SIZE="1"][HTML]azathoth@Cthulu:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr d4:be:d9:06:77:c9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3003268765930635 errors:18019612595583810 dropped:6006537531861270 overruns:3003268765930635 frame:15016343829653175
          TX packets:3003268765930635 errors:12013075063722540 dropped:0 overruns:3003268765930635 carrier:6006537531861270
          collisions:15016343829653175 txqueuelen:1000 
          RX bytes:3003268765930635 (3.0 PB)  TX bytes:3003268765930635 (3.0 PB)
          Interrupt:43 

azathoth@Cthulu:~$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  Not reported
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: Unknown!
	Duplex: Unknown! (255)
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: pg
	Wake-on: g
	Current message level: 0x0000003f (63)
			       drv probe link timer ifdown ifup
	Link detected: no
azathoth@Cthulu:~$[/HTML][/SIZE]

the wired adapter its alteros and the wireless its broadcom i have se several post about broadcom but for wireless 

try the metod posted on this link [http://serverfault.com/questions/23687/how-do-i-clear-the-interface-stats-on-linux](http://serverfault.com/questions/23687/how-do-i-clear-the-interface-stats-on-linux)

but didnt clear the counters:
[SIZE="1"][HTML]azathoth@Cthulu:~$ sudo ifconfig eth0 down; rmmod eth0;insmod eth0;ifconfig eth0
ERROR: Module eth0 does not exist in /proc/modules
insmod: can't read 'eth0': No such file or directory
eth0      Link encap:Ethernet  HWaddr d4:be:d9:06:77:c9  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3138375552129450 errors:18830253312776700 dropped:6276751104258900 overruns:3138375552129450 frame:15691877760647250
          TX packets:3138375552129450 errors:12553502208517800 dropped:0 overruns:3138375552129450 carrier:6276751104258900
          collisions:15691877760647250 txqueuelen:1000 
          RX bytes:3138375552129450 (3.1 PB)  TX bytes:3138375552129450 (3.1 PB)
          Interrupt:43 

azathoth@Cthulu:~$ [/HTML][/SIZE]

hows the networking module called on ubuntu ?

if helps here is my lspci output:

[HTML][SIZE="1"]azathoth@Cthulu:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation 5 Series/3400 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GT215 [GeForce GT 335M] (rev ff)
02:00.0 Ethernet controller: Atheros Communications Inc. AR8132 Fast Ethernet (rev c0)
03:00.0 Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)
04:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller (rev 30)
04:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 30)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
azathoth@Cthulu:~$ [/SIZE][/HTML]

any comment its apreciated

---

### Post by salpula on 2013-02-06
Your extremely high errors are likely because you are using wireless. Poor signal and interference cause large numbers of errors on wireless interfaces.

---

