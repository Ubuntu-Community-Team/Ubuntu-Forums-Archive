---
title: "Can't connect to detected network."
date: 2012-05-17
forum: Networking &amp; Wireless
---

### Post by Seiken Ai on 2012-05-17
I have problems with my Benq U102 wireless, it catch ap signals well but never build any connection. It was fine under Ubuntu 10.04 and someday(maybe since some update I can't remember) broke. I have tried the default STA driver and the b43-fwcutter solution and reinstalled with Ubuntu 9.10, 10.04, 12.04 , Mint 12, both not work. I also plugged an USB wireless card to test and same, when the ethernet works fine. Under Windows XP everything is fine. Now it's an brand new Ubuntu 12.04 installation again, I need help to solve this problem.

lspci info:
> 01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:04ac]

ifconfig info
> eth2      Link encap:Ethernet  HWaddr 00:23:08:b7:96:87  
          inet6 addr: fe80::223:8ff:feb7:9687/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:131 errors:0 dropped:0 overruns:0 frame:19117
          TX packets:1769 errors:944 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13758 (13.7 KB)  TX bytes:394411 (394.4 KB)
          Interrupt:16frame:0

---

### Post by chili555 on 2012-05-17
Let's see what's happening under the hood. Please post:> lsmod | grep -e b43 -e wl
dmesg | grep -e b43 -e wlThere are probably a couple of ways to get this card going, we need to narrow down the best.

Thanks.

---

### Post by Seiken Ai on 2012-05-17
lsmod | grep -e b43 -e wl
> wl                   2646601  0
lib80211               14040  2 lib80211_crypt_tkip,wl

dmesg | grep -e b43 -e wl
> [   12.284189] wl: module license 'MIXED/Proprietary' taints kernel.
[   12.415679] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.415700] wl 0000:01:00.0: setting latency timer to 64
[   18.390451] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.397118] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.641321] wlan0: direct probe to 48:5b:39:bd:f1:27 (try 1/3)
[   23.643431] wlan0: direct probe responded
[   23.648226] wlan0: authenticate with 48:5b:39:bd:f1:27 (try 1)
[   23.651965] wlan0: authenticated
[   23.893454] wlan0: associate with 48:5b:39:bd:f1:27 (try 1)
[   23.895819] wlan0: RX AssocResp from 48:5b:39:bd:f1:27 (capab=0x431 status=0 aid=2)
[   23.895834] wlan0: associated
[   23.900268] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   34.144070] wlan0: no IPv6 routers present
[   69.213047] wlan0: deauthenticating from 48:5b:39:bd:f1:27 by local choice (reason=3)
[   74.233343] wlan0: authenticate with 48:5b:39:bd:f1:27 (try 1)
[   74.235324] wlan0: authenticated
[   74.357318] wlan0: associate with 48:5b:39:bd:f1:27 (try 1)
[   74.359241] wlan0: RX ReassocResp from 48:5b:39:bd:f1:27 (capab=0x431 status=0 aid=2)
[   74.359257] wlan0: associated
[   84.768067] wlan0: no IPv6 routers present
[  120.215182] wlan0: deauthenticating from 48:5b:39:bd:f1:27 by local choice (reason=3)
[  125.293492] wlan0: authenticate with 48:5b:39:bd:f1:27 (try 1)
[  125.295174] wlan0: authenticated
[  125.421517] wlan0: associate with 48:5b:39:bd:f1:27 (try 1)
[  125.424008] wlan0: RX ReassocResp from 48:5b:39:bd:f1:27 (capab=0x431 status=0 aid=2)
[  125.424101] wlan0: associated
[  136.448128] wlan0: no IPv6 routers present
[  171.215585] wlan0: deauthenticating from 48:5b:39:bd:f1:27 by local choice (reason=3)
[  176.257387] wlan0: authenticate with 48:5b:39:bd:f1:27 (try 1)
[  176.260273] wlan0: authenticated
[  176.393659] wlan0: associate with 48:5b:39:bd:f1:27 (try 1)
[  176.396714] wlan0: RX ReassocResp from 48:5b:39:bd:f1:27 (capab=0x431 status=0 aid=2)
[  176.396728] wlan0: associated
[  187.352058] wlan0: no IPv6 routers present
[  222.221718] wlan0: deauthenticating from 48:5b:39:bd:f1:27 by local choice (reason=3)

---

