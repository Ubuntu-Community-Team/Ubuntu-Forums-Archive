---
title: "Intel 5100AGN wireless connects but cannot ping anything"
date: 2012-05-07
forum: Networking &amp; Wireless
---

### Post by Hansg91 on 2012-05-07
Hello everyone,

Yesterday I decided to upgrade to Ubuntu Precise (12.04 LTS) and everything went sorta smooth, except for my wlan with my home network. It would claim the connection is established, but I could not go online. I experienced some weird stuff about it, which I will just sum up for ease :

[LIST=1][*]I can't ping my gateway or any other computers in the network[*]I have internet when using an external wifi USB dongle[*]In Windows I have internet from the same network, with the same (built in) wifi device[*]On my university I have internet in Ubuntu with the same network device
[/LIST]

So to make a not so long story short, it seems the combination of my home network and my built in wifi card gives me some sort of issue. I did not have this issue on 11.04 though, nor on Windows, so it suggests some kind of driver issue?

I searched and found some similar topics online, but none of them worked for me or they were outdated.

Below is some extra information which may help:

lspci :

```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection

```

iwconfig wlan0 :

```
wlan0     IEEE 802.11abgn  ESSID:"dd-wrt-nd"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:25:9C:CA:7B:3C   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=37/70  Signal level=-73 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:34   Missed beacon:0

```

lsmod | grep 'wl' :
```

iwlwifi               328352  0 
mac80211              506816  3 rt2x00usb,rt2x00lib,iwlwifi
cfg80211              205544  3 rt2x00lib,iwlwifi,mac80211

```

dmesg :

```
[ 3434.540590] wlan0: authenticate with 00:25:9c:ca:7b:3c (try 1)
[ 3434.549061] wlan0: authenticated
[ 3434.552569] wlan0: associate with 00:25:9c:ca:7b:3c (try 1)
[ 3434.558458] wlan0: RX AssocResp from 00:25:9c:ca:7b:3c (capab=0x411 status=0 aid=2)
[ 3434.558463] wlan0: associated
[ 3434.574149] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3443.147263] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = 00:25:9c:ca:7b:3c tid = 6
[ 3445.632049] wlan0: no IPv6 routers present
[ 3498.793426] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = 00:25:9c:ca:7b:3c tid = 0

```

uname -mr
```
3.2.0-23-generic x86_64
```

If there is anything more I can supply, let me know. I'm getting a bit clueless here :)


UPDATE:
Ok that was quick ... I think I fixed it. I installed the drivers from here ([http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)) and that seems to have helped.

---

