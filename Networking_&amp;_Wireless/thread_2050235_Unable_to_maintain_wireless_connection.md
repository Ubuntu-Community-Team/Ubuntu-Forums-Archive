---
title: "Unable to maintain wireless connection"
date: 2012-08-30
forum: Networking &amp; Wireless
---

### Post by markcoronado on 2012-08-30
I recently upgraded from 10.04 to 12.04 and when I try to connect to my Linksys BEFW11S4 Ver. 4  I enter my network password and after about 30 seconds it asks for the password again so I enter it again and the process repeats again and again and will never stay connected.

I am able to connect to my neighbours unprotected wireless network with no problem.

For some reason the default connection is my neighbours network and I can't seem to find out how to change that.

My neighbour doesn't care that I connect to his but I would like to connect to mine so I can try to connect to my windows 7 printer. 

Any help would be greatly appreciated.

---

### Post by steeldriver on 2012-08-30
There are some wireless devices / drivers that are buggy with encrypted connections and / or 802.11n - please open a terminal post the output of

```
 lspci -vnn | grep -iA2 'net'
```

so we can see what network hardware you have and suggest accordingly

---

### Post by markcoronado on 2012-08-30
mark@mark-laptop:~$ lspci -vnn | grep -iA2 'net'
03:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0207]
    Flags: bus master, fast devsel, latency 0, IRQ 42
--
06:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
    Subsystem: Foxconn International, Inc. T77H053.00 802.11bgn Wireless Mini PCIe Card [AR9281] [105b:e006]
    Flags: bus master, fast devsel, latency 0, IRQ 17
mark@mark-laptop:~$

---

### Post by steeldriver on 2012-08-30
OK so it may be we need to change the nohwcrypt param, however there are a couple of different ways depending on the driver, so can you also do 

```
lsmod | grep 'ath'
```Thanks

---

### Post by markcoronado on 2012-08-30
mark@mark-laptop:~$ lsmod | grep 'ath'
ath9k                 132390  0 
mac80211              506816  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              411151  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
cfg80211              205544  3 ath9k,mac80211,ath
mark@mark-laptop:~$

---

### Post by steeldriver on 2012-08-30
OK so let's try

```
sudo modprobe -rf ath9k
sudo modprobe ath9k nohwcrypt=1
```If that helps, post back and we can add it to your /etc/modprobe.d/ files to make the change persistent

---

### Post by markcoronado on 2012-08-30
I just ran those 2 commands and it still keeps asking for the network password every 20 seconds.

It has a mind of its own.lol

---

### Post by steeldriver on 2012-08-30
In that case I'm sorry, I probably can't help you - is there anything in the dmesg log to indicate what the problem is?

```
dmesg | grep 'ath9k' 
``````
dmesg | grep -E -e 'eth[0-9]' -e 'wlan[0-9]'
```

---