### Post by chili555 on 2012-05-17
Let's try b43:```
sudo modprobe -r wl
sudo modprobe b43
dmesg | grep b43
```Look for activity after the 222.xx timestamp. Since it's an LP-PHY chipset, I wonder if it might work better with the lp-phy firmware and b43. We don't see a lot of these so we need to experiment just a bit.> Broadcom Corporation BCM4312 802.11b/g [COLOR="Red"]LP-PHY[/COLOR] [14e4:4315] 

---

### Post by Seiken Ai on 2012-05-17
I install firmware-b43-lpphy-installer from apt-get and do your suggest. I got below:

dmesg | grep b43
> [  142.339281] b43-pci-bridge 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  142.339322] b43-pci-bridge 0000:01:00.0: setting latency timer to 64
[  142.647404] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[  142.825758] Registered led device: b43-phy0::tx
[  142.828963] Registered led device: b43-phy0::rx
[  142.829075] Registered led device: b43-phy0::radio
[  143.160155] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  148.724301] b43-phy0: Radio hardware status changed to DISABLED
[  148.728828] b43-phy0: Radio turned on by software
[  148.728841] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[  193.828236] b43-phy0: Radio hardware status changed to ENABLED
[  194.020204] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)

I still have problem after this.

dmesg | grep -e b43 -e wl
> [  199.551492] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  202.986774] wlan0: authenticate with 84:c9:b2:75:be:b9 (try 1)
[  202.997735] wlan0: authenticated
[  202.998738] wlan0: associate with 84:c9:b2:75:be:b9 (try 1)
[  203.196089] wlan0: associate with 84:c9:b2:75:be:b9 (try 2)
[  203.209267] wlan0: RX AssocResp from 84:c9:b2:75:be:b9 (capab=0x421 status=0 aid=1)
[  203.209279] wlan0: associated
[  203.213415] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  206.963789] wlan0: deauthenticating from 84:c9:b2:75:be:b9 by local choice (reason=3)
[  207.908307] wlan0: authenticate with 48:5b:39:bd:f1:27 (try 1)
[  207.909814] wlan0: authenticated
[  207.932226] wlan0: associate with 48:5b:39:bd:f1:27 (try 1)
[  207.934121] wlan0: RX AssocResp from 48:5b:39:bd:f1:27 (capab=0x431 status=0 aid=1)
[  207.934144] wlan0: associated
[  218.416212] wlan0: no IPv6 routers present
[  253.226623] wlan0: deauthenticating from 48:5b:39:bd:f1:27 by local choice (reason=3)
[  257.348323] wlan0: authenticate with 84:c9:b2:75:be:b9 (try 1)
[  257.364402] wlan0: authenticated
[  257.388225] wlan0: associate with 84:c9:b2:75:be:b9 (try 1)
[  257.588127] wlan0: associate with 84:c9:b2:75:be:b9 (try 2)
[  257.788154] wlan0: associate with 84:c9:b2:75:be:b9 (try 3)
[  257.800314] wlan0: RX AssocResp from 84:c9:b2:75:be:b9 (capab=0x421 status=0 aid=1)
[  257.800338] wlan0: associated
[  268.704211] wlan0: no IPv6 routers present
[  303.229398] wlan0: deauthenticating from 84:c9:b2:75:be:b9 by local choice (reason=3)

---

### Post by chili555 on 2012-05-17
In post #3, the dmesg timestamp was 222.221718. So may I assume that this is before you switched to b43:> [ 199.551492] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 202.986774] wlan0: authenticate with 84:c9:b2:75:be:b9 (try 1)
[ 202.997735] wlan0: authenticated
[ 202.998738] wlan0: associate with 84:c9:b2:75:be:b9 (try 1)
[ 203.196089] wlan0: associate with 84:c9:b2:75:be:b9 (try 2)
[ 203.209267] wlan0: RX AssocResp from 84:c9:b2:75:be:b9 (capab=0x421 status=0 aid=1)
[ 203.209279] wlan0: associated
[ 203.213415] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 206.963789] wlan0: deauthenticating from 84:c9:b2:75:be:b9 by local choice (reason=3)
[ 207.908307] wlan0: authenticate with 48:5b:39:bd:f1:27 (try 1)
[ 207.909814] wlan0: authenticated
[ 207.932226] wlan0: associate with 48:5b:39:bd:f1:27 (try 1)
[ 207.934121] wlan0: RX AssocResp from 48:5b:39:bd:f1:27 (capab=0x431 status=0 aid=1)
[ 207.934144] wlan0: associated
[ 218.416212] wlan0: no IPv6 routers presentThat looks like you were actually connected just fine. Is that correct?

And then this is *after* b43 and firmware, correct?> [ 253.226623] wlan0: deauthenticating from 48:5b:39:bd:f1:27 by local choice (reason=3)
[ 257.348323] wlan0: authenticate with 84:c9:b2:75:be:b9 (try 1)
[ 257.364402] wlan0: authenticated
[ 257.388225] wlan0: associate with 84:c9:b2:75:be:b9 (try 1)
[ 257.588127] wlan0: associate with 84:c9:b2:75:be:b9 (try 2)
[ 257.788154] wlan0: associate with 84:c9:b2:75:be:b9 (try 3)
[ 257.800314] wlan0: RX AssocResp from 84:c9:b2:75:be:b9 (capab=0x421 status=0 aid=1)
[ 257.800338] wlan0: associated  [COLOR="Red"]<---looks perfect[/COLOR]
[ 268.704211] wlan0: no IPv6 routers present
[ 303.229398] wlan0: deauthenticating from 84:c9:b2:75:be:b9 by local choice (reason=3)  [COLOR="Red"]<---looks bad[/COLOR]Are all these attempts with the ethernet cable detached? Network Manager is designed to disallow a wireless connection if wired is available.

Is your router set to WPA and WPA2 mixed mode? That's difficult for wpa_supplicant. WPA2 only is preferred.

---

### Post by Seiken Ai on 2012-05-18
I have rebooted my notebook so the timestamp restarted(the logs in post #5 are actually continous).

My router was in WEP mode, now I reset it to no encryption and still have same problem(always associate and then deauthenticate for reason 3). I also tried solution decribed [here]("http://ubuntuforums.org/showthread.php?t=1266620") which modprobe b43 with PIO mode, still have same problem.

I wonder if this possible a problem before wireless driver? Since my USB wireless card is RTL8187(pretty common) and have totally same issue.

---

### Post by chili555 on 2012-05-18
> I wonder if this possible a problem before wireless driver? I'm fairly certain it is. The b43/ssb suite is usually pretty reliable and trouble-free. There are two suspects, wpa_supplicant and Network Manager. You could certainly undo any changes you made, either in the NM gui or by editing configuration files. You could also go into Synaptic package manager and mark both for re-installation. You could also remove NM and install Wicd.

---

