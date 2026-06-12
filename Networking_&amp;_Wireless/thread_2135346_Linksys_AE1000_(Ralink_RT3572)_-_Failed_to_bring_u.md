---
title: "Linksys AE1000 (Ralink RT3572) - Failed to bring up wlan1, Destination Host Unreachab"
date: 2013-04-14
forum: Networking &amp; Wireless
---

### Post by Noonien2600 on 2013-04-14
Hi there, UbuntuForums!  Lurker for years, finally made an account because I'm at a loss here!  Been using Debian for ages, heard Ubuntu had a better chance of finding drivers for wireless hardware and switched a server over, so far love it!  Tried getting an old Linksys WUSB54Gv2 working, gave up with that, now trying a Linksys AE1000 and am not having much luck at all.

I'm bridging two networks. Basically, I need my lil (actually, ******* huge. real old school dual pentium II, Zgraph, hah!) Ubuntu box to sit in between a Debian router, and a little consumer Linksys router (not sure of the model, it's newer, nothing special) with WEP enabled.

I believe I've got the hardware installed correctly (I think?), but dhclient hangs, and ifup fails.  Wavemon is able to show signal strength.

My apologies for the wall of text, hope something here is useful.

uname -a:
```

Linux mercury 3.5.0-27-generic #46~precise1-Ubuntu SMP Tue Mar 26 19:33:56 UTC 2013 i686 i686 i386 GNU/Linux

```

lsusb:
```

Bus 001 Device 018: ID 13b1:002f Linksys AE1000 v1 802.11n [Ralink RT3572]

```

Have tried both configurations for wlan1, the dhcp and static ones:
```

#allow-hotplug wlan1
#iface wlan1 inet dhcp
#       wireless-essid my_essid
#       wireless-key MY_10_CHAR_HEX_WEP_KEY

allow-hotplug wlan1
iface wlan1 inet static
       onboot yes
       peerdns yes
       address 192.168.1.10
       netmask 255.255.255.0
       network 192.168.1.0
       broadcast 192.168.1.255
       gateway 192.168.1.1
       wireless-essid my_essid
       wireless-key MY_10_CHAR_HEX_WEP_KEY
       dns-nameservers dns.ip.address.1 dns.ip.address.2

```

iwconfig wlan1:
```

wlan1     IEEE 802.11abgn  ESSID:"my_essid"
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:1E:E5:42:64:A3
          Bit Rate=48 Mb/s   Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:MY_10_CHAR_HEX_WEP_KEY
          Power Management:on
          Link Quality=19/70  Signal level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:54  Invalid misc:608   Missed beacon:0

```

