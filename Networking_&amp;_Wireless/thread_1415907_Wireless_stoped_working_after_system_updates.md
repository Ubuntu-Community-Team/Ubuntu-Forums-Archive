---
title: "Wireless stoped working after system updates"
date: 2010-02-25
forum: Networking &amp; Wireless
---

### Post by tarek.ghaddar on 2010-02-25
Hi,
two days ago I have installed some updates suggested by Update Manager and after that wireless stopped working.
From network manager I see that the wireless is disabled but I don't know how to enable it.
I searched on this forum and tried a workaroud but it didn't work for me (remove network manager and install wicd).
I also found that maybe I need the "b43" module but I don't have it loaded in my kernel:

tarek@uTarek:~$ sudo lsmod | grep b43
tarek@uTarek:~$ 


Following some info of my system:

tarek@uTarek:~$ uname -r
2.6.31-19-generic
tarek@uTarek:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1c:25:16:33:7f
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=0.3-0 ip=192.168.0.8 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:30 memory:fe000000-fe01ffff memory:fe025000-fe025fff ioport:1840(size=32)
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:04:76:08
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:32 memory:df3ff000-df3fffff

When I try to assign an ipaddress to my wireless network card I get this error:
tarek@uTarek:~$ sudo ifconfig wlan0 192.168.0.9
SIOCSIFFLAGS: Errore sconosciuto 132

tarek@uTarek:~$ sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1c:25:16:33:7f  
          indirizzo inet:192.168.0.8  Bcast:192.168.0.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::21c:25ff:fe16:337f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1745 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1780 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:100 
          Byte RX:1588723 (1.5 MB)  Byte TX:304171 (304.1 KB)
          Memoria:fe000000-fe020000 

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:240 (240.0 B)  Byte TX:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:04:76:08  
          indirizzo inet:192.168.0.9  Bcast:192.168.0.255  Maschera:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-BF-04-76-08-00-00-00-00-00-00-00-00-00-00  
          [NO FLAGS]  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)


Please help, thanks.
Tarek

---

### Post by tarek.ghaddar on 2010-02-25
The wireless adapter seems hardware blocked:

tarek@uTarek:~$ sudo rfkill list
0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
tarek@uTarek:~$ sudo rfkill unblock all
tarek@uTarek:~$ sudo rfkill list
0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

How can I unlock it?

---

### Post by chili555 on 2010-02-25
> How can I unlock it?]Find the hardware wireless switch on your laptop and slide it back to 'On.' If you have none, there may be a problem with the operating system recognizing the hotkeys. If you suspect so, post the make and model of your laptop. Thanks.

---

### Post by kennyadsl on 2010-02-25
same problem after the last update.

I'm on IBM thinkpad X60s with intel PRO/Wireless 3945ABG
```

k ~ $  sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:16:d3:39:7f:fd
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=0.5-1 ip=192.168.1.2 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:ee000000-ee01ffff ioport:2000(size=32)
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:18:de:cb:6a:92
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:30 memory:edf00000-edf00fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes


```

The wireless led is off and pushing the key (fn+F5) to enable wifi nothing happens.

i tryed 

```
sudo modprobe -r -f iwl3945
sudo modprobe iwl3945
```

but nothing again.

i tryed installing 

```
linux-backports-modules-wireless-karmic-generic
```

but nothing again.

Also my bluetooth is locked:

```
k ~ $  sudo rfkill list
0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes

```

Some help please?

---

### Post by chili555 on 2010-02-25
> Some help please?Same answer. Please see: [http://www.thinkwiki.org/wiki/Category:X60s](http://www.thinkwiki.org/wiki/Category:X60s)> A tiny "Radio Frequency Kill Switch" is rather hidden below the front edge of the keyboard, it stops Wireless, Bluetooth and GSM/UMTS. 

---

