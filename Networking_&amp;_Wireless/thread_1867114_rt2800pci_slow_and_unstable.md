---
title: "rt2800pci slow and unstable"
date: 2011-10-22
forum: Networking &amp; Wireless
---

### Post by DanielSon2055 on 2011-10-22
Hello all, with the help of the fantastic Chili5558, my wireless is now working on my HP. However it is slow and a little unstable. While I'm on the internet, i have a connection that works albeit a little sluggish. When i go to software center to DL the Flash Plugin i get "Failed to download packages. Check your internet connection"
   I'll post some info below from my terminal.
------------------------------------------------------
daniel@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"linksysnorth"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:F8:72:EA:2F   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:160  Invalid misc:3   Missed beacon:0
----------------------------------------------------------------------------------
daniel@ubuntu:~$ dmesg | grep -e wlan -e rt2
[   18.868242] rt2800pci 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.868257] rt2800pci 0000:03:00.0: setting latency timer to 64
[   18.885594] Registered led device: rt2800pci-phy0::radio
[   18.885645] Registered led device: rt2800pci-phy0::assoc
[   18.885690] Registered led device: rt2800pci-phy0::quality
[   27.213444] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.300184] wlan0: authenticate with 00:18:f8:72:ea:2f (try 1)
[   30.301858] wlan0: authenticated
[   30.316263] wlan0: associate with 00:18:f8:72:ea:2f (try 1)
[   30.318590] wlan0: RX AssocResp from 00:18:f8:72:ea:2f (capab=0x411 status=0 aid=6)
[   30.318596] wlan0: associated
[   30.320138] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   41.904024] wlan0: no IPv6 routers present
[ 2651.316279] ieee80211 phy0: wlan0: No probe response from AP 00:18:f8:72:ea:2f after 500ms, disconnecting.
[ 2664.880580] wlan0: authenticate with 00:18:f8:72:ea:2f (try 1)
[ 2664.883770] wlan0: authenticated
[ 2664.884301] wlan0: associate with 00:18:f8:72:ea:2f (try 1)
[ 2664.887262] wlan0: RX ReassocResp from 00:18:f8:72:ea:2f (capab=0x411 status=0 aid=4)
[ 2664.887272] wlan0: associated
------------------------------------------------------------------------


Any help is much appriciated, thanks in advance!!


Dan

---

### Post by chili555 on 2011-10-22
> No probe response from AP 00:18:f8:72:ea:2f after 500ms, disconnecting.There, clearly, is an example of a drop and reconnect. Does your router have a power setting? Is it at the maximum? Many of us have better luck on a less crowded channel in the router. Have you tried channel 1 or 11?

---

### Post by DanielSon2055 on 2011-10-22
I'm using a router that's a little older,  a Linksys wrt54gts I think...ill try changing     the channel

---

### Post by DanielSon2055 on 2011-10-22
Tried both....no dice. :(

---

### Post by chili555 on 2011-10-23
Please try this:```
sudo gedit /etc/modprobe.d/mac80211.conf
```Add one line:```
options mac80211 probe_wait_ms=1000
```Proofread carefully, save and close gedit. Reboot and let us have your report. If it is still not working as expected, please show us:```
dmesg | grep wlan
```

---

### Post by DanielSon2055 on 2011-10-23
Typed

** sudo gedit /etc/modprobe.d/mac80211.conf **

and a text editor came up. there was nothing in the file that opened, as in no text Should it be blank?

 Was i just to type

 "**options mac80211 probe_wait_ms=1000**"   in that text editor, save and close?

EDIT**********

**I did just as described in this post, rebooted and now it stays connected when i am downloading the Flash Plugin.** Thanks Again Chili! You Rule

---

### Post by DanielSon2055 on 2011-10-23
heres the paste from dmesg | grep wlan


daniel@ubuntu:~$ dmesg | grep wlan
[   21.497181] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.564298] wlan0: authenticate with 00:18:f8:72:ea:2f (try 1)
[   24.565893] wlan0: authenticated
[   24.566291] wlan0: associate with 00:18:f8:72:ea:2f (try 1)
[   24.568428] wlan0: RX AssocResp from 00:18:f8:72:ea:2f (capab=0x411 status=0 aid=6)
[   24.568434] wlan0: associated
[   24.569747] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   34.944215] wlan0: no IPv6 routers present



That look kosher?

---

### Post by chili555 on 2011-10-23
> That look kosher?Yes, as does this:> I did just as described in this post, rebooted and now it stays connected when i am downloading the Flash Plugin. Glad it's working as expected. Please use thread tools at the top and mark Solved.

---