### Post by markcoronado on 2012-08-30
mark@mark-laptop:~$ dmesg | grep 'ath9k'
[   26.168472] ath9k 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   26.168487] ath9k 0000:06:00.0: setting latency timer to 64
[   26.637710] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   26.720031] Registered led device: ath9k-phy0
[ 9966.245162] ath9k 0000:06:00.0: PCI INT A disabled
[ 9966.245228] ath9k: Driver unloaded
[ 9990.328154] ath9k 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 9990.328194] ath9k 0000:06:00.0: setting latency timer to 64
[ 9990.766342] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[ 9990.776436] Registered led device: ath9k-phy0
mark@mark-laptop:~$ dmesg | grep -E -e 'eth[0-9]' -e 'wlan[0-9]'
[    1.757796] tg3 0000:03:00.0: eth0: Tigon3 [partno(BCM95784M) rev 5784100] (PCI Express) MAC address 00:26:2d:57:c0:84
[    1.757802] tg3 0000:03:00.0: eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.757806] tg3 0000:03:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.757809] tg3 0000:03:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   25.721232] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.528915] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.530101] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.573314] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.573856] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.989536] wlan0: authenticate with 00:0f:b3:9f:16:a1 (try 1)
[   31.991452] wlan0: authenticated
[   32.027164] wlan0: associate with 00:0f:b3:9f:16:a1 (try 1)
[   32.029694] wlan0: RX AssocResp from 00:0f:b3:9f:16:a1 (capab=0x421 status=0 aid=2)
[   32.029698] wlan0: associated
[   32.030561] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   43.000051] wlan0: no IPv6 routers present
[ 1274.009794] wlan0: deauthenticating from 00:0f:b3:9f:16:a1 by local choice (reason=3)
[ 1289.150044] wlan0: authenticate with 00:0c:41:3e:2a:7c (try 1)
[ 1289.152284] wlan0: authenticated
[ 1289.152854] wlan0: associate with 00:0c:41:3e:2a:7c (try 1)
[ 1289.154980] wlan0: RX AssocResp from 00:0c:41:3e:2a:7c (capab=0x15 status=0 aid=2)
[ 1289.154983] wlan0: associated
[ 1299.808095] wlan0: no IPv6 routers present
[ 1334.216915] wlan0: deauthenticating from 00:0c:41:3e:2a:7c by local choice (reason=3)
[ 1338.010101] wlan0: authenticate with 00:0f:b3:9f:16:a1 (try 1)
[ 1338.012073] wlan0: authenticated
[ 1338.012766] wlan0: associate with 00:0f:b3:9f:16:a1 (try 1)
[ 1338.014995] wlan0: RX AssocResp from 00:0f:b3:9f:16:a1 (capab=0x421 status=0 aid=2)
[ 1338.015008] wlan0: associated
[ 1348.336081] wlan0: no IPv6 routers present
[ 1424.456618] wlan0: deauthenticating from 00:0f:b3:9f:16:a1 by local choice (reason=3)
[ 1425.743713] wlan0: authenticate with 00:0c:41:3e:2a:7c (try 1)
[ 1425.745827] wlan0: authenticated
[ 1425.793758] wlan0: associate with 00:0c:41:3e:2a:7c (try 1)
[ 1425.796682] wlan0: RX AssocResp from 00:0c:41:3e:2a:7c (capab=0x15 status=0 aid=3)
[ 1425.796688] wlan0: associated
[ 1436.376036] wlan0: no IPv6 routers present
[ 1471.218911] wlan0: deauthenticating from 00:0c:41:3e:2a:7c by local choice (reason=3)
[ 1475.014103] wlan0: authenticate with 00:0f:b3:9f:16:a1 (try 1)
[ 1475.016962] wlan0: authenticated
[ 1475.055438] wlan0: associate with 00:0f:b3:9f:16:a1 (try 1)
[ 1475.057855] wlan0: RX AssocResp from 00:0f:b3:9f:16:a1 (capab=0x421 status=0 aid=2)
[ 1475.057863] wlan0: associated
[ 1485.232058] wlan0: no IPv6 routers present
[ 1675.971549] wlan0: deauthenticating from 00:0f:b3:9f:16:a1 by local choice (reason=3)
[ 1677.213042] wlan0: authenticate with 00:0c:41:3e:2a:7c (try 1)
[ 1677.215332] wlan0: authenticated
[ 1677.215849] wlan0: associate with 00:0c:41:3e:2a:7c (try 1)
[ 1677.218027] wlan0: RX AssocResp from 00:0c:41:3e:2a:7c (capab=0x15 status=0 aid=4)
[ 1677.218031] wlan0: associated
[ 1687.776083] wlan0: no IPv6 routers present
[ 1722.216180] wlan0: deauthenticating from 00:0c:41:3e:2a:7c by local choice (reason=3)
[ 1726.007840] wlan0: authenticate with 00:0f:b3:9f:16:a1 (try 1)
[ 1726.009841] wlan0: authenticated
[ 1726.046921] wlan0: associate with 00:0f:b3:9f:16:a1 (try 1)
[ 1726.049174] wlan0: RX AssocResp from 00:0f:b3:9f:16:a1 (capab=0x421 status=0 aid=2)
[ 1726.049178] wlan0: associated
[ 1736.176071] wlan0: no IPv6 routers present
[ 1736.709646] wlan0: deauthenticating from 00:0f:b3:9f:16:a1 by local choice (reason=3)
[ 1794.862521] wlan0: authenticate with 00:0c:41:3e:2a:7c (try 1)
[ 1794.864553] wlan0: authenticated
[ 1794.904142] wlan0: associate with 00:0c:41:3e:2a:7c (try 1)
[ 1794.906316] wlan0: RX AssocResp from 00:0c:41:3e:2a:7c (capab=0x15 status=0 aid=5)
[ 1794.906319] wlan0: associated
[ 1805.864074] wlan0: no IPv6 routers present
[ 1815.055788] wlan0: deauthenticating from 00:0c:41:3e:2a:7c by local choice (reason=3)
[ 1833.406626] wlan0: authenticate with 00:0c:41:3e:2a:7c (try 1)
[ 1833.408738] wlan0: authenticated
[ 1833.429030] wlan0: associate with 00:0c:41:3e:2a:7c (try 1)
[ 1833.431623] wlan0: RX ReassocResp from 00:0c:41:3e:2a:7c (capab=0x15 status=0 aid=6)
[ 1833.431629] wlan0: associated
[ 1843.904063] wlan0: no IPv6 routers present
[ 1854.064811] wlan0: deauthenticating from 00:0c:41:3e:2a:7c by local choice (reason=3)
[ 1859.917765] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1864.026980] wlan0: authenticate with 00:0f:b3:9f:16:a1 (try 1)
[ 1864.032868] wlan0: authenticated
[ 1864.033386] wlan0: associate with 00:0f:b3:9f:16:a1 (try 1)
[ 1864.035668] wlan0: RX AssocResp from 00:0f:b3:9f:16:a1 (capab=0x421 status=0 aid=2)
[ 1864.035674] wlan0: associated
[ 1864.036673] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1874.344054] wlan0: no IPv6 routers present
[ 9966.128465] wlan0: deauthenticating from 00:0f:b3:9f:16:a1 by local choice (reason=3)
[ 9990.831499] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9990.835074] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9993.594134] wlan0: authenticate with 00:0f:b3:9f:16:a1 (try 1)
[ 9993.596137] wlan0: authenticated
[ 9993.596690] wlan0: associate with 00:0f:b3:9f:16:a1 (try 1)
[ 9993.599180] wlan0: RX AssocResp from 00:0f:b3:9f:16:a1 (capab=0x421 status=0 aid=2)
[ 9993.599193] wlan0: associated
[ 9993.601935] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[10004.496078] wlan0: no IPv6 routers present
[10024.485745] wlan0: deauthenticating from 00:0f:b3:9f:16:a1 by local choice (reason=3)
[10048.562735] wlan0: authenticate with 00:0c:41:3e:2a:7c (try 1)
[10048.564860] wlan0: authenticated
[10048.604582] wlan0: associate with 00:0c:41:3e:2a:7c (try 1)
[10048.606794] wlan0: RX AssocResp from 00:0c:41:3e:2a:7c (capab=0x15 status=0 aid=7)
[10048.606801] wlan0: associated
[10058.672091] wlan0: no IPv6 routers present
[10069.054740] wlan0: deauthenticating from 00:0c:41:3e:2a:7c by local choice (reason=3)
[10087.513088] wlan0: authenticate with 00:0c:41:3e:2a:7c (try 1)
[10087.515189] wlan0: authenticated
[10087.547064] wlan0: associate with 00:0c:41:3e:2a:7c (try 1)
[10087.549362] wlan0: RX ReassocResp from 00:0c:41:3e:2a:7c (capab=0x15 status=0 aid=8)
[10087.549366] wlan0: associated
[10095.012399] wlan0: authenticate with 00:0c:41:3e:2a:7c (try 1)
[10095.014513] wlan0: authenticated
[10095.034157] wlan0: associate with 00:0c:41:3e:2a:7c (try 1)
[10095.036318] wlan0: RX ReassocResp from 00:0c:41:3e:2a:7c (capab=0x15 status=0 aid=9)
[10095.036321] wlan0: associated
[10098.400095] wlan0: no IPv6 routers present
[10108.048215] wlan0: deauthenticating from 00:0c:41:3e:2a:7c by local choice (reason=3)
[10113.255954] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10117.024562] wlan0: authenticate with 00:0f:b3:9f:16:a1 (try 1)
[10117.028196] wlan0: authenticated
[10117.028767] wlan0: associate with 00:0f:b3:9f:16:a1 (try 1)
[10117.030990] wlan0: RX AssocResp from 00:0f:b3:9f:16:a1 (capab=0x421 status=0 aid=2)
[10117.030996] wlan0: associated
[10117.038838] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[10128.032088] wlan0: no IPv6 routers present
mark@mark-laptop:~$

