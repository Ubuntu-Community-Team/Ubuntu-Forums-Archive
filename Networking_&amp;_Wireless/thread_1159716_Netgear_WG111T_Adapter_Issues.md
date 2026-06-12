---
title: "Netgear WG111T Adapter Issues"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by Alaydriem on 2009-05-14
Greetings,

I've been trying for the past two days now to get my Netgear WG111T 108 Mbps Wireless USB 2.0 Adapter to work on my Mini ITX I built a few days ago. I've been researching the forums and googling all day trying to find a solution to getting this thing to load up and I've run out of ideas. I'm running 9.04 Ubuntu.

So here is what I managed to get:

Installed ndiswrapper and the ndisgtk. Installed the two drivers for it, ntwg11t.inf and athfmwdl.inf.

Network-Manager can use and see the device, but when it comes to connecting to a WPA2 PSK network it keeps prompting me for the WPA Key. I installed WICD, and it sees my network, but it doesn't allow me to the connect to it.

Here's my outputs:

ndiswrapper -l
```
athfmwdl : driver installed
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netwg11t : driver installed
        device (1385:4250) present
```lsusb
```
Bus 001 Device 004: ID 1385:4250 Netgear, Inc WG111T
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```lshw -C Network
```

  *-network
       description: Ethernet interface
       product: MCP73 Ethernet
       vendor: nVidia Corporation
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth0
       version: a2
       serial: 00:01:2e:25:be:ea
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.15 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0f:b5:36:e0:60
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netwg11t driverversion=1.53+NETGEAR,10/15/2004,1.0.1.10 multicast=yes wireless=IEEE 802.11g
```ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:01:2e:25:be:ea
          inet addr:192.168.1.15  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:2eff:fe25:beea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:234 errors:0 dropped:0 overruns:0 frame:0
          TX packets:231 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:25857 (25.8 KB)  TX bytes:48964 (48.9 KB)
          Interrupt:251 Base address:0xe000
```iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"PORTWOODNG"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:108 Mb/s
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``` sudo iwlist scan

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

^[[Awlan0     Scan completed :
          Cell 01 - Address: 00:0F:B5:6C:1E:58
                    ESSID:"mynetwork"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:1E:C7:EE:F6:B9
                    ESSID:"2WIRE402"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:28/100  Signal level:-78 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:14:6C:47:1F:F6
                    ESSID:"PORTWOODNG"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:82/100  Signal level:-43 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
```I can see the network, I just can't join, and resetting the router and clearing it to a default state isn't an option, otherwise I would just do that and test to see if it works without a WPA2 Key.

Any help would be greatly appreciated.

Thank you,
Alaydriem

---

### Post by Alaydriem on 2009-05-15
Greetings,

Does anyone have any suggestions on how to get this hardware to work with Ubuntu?

Thank you

---

### Post by TuxImpersonator on 2009-05-30
Hi,

I'm helping set-up a friends laptop. We have exactly the same problem: Installed the two drivers with ndiswrapper, can see but not connect to a WPA2 route. If anyone can help that'ld be great.

Thanks

---

