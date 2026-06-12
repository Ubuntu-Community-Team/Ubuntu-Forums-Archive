---
title: "WiFi Intel 5300 Ultimate performance problems"
date: 2011-01-01
forum: Networking &amp; Wireless
---

### Post by spoxta on 2011-01-01
Hi,

I've installed an Intel 5300 Ultimate miniPCIe adapter into my ShuttlePC XS35GT.

The Shuttle came with a RTL8192 which never worked under Ubuntu, so I changed
the card. I also installed 2 extra WLAN antennas into the case, I used the Tyco internal WLAN
antennas, so I have all three antenna connectors.

The card is obviously well supported under Linux using the iwlagn driver module. I changed the corresponding file in /etc/modprobe.d/ so allow the "n" speed (changed the setting to 0).

[..]
options iwlagn 11n_disable=0
[..]

Correctly the card identifies itself being "abgn" capable in iwconfig. (The n does not show if I leave the driver module configuration as it is, i.e. disabling the n capability). 

While I can connect to my network (WPA2 protected), the performance is actually abysmal.

I connect most of the time at 1 Mbps, and then after a while it increases around to 25 or so.

Now this is not due to the signal strength itself, because I can also connect the box with a Netgear WNA3100 (v3, USB) using ndiswrapper and I get consistently around 130 Mbps. 

I would really prefer to use the internal card rather than the ugly USB thingy.

I read in the forums that maybe there could be firmware issues or different firmware versions. I found no way to find and/or load a specific firmware into the card. Any advice here would be appreciated.

Ah yes, I run Ubuntu 10.10 (Maverick) latest updates installed (as of today), kernel 2.6.35-24-generic. The access point is a Netgear WNR3500 (v1), and I also tried with a WNDR3700 (dual band). (The 3700 performs actually worse for some strange reason on both 2.4 and 5 GHz, well no surprise on the 5 GHz since it propagates less through walls, etc.).

Any suggestions to improve the performance of the card including any settings/tricks to try are appreciated. Special firmware? Hidden settings? (iwpriv does not show anything, though), different antennas (already tried many combinations).

Cheers.

---