---

### Post by steeldriver on 2012-08-30
Are you by any chance using WEP? if so would it be possible for you to try with WPA? It might also be worth going into the connection manager and editing your wireless connection setting IPV6 to 'Ignore'

BTW what is your kernel version?

```
uname -r
```

---

### Post by markcoronado on 2012-08-30
Thanks for all your help steeldriver.

mark@mark-laptop:~$ uname -r
3.2.0-29-generic
mark@mark-laptop:~$ 

I managed to get it working by clicking on Forget Network and entering the info again for my Linksys.

Yes it is  WEP but it seems to be working correctly now.

Now if I can get my printer to print a test page I'll be a happy camper.

When I try to print a test page the print job just stops and if I restart it it stops again.

I probably have it set up wrong, the printer is connected to my desktop which is a Windows 7 machine.

---

### Post by markcoronado on 2012-08-30
I'm going to mark this thread solved.

I just got my Windows 7 printer working by deleting it and reinstalling it using the instructions from this site.
[http://xxx.liberiangeek.net/2012/04/setup-windows-printer-in-ubuntu-12-04-precise-pangolin/](http://xxx.liberiangeek.net/2012/04/setup-windows-printer-in-ubuntu-12-04-precise-pangolin/)

I'm not sure if I'm allowed to post live links so just change the xxx to www.

Thanks and I hope this will help others that may have the same problem.

---

### Post by steeldriver on 2012-08-30
OK glad you got it working

For the record (and in case anyone else stumbles on this thread while searching) the reason I was asking about WEP and kernel version is that there do seem to be reports of a kernel regression bug affecting WEP on ath9k

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/923512](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/923512)

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=659521](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=659521)

---