dmesg after ifup wlan1:
```

[ 5214.413148] usb 1-2.2: new full-speed USB device number 18 using uhci_hcd
[ 5214.565084] usb 1-2.2: New USB device found, idVendor=13b1, idProduct=002f
[ 5214.565104] usb 1-2.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 5214.565121] usb 1-2.2: Product: Linksys AE1000
[ 5214.565136] usb 1-2.2: Manufacturer: Linksys
[ 5214.649088] usb 1-2.2: reset full-speed USB device number 18 using uhci_hcd
[ 5214.886307] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 5214.886339] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5214.886355] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 5214.886369] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5214.886383] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 5214.886396] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5214.886409] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 5214.886423] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5214.886436] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 5214.886450] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5214.886463] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 5214.886476] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5214.886489] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 5214.886503] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5214.886515] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 5214.886529] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5214.886541] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 5214.886554] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5214.886567] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 5214.886580] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5214.886593] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 5214.886606] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5214.886619] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 5214.886632] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 5214.886645] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 5214.886658] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 5214.886672] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 5214.886685] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 5214.886698] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[ 5214.886712] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5214.886725] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
[ 5214.886738] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5214.886751] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[ 5214.886764] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5214.886777] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[ 5214.886791] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5214.886803] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
[ 5214.886817] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5214.886829] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[ 5214.886843] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5214.886854] cfg80211: Disabling freq 5260 MHz
[ 5214.886864] cfg80211: Disabling freq 5270 MHz
[ 5214.886875] cfg80211: Disabling freq 5280 MHz
[ 5214.886884] cfg80211: Disabling freq 5300 MHz
[ 5214.886894] cfg80211: Disabling freq 5310 MHz
[ 5214.886903] cfg80211: Disabling freq 5320 MHz
[ 5214.886912] cfg80211: Disabling freq 5500 MHz
[ 5214.886922] cfg80211: Disabling freq 5510 MHz
[ 5214.886931] cfg80211: Disabling freq 5520 MHz
[ 5214.886941] cfg80211: Disabling freq 5540 MHz
[ 5214.886975] cfg80211: Disabling freq 5550 MHz
[ 5214.886986] cfg80211: Disabling freq 5560 MHz
[ 5214.886995] cfg80211: Disabling freq 5580 MHz
[ 5214.887005] cfg80211: Disabling freq 5590 MHz
[ 5214.887014] cfg80211: Disabling freq 5600 MHz
[ 5214.887024] cfg80211: Disabling freq 5620 MHz
[ 5214.887033] cfg80211: Disabling freq 5630 MHz
[ 5214.887042] cfg80211: Disabling freq 5640 MHz
[ 5214.887052] cfg80211: Disabling freq 5660 MHz
[ 5214.887061] cfg80211: Disabling freq 5670 MHz
[ 5214.887071] cfg80211: Disabling freq 5680 MHz
[ 5214.887080] cfg80211: Disabling freq 5700 MHz
[ 5214.887093] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[ 5214.887107] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5214.887120] cfg80211: Updating information on frequency 5755 MHz for a 20 MHz width channel with regulatory rule:
[ 5214.887134] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5214.887147] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[ 5214.887160] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5214.887173] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[ 5214.887186] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5214.887199] cfg80211: Updating information on frequency 5795 MHz for a 20 MHz width channel with regulatory rule:
[ 5214.887212] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5214.887225] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[ 5214.887238] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5214.887251] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[ 5214.887265] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5214.887276] cfg80211: Disabling freq 5835 MHz
[ 5214.887285] cfg80211: Disabling freq 5845 MHz
[ 5214.887295] cfg80211: Disabling freq 5855 MHz
[ 5214.887304] cfg80211: Disabling freq 5865 MHz
[ 5214.888031] ieee80211 phy10: Selected rate control algorithm 'minstrel_ht'
[ 5214.889697] Registered led device: rt2800usb-phy10::radio
[ 5214.889882] Registered led device: rt2800usb-phy10::assoc
[ 5214.890041] Registered led device: rt2800usb-phy10::quality
[ 5237.581606] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 5244.277962] wlan1: authenticate with 00:1e:e5:42:64:a3
[ 5244.586091] wlan1: send auth to 00:1e:e5:42:64:a3 (try 1/3)
[ 5244.592073] wlan1: authenticated
[ 5244.745982] wlan1: associate with 00:1e:e5:42:64:a3 (try 1/3)
[ 5244.752861] wlan1: RX AssocResp from 00:1e:e5:42:64:a3 (capab=0x411 status=0 aid=2)
[ 5244.807823] wlan1: associated
[ 5244.809383] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready

```


iwlist scan:
```

wlan1     Scan completed :
          Cell 01 - Address: 00:1E:E5:42:64:A3
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=39/70  Signal level=-71 dBm
                    Encryption key:on
                    ESSID:"my_essid"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000035a6c4183
                    Extra: Last beacon: 1604ms ago
                    IE: Unknown: 000C656D705F696E7465726E616C
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020014000000

```

route -n:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.4     0.0.0.0         UG    100    0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan1

```

ip link:
```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 00:10:5a:24:b9:b7 brd ff:ff:ff:ff:ff:ff
13: wlan1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
    link/ether 68:7f:74:e6:ab:57 brd ff:ff:ff:ff:ff:ff

```

ip route:
```

