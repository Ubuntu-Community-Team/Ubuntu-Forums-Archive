---
title: "Frequent wireless drop outs"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by joeinnes on 2009-04-29
For the past three days (or so), I have been having serious problems with my wireless. Essentially, I'm experiencing drop-outs every three to five minutes, despite having approximately 50% signal strength (whatever that means). By drop-out, I mean Network Manager tries to connect to the network again.

Information:
Laptop is a Mesh Pegasus 8889C (if that helps!)

Quick note: I have two wireless interfaces, one (wlan2, normally) is part of an ad-hoc network. The other is connected to my University halls wireless network (wlan0, normally). The problem is with wlan0, and I can't replicate it on wlan2, which leads me to believe it is RT2500 driver issue.

```
lspci:
00:0a.0 Network controller [0280]: RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] (rev 01)

ifconfig:
<snip lo & eth0>
wlan0     Link encap:Ethernet  HWaddr 00:13:d3:6d:ce:2a  
          inet addr:10.188.77.160  Bcast:10.188.255.255  Mask:255.255.0.0
          inet6 addr: fe80::213:d3ff:fe6d:ce2a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39839 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21762 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17697073 (17.6 MB)  TX bytes:9719302 (9.7 MB)

wlan2     Link encap:Ethernet  HWaddr 00:16:0a:15:25:5d  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:aff:fe15:255d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53685 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48621 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3417833 (3.4 MB)  TX bytes:66201283 (66.2 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-0A-15-25-5D-35-35-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster1  Link encap:UNSPEC  HWaddr 00-13-D3-6D-CE-2A-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

iwconfig wlan0:
wlan0     IEEE 802.11bg  ESSID:"Wifirst-Normandie-2"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:03:52:DC:9A:A0   
          Bit Rate=54 Mb/s   Tx-Power=25 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=31/100  Signal level:-78 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lsmod | grep "rt2500pci":
rt2500pci              24064  0 
rt2x00pci              15104  1 rt2500pci
eeprom_93cx6           10240  1 rt2500pci
rt2x00lib              36224  5 rt2500pci,rt2x00pci,rt2500usb,rt73usb,rt2x00usb

dmesg
<snip to the interesting bit (hopefully)>
[  158.153177] rt2500pci 0000:00:0a.0: PCI INT A -> Link[LNKC] -> GSI 5 (level, low) -> IRQ 5
[  158.220767] Registered led device: rt2500pci-phy1:radio

<snip to the next interesting bit (hopefully)>
[ 3418.892059] wlan0: No ProbeResp from current AP 00:03:52:dc:9a:a0 - assume out of range
[ 3419.739423] wlan0: authenticate with AP 00:03:52:dc:9a:a0
[ 3419.936061] wlan0: authenticate with AP 00:03:52:dc:9a:a0
[ 3420.136053] wlan0: authenticate with AP 00:03:52:dc:9a:a0
[ 3420.336067] wlan0: authentication with AP 00:03:52:dc:9a:a0 timed out
[ 3430.484242] wlan0: authenticate with AP 00:03:52:dc:9a:a0
[ 3430.486131] wlan0: authenticated
[ 3430.486144] wlan0: associate with AP 00:03:52:dc:9a:a0
[ 3430.488917] wlan0: RX ReassocResp from 00:03:52:dc:9a:a0 (capab=0x421 status=0 aid=3)
[ 3430.488929] wlan0: associated
[ 3430.500853] wlan0: authenticate with AP 00:03:52:dc:9a:a0
[ 3430.501296] wlan0: authenticate with AP 00:03:52:dc:9a:a0
[ 3430.502831] wlan0: authenticated
[ 3430.502843] wlan0: associate with AP 00:03:52:dc:9a:a0
[ 3430.673050] wlan0: RX ReassocResp from 00:03:52:dc:9a:a0 (capab=0x421 status=0 aid=3)
[ 3430.673062] wlan0: associated
[ 3436.672059] wlan0: No ProbeResp from current AP 00:03:52:dc:9a:a0 - assume out of range
[ 3437.516195] wlan0: authenticate with AP 00:03:52:dc:9a:a0
[ 3437.521512] wlan0: authenticate with AP 00:03:52:dc:9a:a0
[ 3437.521956] wlan0: authenticate with AP 00:03:52:dc:9a:a0
[ 3437.720101] wlan0: authenticate with AP 00:03:52:dc:9a:a0
[ 3437.920067] wlan0: authenticate with AP 00:03:52:dc:9a:a0
[ 3438.121894] wlan0: authentication with AP 00:03:52:dc:9a:a0 timed out
<snip a few more attempts>
[ 3486.988890] wlan0: associate with AP 00:03:52:dc:9a:a0
[ 3487.188055] wlan0: associate with AP 00:03:52:dc:9a:a0
[ 3487.191835] wlan0: RX AssocResp from 00:03:52:dc:9a:a0 (capab=0x421 status=0 aid=3)
[ 3487.191845] wlan0: associated

sudo lshw -C network:
<snip>
  *-network:0             
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: wmaster1
       version: 01
       serial: 00:13:d3:6d:ce:2a
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci ip=192.168.1.1 latency=128 module=rt2500pci multicast=yes wireless=IEEE 802.11bg

sudo /etc/init.d/networking restart:
Reconfiguring network interfaces...Ignoring unknown interface wlan0=wlan0.
Ignoring unknown interface wlan2=wlan2.
done.

iwlist wlan0 scanning:
wlan0     Scan completed :
          Cell 01 - Address: BE:F7:BE:7E:A7:F8
                    ESSID:"joe"
                    Mode:Ad-Hoc
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=86/100  Signal level:-33 dBm  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000000d0a52f25c
                    Extra: Last beacon: 48ms ago
          Cell 02 - Address: 00:03:52:DC:92:00
                    ESSID:"Wifirst-Normandie-20"
                    Mode:Master
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=58/100  Signal level:-78 dBm  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000000022777181
                    Extra: Last beacon: 9768ms ago

```

I'm on 8.10, running kernel 2.6.27-13-generic i686.

Any assistance would be great.

Thanks

---

### Post by joeinnes on 2009-04-30
Nobody got any ideas?

---

### Post by joeinnes on 2009-05-01
Still no thoughts?

---

