---
title: "Connection to unsecured (hotel-type) wireless fails at requesting IP"
date: 2009-04-16
forum: Networking &amp; Wireless
---

### Post by eeking on 2009-04-16
HP Pavillion zv5320us
dual booting XP Home and Ubuntu Intrepid

I can successfully connect to the same network in XP, and have properly(?) configured my wireless in Ubuntu to be able to connect to my secured home wireless network.

```
lspci -nn | grep 'Wireless'

02:02.0 Network Controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
```
```
iwconfig wlan0

wlan0     IEEE 802.11bg  ESSID:"Warehouse Row WiFi"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
```
lsmod | grep b43

b43                   131356  0 
rfkill                 17176  3 rfkill_input,b43
mac80211              216820  1 b43
led_class              12164  1 b43
input_polldev          11912  1 b43
ssb                    40580  1 b43
```
```
dmesg | grep b43

[    5.079402] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNK3] -> GSI 17 (level, low) -> IRQ 17
[   24.447806] b43-phy0: Broadcom 4306 WLAN found
[  177.665880] input: b43-phy0 as /devices/virtual/input/input9
[  177.746473] firmware: requesting b43/ucode5.fw
[  177.799536] firmware: requesting b43/pcm5.fw
[  177.891573] firmware: requesting b43/b0g0initvals5.fw
[  177.912542] firmware: requesting b43/b0g0bsinitvals5.fw
[  178.044055] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  178.192976] Registered led device: b43-phy0::tx
[  178.193402] Registered led device: b43-phy0::rx
[  178.193692] Registered led device: b43-phy0::radio
```
```
dmesg | grep wlan

[  179.044099] wlan0: authenticate with AP 00:18:0a:01:23:24
[  179.054322] wlan0: authenticated
[  179.054333] wlan0: associate with AP 00:18:0a:01:23:24
[  179.069796] wlan0: RX AssocResp from 00:18:0a:01:23:24 (capab=0x421 status=0 aid=2)
[  179.069804] wlan0: associated
[  179.071915] wlan0: disassociating by local choice (reason=3)
[  204.896579] wlan0: authenticate with AP 00:18:0a:01:23:24
[  204.898093] wlan0: authenticate with AP 00:18:0a:01:23:24
[  204.904090] wlan0: authenticated
[  204.904104] wlan0: associate with AP 00:18:0a:01:23:24
[  204.921498] wlan0: RX ReassocResp from 00:18:0a:01:23:24 (capab=0x421 status=0 aid=2)
[  204.921516] wlan0: associated
[  250.146791] wlan0: disassociating by local choice (reason=3)
[  250.158187] wlan0: authenticate with AP 00:18:0a:01:23:24
[  250.161182] wlan0: authenticated
[  250.161199] wlan0: associate with AP 00:18:0a:01:23:24
[  250.175223] wlan0: RX AssocResp from 00:18:0a:01:23:24 (capab=0x421 status=0 aid=2)
[  250.175237] wlan0: associated
[  250.177473] wlan0: disassociating by local choice (reason=3)
[  250.973318] wlan0: authenticate with AP 00:18:0a:01:23:24
[  250.974278] wlan0: authenticate with AP 00:18:0a:01:23:24
[  250.984097] wlan0: authenticated
[  250.984109] wlan0: associate with AP 00:18:0a:01:23:24
[  251.004921] wlan0: RX ReassocResp from 00:18:0a:01:23:24 (capab=0x421 status=0 aid=2)
[  251.004932] wlan0: associated
[  296.225128] wlan0: disassociating by local choice (reason=3)
[  296.254832] wlan0: authenticate with AP 00:18:0a:01:23:24
[  296.452037] wlan0: authenticate with AP 00:18:0a:01:23:24
[  296.454150] wlan0: authenticated
[  296.454160] wlan0: associate with AP 00:18:0a:01:23:24
[  296.467217] wlan0: RX AssocResp from 00:18:0a:01:23:24 (capab=0x421 status=0 aid=1)
[  296.467229] wlan0: associated
[  296.467694] wlan0: disassociating by local choice (reason=3)
[  306.052629] wlan0: authenticate with AP 00:18:0a:01:23:24
[  306.054723] wlan0: authenticated
[  306.054735] wlan0: associate with AP 00:18:0a:01:23:24
[  306.060280] wlan0: RX ReassocResp from 00:18:0a:01:23:24 (capab=0x421 status=0 aid=1)
[  306.060293] wlan0: associated
[  326.060069] wlan0: No ProbeResp from current AP 00:18:0a:01:23:24 - assume out of range
[  326.944677] wlan0: authenticate with AP 00:18:0a:01:23:24
[  327.144068] wlan0: authenticate with AP 00:18:0a:01:23:24
[  327.344069] wlan0: authenticate with AP 00:18:0a:01:23:24
[  327.544069] wlan0: authentication with AP 00:18:0a:01:23:24 timed out
[  337.724137] wlan0: authenticate with AP 00:18:0a:01:23:24
[  337.725609] wlan0: authenticate with AP 00:18:0a:01:23:24
[  337.733944] wlan0: authenticated
[  337.733956] wlan0: associate with AP 00:18:0a:01:23:24
[  337.751058] wlan0: RX ReassocResp from 00:18:0a:01:23:24 (capab=0x421 status=0 aid=1)
[  337.751068] wlan0: associated
[  351.278895] wlan0: disassociating by local choice (reason=3)
[  351.308726] wlan0: authenticate with AP 00:18:0a:01:23:24
[  351.315979] wlan0: authenticated
[  351.316000] wlan0: associate with AP 00:18:0a:01:23:24
[  351.516062] wlan0: associate with AP 00:18:0a:01:23:24
[  351.716052] wlan0: associate with AP 00:18:0a:01:23:24
[  351.916055] wlan0: association with AP 00:18:0a:01:23:24 timed out
[  511.993642] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  524.100616] wlan0: authenticate with AP 00:18:0a:01:23:24
[  524.300035] wlan0: authenticate with AP 00:18:0a:01:23:24
[  524.500037] wlan0: authenticate with AP 00:18:0a:01:23:24
[  524.700028] wlan0: authentication with AP 00:18:0a:01:23:24 timed out
[  540.664532] wlan0: authenticate with AP 00:18:0a:01:23:24
[  540.666263] wlan0: authenticate with AP 00:18:0a:01:23:24
[  540.676106] wlan0: authenticated
[  540.676122] wlan0: associate with AP 00:18:0a:01:23:24
[  540.692847] wlan0: RX AssocResp from 00:18:0a:01:23:24 (capab=0x421 status=0 aid=1)
[  540.692858] wlan0: associated
[  540.693624] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  551.336039] wlan0: no IPv6 routers present
[  568.692055] wlan0: No ProbeResp from current AP 00:18:0a:01:23:24 - assume out of range
[  569.589189] wlan0: authenticate with AP 00:18:0a:01:23:24
[  569.590235] wlan0: authenticate with AP 00:18:0a:01:23:24
[  569.788067] wlan0: authenticate with AP 00:18:0a:01:23:24
[  569.988061] wlan0: authenticate with AP 00:18:0a:01:23:24
[  570.188070] wlan0: authentication with AP 00:18:0a:01:23:24 timed out
[  580.369216] wlan0: authenticate with AP 00:18:0a:01:23:24
[  580.370272] wlan0: authenticate with AP 00:18:0a:01:23:24
[  580.568062] wlan0: authenticate with AP 00:18:0a:01:23:24
[  580.768066] wlan0: authenticate with AP 00:18:0a:01:23:24
[  580.968067] wlan0: authentication with AP 00:18:0a:01:23:24 timed out
[  585.917129] wlan0: authenticate with AP 00:18:0a:01:23:24
[  586.116058] wlan0: authenticate with AP 00:18:0a:01:23:24
[  586.316074] wlan0: authenticate with AP 00:18:0a:01:23:24
[  586.322612] wlan0: authenticated
[  586.322626] wlan0: associate with AP 00:18:0a:01:23:24
[  586.330756] wlan0: RX AssocResp from 00:18:0a:01:23:24 (capab=0x421 status=0 aid=1)
[  586.330766] wlan0: associated
[  586.331210] wlan0: disassociating by local choice (reason=3)
[  679.164077] wlan0: No ProbeResp from current AP 00:18:0a:01:23:24 - assume out of range
[  845.379604] wlan0: deauthenticated
```
```
lshw -C network

  *-network:0
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: xx:xx:xx:xx:xx:94
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: xx:xx:xx:xx:xx:5f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: xx:xx:xx:xx:xx:f3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```
```
iwlist wlan0 scan

