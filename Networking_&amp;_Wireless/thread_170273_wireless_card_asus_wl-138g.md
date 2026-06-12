---
title: "wireless card asus wl-138g"
date: 2006-05-04
forum: Networking &amp; Wireless
---

### Post by morphis on 2006-05-04
Ho 
Im beggining in ubuntu...and It would be great to enable internet on it...
So my driver looks to be OK Ive set it up with the last version of ndiswrapper and the WinXP driver provided in the install CD of the card...
First Im on breezy, I had the kernel 2.6.12-9-386 with the wireless extension 17,
when i ran iwlist wlan0 scan I had:
```
Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...
```

so I upgraded my kernel to 2.6.16-ck3 so the wireless extension (WE) has been upgraded to the version 19, then i took the wireless-tools28 to be compatible withe that WE...
But It did not fix the problem...](*,) 
I think the point is that i cant set the essid
```
morphelin@master:~$ sudo iwconfig wlan0 essid BTVOYAGER2091-28
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Invalid argument.
``` 

If anyone succeed to make that card working, let me know...
thx in advance

---

### Post by morphis on 2006-05-04
So after looking in several threads, I gathered the informations usefull...
but it didn't help me to find any clue...

```
morphelin@master:~$ sudo lshw -C network
  *-network:0 DISABLED
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@00:08.0
       logical name: eth0
       version: 10
       serial: 00:e0:4c:11:25:3b
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=half link=no multicast=yes port=MII speed=10MB/s
       resources: ioport:d800-d8ff iomemory:df020000-df0200ff irq:11
  *-network:1
       description: Wireless interface
       product: Marvell W8300 802.11 Adapter
       vendor: Marvell Technology Group Ltd.
       physical id: b
       bus info: pci@00:0b.0
       logical name: wlan0
       version: 07
       serial: 00:15:f2:2a:23:56
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.16rc2 firmware=ASUS,12/24/2003,2.2.0.20 link=no multicast=yes wireless=IEEE 802.11b
       resources: iomemory:df000000-df00ffff iomemory:df010000-df01ffff irq:10

morphelin@master:~$ sudo lspci -v
0000:00:0b.0 Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 802.11 Adapter (rev 07)
        Subsystem: Asustek Computer, Inc.: Unknown device 138f
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 10
        Memory at df000000 (32-bit, non-prefetchable) [size=64K]
        Memory at df010000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2

morphelin@master:~$ sudo lspci -v | grep subordinate
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0

```
That logically means that my card is recognise by the system,
> /etc/network/interfaces

 The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

iface wlan0 inet static
wireless-essid BTVOYAGER2091-28
wireless-key 0101010101
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1

auto wlan0

that means that the essid is set... the WEP key too
but

```
morphelin@master:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Sensitivity=-200 dBm
          RTS thr:2346 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

morphelin@master:~$ ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:15:F2:2A:23:56
          inet6 addr: fe80::215:f2ff:fe2a:2356/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Memory:df010000-df020000

```
but that not!!!!
but my scan can find the network
```
morphelin@master:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:11:F5:F3:4D:28
                    ESSID:"BTVOYAGER2091-28"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:0/100  Signal level:-85 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
```

So the problem is unchanged, moreover when i run wifi-radar and i try to connect with, it freeze on a "working" window...
[SIZE="6"]HELP[/SIZE]

---

### Post by morphis on 2006-05-04
Im speaking alone but maybe it can be helpfull
I have smth more, when I run wifi-radar in a terminal I have that:
```
Error : unrecognised wireless request "BTVOYAGER2091-28"
Traceback (most recent call last):
  File "/usr/sbin/wifi-radar", line 903, in connect_profile
    connect_to_network( ssid, connect_status_window )
  File "/usr/sbin/wifi-radar", line 296, in connect_to_network
    os.kill( int(open(DHCP_PIDFILE, mode='r').readline()), signal.SIGTERM )
ValueError: invalid literal for int():
```
So the probleme is definitly with the essid or ssid??
and I'll try with the driver from another card which seems to work... dwlg510_driver_100.zip
I let kno if it works...

---

### Post by morphis on 2006-05-06
in fact its working now...
if u have the same problem of essid try

```
ifconfig wlan0 down
ifconfig wlan0 up
```
or maybe an ipv6 problem...
but not sure...
By the way its working so its possible, good luck!:D

---

