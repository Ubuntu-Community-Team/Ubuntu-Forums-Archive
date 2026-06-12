---
title: "Can't get WPA2-PSK working"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by Bigfoot73 on 2009-11-05
I am trying to get my wireless connection working without success. I have a D-link DWL-G520 that should connect to a D-link DWL-2100AP.

The first problem was that there seemed to be no driver installed after upgrading to 9.10, but I think I solved that. (I know there was another driver installed in 9.04, but I don't know if that was better. Normally I don't need the wireless, but now I need to move the computer to a room without wired network.)

Below is the content of /etc/network/interfaces, I have added all the wlan-stuff manually. 
My first problem is that the wireless is not working at all.
My other problem is that the wired network also stops working. I have to comment out the wlan section and reboot to get any network connection at all working!
=================================================================
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.0.20
    netmask 255.255.255.0
    network 192.168.0.0
    broadcast 192.168.0.255
    gateway 192.168.0.254
    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 192.168.0.254

# Wireless
auto wlan0
iface wlan0 inet static
    address 192.168.0.30
    netmask 255.255.255.0
    network 192.168.0.0
    broadcast 192.168.0.255
    gateway 192.168.0.254
    dns-nameservers 192.168.0.254
    wpa-driver wext
    wpa-ssid rohenetwlan
    #No broadcast
    wpa-ap-scan 2
    #WPA2
    wpa-proto RSN
    #TKIP
    wpa-pairwise TKIP
    wpa-group TKIP
    #Pre-shared key
    wpa-key-mgmt WPA-PSK
    #Key must be in hex
    wpa-psk *******************
=================================================================

iwconfig output with "wlan0"-section of /etc/network/interfaces outcommented:
=================================================================
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  Mode:Managed  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vboxnet0  no wireless extensions.
=================================================================

iwconfig output with "wlan0"-section of /etc/network/interfaces NOT outcommented:
=================================================================
...
wlan0     IEEE 802.11bg  ESSID:"rohenetwlan"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
....
=================================================================

iwlist scan output with "wlan0"-section of /etc/network/interfaces outcommented:
=================================================================
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

vboxnet0  Interface doesn't support scanning.
=================================================================

iwlist scan output with "wlan0"-section of /etc/network/interfaces NOT outcommented:
=================================================================
...
wlan0     Scan completed :
          Cell 01 - Address: 00:22:B0:6E:3F:99
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000006da01181
                    Extra: Last beacon: 930ms ago
                    IE: Unknown: 00080000000000000000
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030102
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706474220010D11
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
...
=================================================================

lshw -C network output:
=================================================================
  *-network               
       description: Ethernet interface
       product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:26:18:14:5b:b1
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.0.20 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:26 memory:fbec0000-fbefffff ioport:ec00(size=128)
  *-network
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: wlan0
       version: 01
       serial: 00:17:9a:af:50:da
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.0.30 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:21 memory:fbff0000-fbffffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
=================================================================

Any suggestion what I should try next?
(I haven't tried other encryptions or without. There are other computers connected to the accesspoint so I prefer not to mess with that unless really needed.)

---

### Post by papangul on 2009-11-05
Why don't you first try the WICD network manager?
The following direction is from wicd site-
If Wicd fails to connect after you install it, make sure that the only entry in your /etc/network/interfaces file is: 
```
auto lo
iface lo inet loopback
```

---

### Post by Bigfoot73 on 2009-11-06
Thanks. I was able to connect now, but there are still two small problems.

1. It only works with SSID broadcast enabled. If a disable broadcasting wicd only displays the network as <hidden> and I can't find anywhere to type in the SSID. If I select "Find a hidden network" I can enter a SSID but it always tells me that there are no hidden networks found.

2. If I connect and disconnect a few times I can't connect any more. Rebooting helps.

(I can live with these problems, I only need the wireless for a couple of weeks while renovating the room where I normally have the computer, but it would be nice to have it working perfectly.)

---