wlan0     Scan completed :
          Cell 01 - Address: 00:18:0A:01:23:24
                    ESSID:"Warehouse Row WiFi"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/100  Signal level:-77 dBm  Noise level=-66 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000008944a181
                    Extra: Last beacon: 448ms ago
```
```
lsb_release -d

Description:	Ubuntu 8.10
```
```
uname -mr

2.6.27-11-generic i686
```

Granted, the SNR isn't great where I'm sitting, but I reckon if XP can find a signal in there, Ubuntu should be able to. :) But that doesn't seem to be the issue anyhow, since the nm-applet indicates it's negotiating for an IP before failing/disconnecting.

---

### Post by duQuesne86 on 2009-05-31
I'm also running Ubuntu (jaunty jackalope) on an HP Pavillion zv5320us, and as well, having no luck with the wireless. I assume that ubuntu detects the wireless hardware, as there is an empty "wireless networks" heading in the network connections. 

What i think is blocking wireless detection (at least in my case) is the external wireless "power switch" (located directly above the F8 key) which i'd assume functions by controlling the power supplied to the antenna. I make this assumption because even when i had windows on the laptop, it could always see the sireless hardware, the wireless power switch just functioned to empty the available connections. Without the necesary drivers to control this switch (which i've never seen on any other laptop, and which HP doesn't seem willing to furnish for linux users) we're pretty well up a creek as far as the on-board wireless is concerned.

If you have any luck in working on this problem, please post what you did, because i'd love to be able to use the onboard 802.11g.

--duQ

---

### Post by Ayuthia on 2009-05-31
> **duQuesne86 said:**
> I'm also running Ubuntu (jaunty jackalope) on an HP Pavillion zv5320us, and as well, having no luck with the wireless. I assume that ubuntu detects the wireless hardware, as there is an empty "wireless networks" heading in the network connections. 

What i think is blocking wireless detection (at least in my case) is the external wireless "power switch" (located directly above the F8 key) which i'd assume functions by controlling the power supplied to the antenna. I make this assumption because even when i had windows on the laptop, it could always see the sireless hardware, the wireless power switch just functioned to empty the available connections. Without the necesary drivers to control this switch (which i've never seen on any other laptop, and which HP doesn't seem willing to furnish for linux users) we're pretty well up a creek as far as the on-board wireless is concerned.

If you have any luck in working on this problem, please post what you did, because i'd love to be able to use the onboard 802.11g.

--duQ

If you have a working wired connection in Ubuntu, have you tried going into System->Administration->Hardware Drivers and activating the Broadcom driver option?  If so, can you post the results of:
```
dmesg|grep b43
```It will help us see what is happening with the b43 module.

---

