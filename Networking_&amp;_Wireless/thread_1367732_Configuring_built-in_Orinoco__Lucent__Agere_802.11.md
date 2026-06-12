---
title: "Configuring built-in Orinoco / Lucent / Agere 802.11b  on Sony VAIO SRX77"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by rmacksoud on 2009-12-29
I need some assistance in figuring out why my built-in wireless on a Sony VAIO srx77 laptop (circa 2002) is not working.  I'm new to Ubuntu (and Linux) but was able to install and configure everything else on this machine w/o much difficulty and it now runs like a champ.

The machine has both built-in wired (eth0) and wireless (eth1). Wireless works when I attach a NetGear USB device, just not the built-in (which is apparently an Orinoco / Lucent / Agere device).

Running Ubuntu 9.10.  Please let me know what other info I can provide.  Thanks.

---

### Post by The Toxic Mite on 2009-12-30
Hey!

Can you go to Applications -> Accessories -> Terminal, and enter the following commands please?:

```

lspci -v less
sudo lshw -c network
ifconfig
iwconfig

```

Post them here when you are done :)

---

### Post by rmacksoud on 2009-12-30
Thanks!


-------------
lspci -v less

It responds with the usage for lspci

--------------------
sudo lshw -c network

The first is the built-in wired device
The second is the built-in wireless device
The third is a NetGear device plugged into my USB port
FWIW, the built-in wireless was not working prior to added the netgear device and removing the netgear device doesn't appear to have any impact.

  *-network               
       description: WaveLAN/IEEE
       product: Version 01.01
       vendor: Lucent Technologies
       physical id: 0
       slot: Socket 1
       resources: irq:9
  *-network
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 03
       serial: 08:00:46:45:27:7c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:9 memory:f4100000-f4100fff ioport:3000(size=64)
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:02:2d:45:99:bb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 7.28 link=no multicast=yes wireless=IEEE 802.11b
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:09:5b:b6:87:43
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.9 multicast=yes wireless=IEEE 802.11-b



--------
ifconfig

eth0      Link encap:Ethernet  HWaddr 08:00:46:45:27:7c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:02:2d:45:99:bb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:9 Base address:0x3040 

eth1:avahi Link encap:Ethernet  HWaddr 00:02:2d:45:99:bb  
          inet addr:169.254.8.55  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:9 Base address:0x3040 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:09:5b:b6:87:43  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:feb6:8743/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1008 errors:0 dropped:0 overruns:0 frame:0
          TX packets:545 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:931038 (931.0 KB)  TX bytes:64439 (64.4 KB)



--------
iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"macksoud-a"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     IEEE 802.11-b  ESSID:"Macksoud-A"  Nickname:"Macksoud-A"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:90:F2:42:A4   
          Bit Rate:11 Mb/s   Tx-Power:18 dBm   
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level=-46 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

