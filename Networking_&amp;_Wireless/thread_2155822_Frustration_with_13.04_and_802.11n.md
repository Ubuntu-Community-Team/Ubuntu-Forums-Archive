---
title: "Frustration with 13.04 and 802.11n"
date: 2013-06-19
forum: Networking &amp; Wireless
---

### Post by mbott on 2013-06-19
I've been working to correct the very poor performance of my desktop running 13.04 and I'm just not making any headway.  Network manager reports a link speed of 144 Mb/s but my throughput barely breaks 200 Kbps at best.  Hardware is the Netis WF-2113 and the system is an Asus H87M-Plus motherboard.  CPU is a new Intel i5.  My router is a Belkin N600 DB.

 lspci -nnk | grep -iA2 net:
```
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 0c)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8554]
	Kernel driver in use: r8169
--
06:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8178] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8178]
	Kernel driver in use: rtl8192ce
```

 lsmod:
```
Module                  Size  Used by
joydev                 17377  0 
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             23479  0 
vboxdrv               320372  3 vboxnetadp,vboxnetflt,vboxpci
rfcomm                 42641  0 
bnep                   18036  2 
bluetooth             228619  10 bnep,rfcomm
snd_hda_codec_realtek    78399  1 
snd_hda_codec_hdmi     36913  1 
arc4                   12615  2 
snd_hda_intel          39619  5 
coretemp               13355  0 
kvm_intel             132891  0 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
kvm                   443165  1 kvm_intel
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
ghash_clmulni_intel    13259  0 
aesni_intel            55399  2 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
eeepc_wmi              13151  0 
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
asus_wmi               24213  1 eeepc_wmi
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
sparse_keymap          13890  1 asus_wmi
ppdev                  17073  0 
wmi                    19070  1 asus_wmi
parport_pc             28152  1 
rtl8192ce              53594  0 
rtlwifi                79673  1 rtl8192ce
i915                  600396  3 
rtl8192c_common        48779  1 rtl8192ce
mac80211              606457  3 rtlwifi,rtl8192c_common,rtl8192ce
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
mac_hid                13205  0 
video                  19390  2 i915,asus_wmi
drm_kms_helper         49394  1 i915
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
drm                   286028  4 i915,drm_kms_helper
snd                    68876  20 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
i2c_algo_bit           13413  1 i915
soundcore              12680  1 snd
microcode              22881  0 
cfg80211              510937  2 mac80211,rtlwifi
lpc_ich                17061  0 
psmouse                95870  0 
serio_raw              13215  0 
lp                     17759  0 
mei                    41158  0 
parport                46345  3 lp,ppdev,parport_pc
hid_logitech_dj        18604  0 
usbhid                 47074  1 hid_logitech_dj
hid                   101002  2 usbhid,hid_logitech_dj
usb_storage            57204  0 
r8169                  67446  0 
ahci                   25731  2 
libahci                31364  1 ahci
```

 modinfo rtl8192ce:
```
filename:       /lib/modules/3.8.0-25-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     B41EC2D43683C181DF50FB6
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.8.0-25-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
```

 iwconfig:
```
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"cz_2075"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 08:86:3B:57:F2:85   
          Bit Rate=144.4 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:172   Missed beacon:0
```

 sudo iwlist scan:
 
```
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 08:86:3B:57:F2:85
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"cz_2075"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a844fff59
                    Extra: Last beacon: 1365200ms ago
                    IE: Unknown: 0007637A5F32303735
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180202F0040000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 08:86:3B:57:F2:85
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ad5a9d183
                    Extra: Last beacon: 512ms ago
                    IE: Unknown: 000700000000000000
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180203F0040000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 00:13:10:2E:4C:85
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000828089f185
                    Extra: Last beacon: 580ms ago
                    IE: Unknown: 000D00000000000000000000000000
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018010003
```

 ifconfig -a:
```
eth0      Link encap:Ethernet  HWaddr 60:a4:4c:cb:4d:26  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:652 errors:0 dropped:0 overruns:0 frame:0
          TX packets:652 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:69290 (69.2 KB)  TX bytes:69290 (69.2 KB)

wlan0     Link encap:Ethernet  HWaddr 08:10:74:da:9a:16  
          inet addr:192.168.2.19  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a10:74ff:feda:9a16/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3704 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3209 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3142079 (3.1 MB)  TX bytes:440968 (440.9 KB)
```

 dmesg | grep 8192:
