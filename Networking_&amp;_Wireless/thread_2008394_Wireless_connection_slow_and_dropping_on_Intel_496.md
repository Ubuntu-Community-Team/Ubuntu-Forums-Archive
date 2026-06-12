---
title: "Wireless connection slow and dropping on Intel 4965 AGN"
date: 2012-06-22
forum: Networking &amp; Wireless
---

### Post by asimic on 2012-06-22
Hello forum,
I am having trouble with wireless on my laptop that uses Intel 4965agn card. Problem is that the connection is very spotty and slow with dropouts occurring *very* often. 
Note that when I run Windows (which I dislike a lot) on the same laptop in the *exact same* location, everything is fast and rock solid. 
I browsed through the old posts and tried some of the suggestions to no avail. Any help would be greatly appreciated.

So far I tried to disable the n mode (no improvement), changed my security to WPA2 only (from WPA+WPA2), disable ipv6 (my router is ipv4 so no change really). 
 
Here are the details:
$ lspci -nnk | grep -iA2 net
```
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
    Subsystem: Toshiba America Info Systems Device [1179:ff50]
    Kernel driver in use: r8169
--
06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)
    Subsystem: Intel Corporation Vaio VGN-SZ79SN_C [8086:1100]
    Kernel driver in use: iwl4965

```$ iwconfig wlan0 
```
wlan0     IEEE 802.11abgn  ESSID:"Brza_Zona"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:2F:F5:F0:84   
          Bit Rate=26 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:119  Invalid misc:83   Missed beacon:0
```$ lsmod | grep iwl
```
iwl4965               117368  0 
iwl_legacy             71134  1 iwl4965
mac80211              436455  2 iwl4965,iwl_legacy
cfg80211              178679  3 iwl4965,iwl_legacy,mac80211

```$ dmesg | grep iwl
```
[    7.566381] iwl4965: Intel(R) Wireless WiFi 4965 driver for Linux, in-tree:
[    7.566385] iwl4965: Copyright(c) 2003-2011 Intel Corporation
[    7.566456] iwl4965 0000:06:00.0: enabling device (0000 -> 0002)
[    7.566468] iwl4965 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    7.566482] iwl4965 0000:06:00.0: setting latency timer to 64
[    7.566516] iwl4965 0000:06:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[    7.605327] iwl4965 0000:06:00.0: device EEPROM VER=0x36, CALIB=0x5
[    7.664058] iwl4965 0000:06:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[    7.664155] iwl4965 0000:06:00.0: irq 45 for MSI/MSI-X
[    8.152949] iwl4965 0000:06:00.0: loaded firmware version 228.61.2.24
[    8.207587] ieee80211 phy0: Selected rate control algorithm 'iwl-4965-rs'
[   45.642017] iwl4965 0000:06:00.0: Aggregation not enabled for tid 0 because load = 0
[  694.076077] iwl4965 0000:06:00.0: iwl4965_tx_agg_start on ra = 00:1b:2f:f5:f0:84 tid = 0
[  968.605818] iwl4965 0000:06:00.0: Aggregation not enabled for tid 4 because load = 1
[ 2178.338335] iwl4965 0000:06:00.0: Aggregation not enabled for tid 0 because load = 0
[ 2183.647048] iwl4965 0000:06:00.0: iwl4965_tx_agg_start on ra = 00:1b:2f:f5:f0:84 tid = 0

```I am running Ubuntu 12.04 LTS (3.2.0-25-generic-pae i686)
Thank you in advance for your shared wisdom.

---

### Post by asimic on 2012-06-24
Bump.
Is there anyone with a suggestion? This is driving me nuts. It makes the laptop unusable.
The connection dropped 2 times while writing this message.
Thanks.

---

### Post by mikewhatever on 2012-07-07
Unfortunately, this is a known, and a long standing, problem with Intel's 4965 wireless card. Intel will probably never fix it, but there is a workaround as described in this thread: [http://ubuntuforums.org/showthread.php?t=1996768&highlight=11n_disable](http://ubuntuforums.org/showthread.php?t=1996768&highlight=11n_disable). 

Note that the driver you have is iwl4965 and not iwkwifi, and that you may also need to configure the router to use the 802.11b mode.

Do  not hesitate to ask if you have any questions.

---

### Post by praseodym on 2012-07-07
@asimic: Which Ubuntuversion do you use? Please show:

> lsb_release -a
uname -a
ifconfig wlan0

---

### Post by JakcV on 2012-07-13
Hi, I have this identical problem. But the problem only exist in Ubuntu 12.04 which I fresh install a few months ago. I have my same machine with Ubuntu 10.04 before with no problem of connection dropping. 

In my previous Ubuntu 10.04, the Wifi connection was very good. Speed ok and never drop (in the exact position). 

Can I use the old iwl4965 module in my Ubuntu 10.04 to replace the module at my 12.04?

---

### Post by asimic on 2012-07-20
Thank you for your replies, I truly appreciate the effort.
The problem solved itself somehow. Well, I played around quite a bit with the router and choosing the channel that has the least amount of interference with neighboring wifi networks. This helped A LOT! Still not as fast and solid as in windows, but quite comparable. 

@mikewhatever
I tried the solution mentioned (disabling the n mode) but to no avail, as I configured my router to run in g mode prior to all of this.

@praseodym
```
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04 LTS
Release:    12.04
Codename:    precise

uname -a
Linux Toshiba-ubuntu 3.2.0-26-generic-pae #41-Ubuntu SMP Thu Jun 14 16:45:14 UTC 2012 i686 i686 i386 GNU/Linux

ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:13:e8:65:5f:29  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:fe65:5f29/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:809827 errors:0 dropped:0 overruns:0 frame:0
          TX packets:755529 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:645788096 (645.7 MB)  TX bytes:450627058 (450.6 MB)

```

---

### Post by Atanas@ on 2012-08-01
Same $%^& here, Ubuntu 12.04 and Debian Wheezy both based on the 3.2.x kernel give:

```
# iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
```

Anyone notice the only 14dBm transmit power above? It should be something like 20.

I tried another WLAN adapter (USB, Atheros based), it defaults to Tx-Power=20dBm and works just fine. Tried lowering it with "iwconfig wlan1 txpower NN" to something below 18 and it also started acting crappy.

Must be some CRDA regression or something. Attempting to bump that up on i4965 fails miserably with the usual mac80211 related error:

```
# iwconfig wlan0 txpower 20
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan0 ; Invalid argument.
```

It seems that it should be possible to set that up to 20 for most countries (or up to 27 for US), but for some reason the driver doesn't allow doing that.

Someone needs to file a kernel bug report I guess...

---

