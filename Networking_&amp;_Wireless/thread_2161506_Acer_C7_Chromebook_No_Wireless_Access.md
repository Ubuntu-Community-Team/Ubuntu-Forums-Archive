---
title: "Acer C7 Chromebook No Wireless Access"
date: 2013-07-10
forum: Networking &amp; Wireless
---

### Post by Cero121 on 2013-07-10
Hi, I have an Acer C7 Chromebook, which I dual-booted with Ubuntu 12.04. Everything works, but when I try to using a wireless connecion, there is no internet access. If I try to connect with an Ethernet cable, the internet works perfectly. Does anyone have the same problem? Has anyone solved it? Please reply! Thanks in advance.

---

### Post by praseodym on 2013-07-11
Please open a terminal with CTRL+ALT+T and show the outputs of these commands without the cable being plugged:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
ifconfig -a
cat /etc/resolv.conf
route -n
```

---

### Post by Cero121 on 2013-07-11
**uname -a**: Linux ChrUbuntu 3.4.0 #1 SMP Sun Aug 26 19:17:55 EDT 2012 x86_64 x86_64 x86_64 GNU/Linux




**lspci -nnk | grep -iA2 net**:


01:00.0 Network controller [0280]: Atheros Communications Inc. AR9462 Wireless Network Adapter [168c:0034] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e052]
	Kernel driver in use: ath9k
--
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:0742]
	Kernel driver in use: tg3
--
02:00.1 SD Host controller [0805]: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader [14e4:16bc] (rev 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:0742]
	Kernel driver in use: sdhci-pci




**lsusb**:  Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0489:e04e Foxconn / Hon Hai 
Bus 001 Device 004: ID 04f2:b336 Chicony Electronics Co., Ltd 




**lsmod**: Module                  Size  Used by
fuse                   59885  2 
rfcomm                 25259  0 
snd_hda_codec_hdmi     29062  1 
snd_hda_codec_realtek    49177  1 
memconsole             12352  0 
uvcvideo               59368  0 
videodev               81368  1 uvcvideo
videobuf2_core         25280  1 uvcvideo
joydev                 16409  0 
videobuf2_vmalloc      12313  1 uvcvideo
videobuf2_memops       12475  1 videobuf2_vmalloc
btusb                  16409  0 
bluetooth             143138  13 rfcomm,btusb
ath9k                 118119  0 
mac80211              318094  1 ath9k
ath9k_common           12689  1 ath9k
ath9k_hw              351731  2 ath9k,ath9k_common
ath                    21105  3 ath9k,ath9k_common,ath9k_hw
rtc_cmos               16409  0 
cfg80211              141223  3 ath9k,mac80211,ath
snd_hda_intel          24601  3 
snd_hda_codec          71435  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              12351  1 snd_hda_codec
sdhci_pci              16409  0 
snd_pcm                61468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
sdhci                  25037  1 sdhci_pci
mmc_core               71579  2 sdhci_pci,sdhci
tg3                   118809  0 
snd_timer              21055  1 snd_pcm
snd_page_alloc         12757  2 snd_hda_intel,snd_pcm
nm10_gpio              12313  0 






**iwconfig**: eth1      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"wireless"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:22:3F:7A:74:3B   
          Bit Rate=1 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-30 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:25   Missed beacon:0




**ifconfig -a**:  eth1      Link encap:Ethernet  HWaddr 20:89:84:bd:ef:5e  
          inet6 addr: fe80::2289:84ff:febd:ef5e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5717 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4416 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5777537 (5.7 MB)  TX bytes:779978 (779.9 KB)
          Interrupt:18 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1020 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1020 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:88396 (88.3 KB)  TX bytes:88396 (88.3 KB)


wlan0     Link encap:Ethernet  HWaddr bc:85:56:38:f9:87  
          inet6 addr: fe80::be85:56ff:fe38:f987/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:146 errors:0 dropped:0 overruns:0 frame:0
          TX packets:332 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23089 (23.0 KB)  TX bytes:80654 (80.6 KB)




**cat /etc/resolv.conf**: # Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1






**route -n**: Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

---

### Post by praseodym on 2013-07-12
Deactivate the power management and the hardware encryption:
```

echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
sudo iwconfig wlan0 power off
```

---

### Post by Cero121 on 2013-07-12
Thank you soooo much! It worked!

---