```
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88041fa00000 s85056 r8192 d21440 u524288
[    0.000000] pcpu-alloc: s85056 r8192 d21440 u524288 alloc=1*2097152
[    0.154979] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.155015] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    8.710025] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
```

All suggestions appreciated.

Thanks!

-- 
Mike

---

### Post by chili555 on 2013-06-19
Are there any clues here?```
dmesg | grep -e rtl -e cfg80211
sudo iw reg get
ping -c3 www.google.com
ping -c3 8.8.8.8
```Thanks.

---

### Post by mbott on 2013-06-19
dmesg | grep -e rtl -e cfg80211:
```
[    8.656100] cfg80211: Calling CRDA to update world regulatory domain
[    8.675925] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[    8.713645] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    8.713754] rtlwifi: wireless switch is on
[    8.792660] cfg80211: World regulatory domain updated:
[    8.792662] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    8.792663] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.792664] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.792665] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.792666] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.792666] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.792670] cfg80211: Calling CRDA for country: EC
[    8.900188] cfg80211: Regulatory domain changed to country: EC
[    8.900189] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    8.900190] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[    8.900191] cfg80211:   (5170000 KHz - 5250000 KHz @ 20000 KHz), (300 mBi, 1700 mBm)
[    8.900192] cfg80211:   (5250000 KHz - 5330000 KHz @ 20000 KHz), (300 mBi, 2300 mBm)
[    8.900192] cfg80211:   (5735000 KHz - 5835000 KHz @ 20000 KHz), (300 mBi, 3000 mBm)
```

Ecuador?  Would like to visit some time but Central Ohio is just a bit north of there ... by about 3,000 miles.

sudo iw reg get:
```
country EC:
	(2402 - 2482 @ 40), (N/A, 20)
	(5170 - 5250 @ 20), (3, 17)
	(5250 - 5330 @ 20), (3, 23), DFS
	(5735 - 5835 @ 20), (3, 30)
```

ping -c3 [www.google.com:](www.google.com:)
```
PING www.google.com (74.125.227.48) 56(84) bytes of data.
64 bytes from dfw06s06-in-f16.1e100.net (74.125.227.48): icmp_req=1 ttl=51 time=43.1 ms
64 bytes from dfw06s06-in-f16.1e100.net (74.125.227.48): icmp_req=2 ttl=51 time=41.6 ms
64 bytes from dfw06s06-in-f16.1e100.net (74.125.227.48): icmp_req=3 ttl=51 time=41.2 ms

--- www.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 41.200/41.991/43.121/0.836 ms
```

ping -c3 8.8.8.8:
```
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=46 time=437 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=46 time=153 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=46 time=31.5 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 31.553/207.516/437.883/170.286 ms
```

---

### Post by chili555 on 2013-06-19
Please try:```
sudo iw reg set US
```Now try again:```
ping -c3 8.8.8.8
```Those were pretty sad times:> PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=46 time=[COLOR="#FF0000"]437 ms[/COLOR]
64 bytes from 8.8.8.8: icmp_req=2 ttl=46 time=153 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=46 time=31.5 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 31.553/207.516/437.883/170.286 msLet's also try:```
sudo modprobe -r rtl8192ce
sudo modprobe rtl8192ce ips=0
ping -c3 8.8.8.8
```If it helps, we'll write a file and make it persistent.

---

### Post by mbott on 2013-06-19
Came across the "iw reg set US" earlier this evening and it appears to have made a difference in the ping results.

ping -c3 8.8.8.8:
```
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=46 time=31.9 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=46 time=32.3 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=46 time=31.1 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 31.136/31.783/32.309/0.528 ms
```

**However**, something else has now changed.  As I've been run these results, I've also been running a speed test before and after to help insure we were dealing with apples-to-apples comparisons.  Just as I was getting ready to do the modprobe, my speed test results tanked so I don't feel going further will be of any use until the speed test results improve.  Chili, thanks for the help so far and I'll reach out when we can proceed.

Here is a sample of what I was seeing:

ping -c3 8.8.8.8
```
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=2 ttl=46 time=207 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=46 time=40.5 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 2 received, 33% packet loss, time 2008ms
rtt min/avg/max/mdev = 40.597/123.957/207.318/83.361 ms
```

-- 
Mike

---

### Post by chili555 on 2013-06-20
>  Just as I was getting ready to do the modprobe, my speed test results tanked That's exactly what the modprobe parts are designed to address and yet you decided to abandon them. Please see:> PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=46 time=437 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=46 time=153 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=46 time=31.5 ms
Notice the times get faster as you go? That suggests to me that the driver was waking up from a long nap due to, perhaps, power saving. Therefor, we instruct the driver to *NOT* use power saving:```
$ modinfo rtl8192ce
filename:       /lib/modules/3.8.0-25-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
<snip>
description:    Realtek 8192C/8188C 802.11n PCI wireless
<snip>
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
[COLOR="#FF0000"]parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)[/COLOR]
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