default via 192.168.0.4 dev eth0  metric 100
192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.1
192.168.1.0/24 dev wlan1  proto kernel  scope link  src 192.168.1.10

```

ping -I wlan1 192.168.1.10 (the ae1000 static ip):
```

PING 192.168.1.10 (192.168.1.10) from 192.168.1.10 wlan1: 56(84) bytes of data.
64 bytes from 192.168.1.10: icmp_req=1 ttl=64 time=0.120 ms

```

ping -I wlan1 192.168.1.1 (the wireless router ip address):
```

PING 192.168.1.1 (192.168.1.1) from 192.168.1.10 wlan1: 56(84) bytes of data.
From 192.168.1.10 icmp_seq=1 Destination Host Unreachable

```

ifup, ifdown, ifup wlan1:
```

root@mercury:~# ifup wlan1
RTNETLINK answers: File exists
Failed to bring up wlan1.
root@mercury:~# ifdown wlan1
ifdown: interface wlan1 not configured
root@mercury:~# ifup wlan1
RTNETLINK answers: File exists
Failed to bring up wlan1.

```

Why do you hate me so much, computer?
```

Why: command not found

```

I'd appreacite any help, I've been off and on at this for days.  The WUSB54G was basicaly just me banging my head in to a wall for hours on end.  At least with this little AE1000, I can get wavemon to spit something out.

IP Addresses:
192.168.1.1 wireless router
192.168.1.10 ae1000
192.168.0.2 debian router

Thanks in advance, and thanks for reading!

---

### Post by sauyon on 2013-04-14
You can use
```
ifconfig wlan1 down
```
to put disable interfaces that haven't been configured with ifup (ie with network manager)

I also find it interesting that you have the results of both route -n and ip route, but no
```
ifconfig
```

---

### Post by Noonien2600 on 2013-04-14
> **sauyon said:**
> 
I also find it interesting that you have the results of both route -n and ip route, but no
```
ifconfig
```

Gahh, sorry. Figured I'd end up forgetting something :)

ifconfig, before running ifconfig wlan1 down:
```

wlan1     Link encap:Ethernet  HWaddr 68:7f:74:e6:ab:57
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6a7f:74ff:fee6:ab57/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:10836 (10.8 KB)

```

I then ran ifconfig wlan1 down and it brouht wlan1 down without complain (no more entry in ifconfig).

When I issue ifup wlan1, I'm back to this:
```

RTNETLINK answers: File exists
Failed to bring up wlan1.

```

But still nothing in ifconfig.


Are these the signs up a bad driver or do you think I've done something wrong while configuring the adapter?

---

### Post by prshah on 2013-04-14
Do you have both wired AND wireless connected? 

Based on your 'iwconfig" output, you have successfully registered with your wireless base station. A quick check to ensure this will be to attempt to get a dynamic IP address from it; try the command ```
sudo dhclient wlan1
``` from a terminal (Dash-Terminal). 

Please post the output from the above command if the trouble persists.

---

### Post by Noonien2600 on 2013-04-14
> **prshah said:**
> Do you have both wired AND wireless connected?

Yes.  I've tried unplugging the wired and get the same results.  It's like the adapter connects, but won't receive any data.  Have verified that the USB ports and the adapter are good.

> **prshah said:**
> 
Based on your 'iwconfig" output, you have successfully registered with your wireless base station. A quick check to ensure this will be to attempt to get a dynamic IP address from it; try the command ```
sudo dhclient wlan1
``` from a terminal (Dash-Terminal). 

Please post the output from the above command if the trouble persists.

dhclient hangs.  I've let it sit for a few minutes and get nothing.  dmesg doesn't show anything.

I saw in some other post someone doing "dhclient -d" to print output, from what I understand, it forces dhclient in to the forground, and set's the "v" flag as well.

dhclient -d wlan1:
```

Internet Systems Consortium DHCP Client 4.1-ESV-R4
Copyright 2004-2011 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan1/68:7f:74:e6:ab:57
Sending on   LPF/wlan1/68:7f:74:e6:ab:57
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 21