```Will you please proceed and give me your report?

---

### Post by mbott on 2013-06-20
And here it is

mbott@mdesktop:~$ sudo modprobe -r rtl8192ce
mbott@mdesktop:~$ sudo modprobe rtl8192ce ips=0
mbott@mdesktop:~$ ping -c3 8.8.8.8
```
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=46 time=35.7 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=46 time=398 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=46 time=217 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 35.760/217.284/398.760/148.194 ms
```

I've noticed that from my laptop running 12.04, I can "see" 8 other networks from it when at the same time I can only "see" one additional network from the desktop.

-- 
Mike

---

### Post by chili555 on 2013-06-20
Frankly, the rtl8192xx suite is tricky. I am not sure and possibly skeptical that it will, in my lifetime, do N speeds. I am anxious to be disproven. 

Nevertheless, if you want to try a newer, possibly better, driver, I suggest this: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.8.2/compat-drivers-3.8.2-2-su.tar.bz2](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.8.2/compat-drivers-3.8.2-2-su.tar.bz2) Obtain this package and download it to your desktop. Right-click it and select 'Extract Here.' Now open a terminal and, with an internet connection, do:

```
sudo apt-get install build-essential linux-headers-generic
cd Desktop/compat-drivers-3.8.2-2-su
./scripts/driver-select rtlwifi
make
sudo make install

```
Reboot and see if performance is improved.

---

### Post by mbott on 2013-06-20
> **chili555 said:**
> Frankly, the rtl8192xx suite is tricky. I am not sure and possibly skeptical that it will, in my lifetime, do N speeds. I am anxious to be disproven. 

Nevertheless, if you want to try a newer, possibly better, driver, I suggest this: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.8.2/compat-drivers-3.8.2-2-su.tar.bz2](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.8.2/compat-drivers-3.8.2-2-su.tar.bz2) Obtain this package and download it to your desktop. Right-click it and select 'Extract Here.' Now open a terminal and, with an internet connection, do:

```
sudo apt-get install build-essential linux-headers-generic
cd Desktop/compat-drivers-3.8.2-2-su
./scripts/driver-select rtlwifi
make
sudo make install

```
Reboot and see if performance is improved.

Chili,

Unfortunately, there has been no improvement in either throughput or stability.  Might have to put together a Plan B which I would have preferred not having to do as I would have like to stay in the linux environment that I've enjoyed for the last six years.  I do greatly appreciate your assistance these last couple of days!

Thanks again.

-- 
Mike

---

### Post by chili555 on 2013-06-21
Will you, as an experiment, temporarily turn off N speeds in the router and see what effect it has here? Is the router's encryption set to TKIP or AES? AES is preferred. I'd also try with and without QOS.

---

### Post by securay on 2013-06-21
Thanks chili, someway You help me with my problem but my card is a broadcom

---

### Post by chili555 on 2013-06-21
> **securay said:**
> Thanks chili, someway You help me with my problem but my card is a broadcomPleease start your own new thread and tell us all about it.

---

### Post by mbott on 2013-06-22
> **chili555 said:**
> Will you, as an experiment, temporarily turn off N speeds in the router and see what effect it has here? Is the router's encryption set to TKIP or AES? AES is preferred. I'd also try with and without QOS.

Turning off N speeds and QOS made no difference in the wireless stability.  AES was the encryption method.

I've thrown in the towel on this.  Maybe when I get some extra time, I'll pick it up again.  Thanks again Chili!

-- 
Mike

---

### Post by chili555 on 2013-06-24
> **mbott said:**
> Maybe when I get some extra time, I'll pick it up again.  Post back and we'll proceed.

---