```
and so on.  Not really sure what the interval is, but after 21, its 10, 11, 10, 11, 14, 7, 14, 9, 9, 11, 11, 13, 15, 13, 17.  It eventually says:
```

No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Throughout this, still nothing in dmesg.  The dchp server (little linksys router) is working and assigns addresses to other machines on that network.

After that, I went back to /etc/network/interfaces and disabled the static configuration and uncommented the dhcp one.

When I tried to bring wlan1 down, i get the ole "screw you" again
ifdown wlan1:
```

ifdown: interface wlan1 not configured

``` 

Earlier, sauyon suggested I do:
ifconfig wlan1 down
I assume that succeded, there was no output.  I then figured, why not try to bring it up that way and did:
ifconfig wlan1 up.  Again, no output.  Better than "failed".  In dmesg I get (after the ifconfig wlan1 up):
```

[64063.133866] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[64063.302283] phy10 -> rt2800usb_fill_rxdone: Error - Bad frame size 14645, forcing to 0
[64063.302650] phy10 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[64069.796420] wlan1: authenticate with 00:1e:e5:42:64:a3
[64070.100417] wlan1: send auth to 00:1e:e5:42:64:a3 (try 1/3)
[64070.105761] wlan1: authenticated
[64070.256291] wlan1: associate with 00:1e:e5:42:64:a3 (try 1/3)
[64070.261679] wlan1: RX AssocResp from 00:1e:e5:42:64:a3 (capab=0x411 status=0 aid=2)
[64070.318297] wlan1: associated
[64070.319650] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready

```

ifconfig wlan1:
```

wlan1     Link encap:Ethernet  HWaddr 68:7f:74:e6:ab:57
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:10836 (10.8 KB)

```

Still no luck with pinging google:
ping -I wlan1 google.com:
```

PING google.com (173.194.37.130) from 192.168.1.10 wlan1: 56(84) bytes of data.
From 192.168.1.10 icmp_seq=1 Destination Host Unreachable

```

Same result for the router (192.168.1.1), but I get responses from the adapter's IP, 192.168.1.10.

DHCP should be assigning something between .100 and .200, the .10 address is from the static configuration.  Not really sure how that's happening.

/etc/network/interfaces:
```

allow-hotplug wlan1
iface wlan1 inet dhcp
       wireless-essid my_essid
       wireless-key MY_10_CHAR_HEX_WEP_KEY

```

Wavemon still shows signal strength.

---

### Post by sauyon on 2013-04-14
By the way, it says that your default gateway is 192.168.0.4, is that what you want it to be?

EDIT:
So you know, the reason that you can't just
```
ifdown wlan1
```
is because it was never ifup'd - instead, it was probably configured with network manager.

Also, run
```
ifup -v wlan1
```
with wlan1 down to see exactly what file exists - it'll probably help you :).

---

### Post by Noonien2600 on 2013-04-14
> **sauyon said:**
> By the way, it says that your default gateway is 192.168.0.4, is that what you want it to be?

EDIT:
So you know, the reason that you can't just
```
ifdown wlan1
```
is because it was never ifup'd - instead, it was probably configured with network manager.

Also, run
```
ifup -v wlan1
```
with wlan1 down to see exactly what file exists - it'll probably help you :).

Yes sir, 192.168.0.4 is correct.  That's our lil temp gateway until I get this machine working.  Also, that makes sense about why I can't do ifdown.

Also, not a desktop install (only 4mb video memory, hah).  Don't have network manager installed.

ifup -v wlan1 output:  (seems the apparent hanging was dhclient)
```

Configuring interface wlan1=wlan1 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant

dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.wlan1.pid -lf /var/lib/dhcp/dhclient.wlan1.leases -1 wlan1
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/000resolvconf
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/openssh-server
ssh stop/waiting
ssh start/running, process 5462
run-parts: executing /etc/network/if-up.d/samba
run-parts: executing /etc/network/if-up.d/upstart
run-parts: executing /etc/network/if-up.d/wpasupplicant

```

---

