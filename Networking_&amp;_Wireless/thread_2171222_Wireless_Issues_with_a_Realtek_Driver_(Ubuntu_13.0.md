---
title: "Wireless Issues with a Realtek Driver (Ubuntu 13.04, Malibal Lotus P150EM)"
date: 2013-08-29
forum: Networking &amp; Wireless
---

### Post by Matt_Tanner on 2013-08-29
Hey all! I'm completely and totally new to ubuntu. I've had a great experience so far, with one exception- my wireless connection. My wireless is slow at its best, and randomly drops the connection at its worst. According the computer, it's still connected, but I have to reconnect to access the internet. From research that I didn't completely understand, I believe it has something to do with my realtek wireless driver. As is, this post was hell to do, having to disconnect and reconnect so often.

I'm headed back to uni next week, and I would love to get this sorted by then. At this point, I'm actually ready to give up, so any and all advice or help is greatly appreciated! 

Alright, that's all I really have to say, so I'm just gonna post everything from the 'howto wireless' post. Sorry if its an overload of information; I genuinely have very little idea what I am doing.

Thanks in advance! Forgive me if I forgot something! Here goes. [B]

1 ) Machine Brand and Model (PC/Laptop)[/B]:

Malibal Lotus P150EM Laptop


**2 ) Wireless Brand, Model and Wireless Chipset:**
```
matt@MAT-P15xEMx:~$ lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF114M [GeForce GTX 675M] (rev a1)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
03:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller (rev 0a)
04:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
05:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller (rev 30)
```

```
matt@MAT-P15xEMx:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 003: ID 147e:1002 Upek 
Bus 002 Device 004: ID 5986:0361 Acer, Inc 
```

**3 ) check interface:**

     
ifconfig:
```
wlan0     Link encap:Ethernet  HWaddr 94:db:c9:0f:b0:9c  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::96db:c9ff:fe0f:b09c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:884 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1048 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:822021 (822.0 KB)  TX bytes:172971 (172.9 KB
```)


iwconfig:
```
wlan0     IEEE 802.11bgn  ESSID:"99GR5"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:7F:28:28:59:5D   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:10   Missed beacon:0
```

**4 ) Check for modules:**
```
matt@MAT-P15xEMx:~$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_realtek    78399  1 
joydev                 17377  0 
bnep                   18036  2 
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  0 
bluetooth             228619  10 bnep,rfcomm
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
ghash_clmulni_intel    13259  0 
aesni_intel            55399  2 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
microcode              22881  0 
uvcvideo               80847  0 
psmouse                95870  0 
serio_raw              13215  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
rtsx_pci_ms            13011  0 
memstick               16554  1 rtsx_pci_ms
arc4                   12615  2 
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
rtl8192ce              53594  0 
nouveau               939088  1 
rtlwifi                79673  1 rtl8192ce
rtl8192c_common        48779  1 rtl8192ce
mac80211              606457  3 rtlwifi,rtl8192c_common,rtl8192ce
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
mxm_wmi                13021  1 nouveau
i915                  600351  3 
wmi                    19070  2 mxm_wmi,nouveau
cfg80211              510937  2 mac80211,rtlwifi
ttm                    83187  1 nouveau
snd                    68876  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
mac_hid                13205  0 
lpc_ich                17061  0 
video                  19390  2 i915,nouveau
drm_kms_helper         49394  2 i915,nouveau
soundcore              12680  1 snd
drm                   286313  7 ttm,i915,drm_kms_helper,nouveau
mei                    41158  0 
i2c_algo_bit           13413  2 i915,nouveau
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
hid_logitech_dj        18604  0 
usbhid                 47074  1 hid_logitech_dj
hid                   101002  2 usbhid,hid_logitech_dj
rtsx_pci_sdmmc         17475  0 
firewire_ohci          40103  0 
rtsx_pci               33355  2 rtsx_pci_ms,rtsx_pci_sdmmc
firewire_core          64508  1 firewire_ohci
r8169                  67446  0 
ahci                   25731  2 
libahci                31364  1 ahci
crc_itu_t              12707  1 firewire_core
```


**5 ) Kernel boot messages**
     ```
matt@MAT-P15xEMx:~$ dmesg | grep wlan0
[    8.161460] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    8.161716] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    9.845875] wlan0: authenticate with 00:7f:28:28:59:5d
[    9.866119] wlan0: send auth to 00:7f:28:28:59:5d (try 1/3)
[    9.868592] wlan0: authenticated
[    9.869452] wlan0: associate with 00:7f:28:28:59:5d (try 1/3)
[    9.872480] wlan0: RX AssocResp from 00:7f:28:28:59:5d (capab=0x431 status=0 aid=9)
[    9.872730] wlan0: associated
[    9.872739] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   19.870690] wlan0: disassociating from 00:7f:28:28:59:5d by local choice (reason=3)
[   19.903080] wlan0: deauthenticating from 00:7f:28:28:59:5d by local choice (reason=3)
[   25.605710] wlan0: authenticate with 00:7f:28:28:59:5d
[   25.625752] wlan0: send auth to 00:7f:28:28:59:5d (try 1/3)
[   25.627279] wlan0: authenticated
[   25.629368] wlan0: associate with 00:7f:28:28:59:5d (try 1/3)
[   25.632561] wlan0: RX AssocResp from 00:7f:28:28:59:5d (capab=0x431 status=0 aid=9)
[   25.632723] wlan0: associated
[   61.004805] wlan0: deauthenticated from 00:7f:28:28:59:5d (Reason: 6)
[   62.293069] wlan0: authenticate with 00:7f:28:28:59:5d
[   62.312929] wlan0: send auth to 00:7f:28:28:59:5d (try 1/3)
[   62.314475] wlan0: authenticated
[   62.316543] wlan0: associate with 00:7f:28:28:59:5d (try 1/3)
[   62.319764] wlan0: RX AssocResp from 00:7f:28:28:59:5d (capab=0x431 status=0 aid=9)
[   62.319922] wlan0: associated

```

 
**6 ) Network configuration**
```
matt@MAT-P15xEMx:~$ sudo lshw -C network
[sudo] password for matt: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168 PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:03:00.2
       logical name: eth0
       version: 0a
       serial: 00:90:f5:d1:b1:28
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-1_0.0.3 06/18/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:d000(size=256) memory:ec104000-ec104fff memory:ec100000-ec103fff
  *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 94:db:c9:0f:b0:9c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.8.0-19-generic firmware=N/A ip=192.168.1.11 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 ioport:c000(size=256) memory:f6900000-f6903fff
```[B]

7 ) Scan for networks:[/B]

```
wlan0     Scan completed :
          Cell 01 - Address: 00:7F:28:28:59:5D
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"99GR5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000054c80058
                    Extra: Last beacon: 560448ms ago
                    IE: Unknown: 00053939475235
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101060003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A8C131BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706555320010B1B
```



**8 ) Ubuntu Version: **

Ubuntu 13.04


**9 ) Kernel/architecture (including 32 vs. 64 bit): **
```
matt@MAT-P15xEMx:~$ uname -mr
3.8.0-19-generic x86_6


```

---

### Post by chili555 on 2013-08-29
I suggest you turn off N speeds in the router. Also, right-click the Network Manager icon and edit wireless, IPv6 to ignore IPv6 settings, like this: [https://access.redhat.com/site/documentation/resources/docs/en-US/Red_Hat_Enterprise_Linux/6/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](https://access.redhat.com/site/documentation/resources/docs/en-US/Red_Hat_Enterprise_Linux/6/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png) Save and close.

Post back and let us know if there is any improvement.

---

### Post by Matt_Tanner on 2013-08-29
Thanks for the reply! Sadly, disabling Ipv6 had little to no effect.

---

### Post by chili555 on 2013-08-29
> **Matt_Tanner said:**
> Thanks for the reply! Sadly, disabling Ipv6 had little to no effect.And N speeds in the router??

---

### Post by Matt_Tanner on 2013-08-29
Been googling that for a while now- I'm not really sure what that is. However, I can say that I had no issues whatsoever on this same laptop when I had windows installed, so I'm not sure playing with the router will help.

---

### Post by chili555 on 2013-08-29
> **Matt_Tanner said:**
> Been googling that for a while now- I'm not really sure what that is. However, I can say that I had no issues whatsoever on this same laptop when I had windows installed, so I'm not sure playing with the router will help.Windows is not Linux. Windows drivers are not Linux drivers, except in the case of the tricky, twitchy ndiswrapper which, thankfully, you are not using. A great many things work perfectly well in Linux but not Windows and vice-versa.

Routers which have the capability of B, G and N generally have the capability to change to B and G only. Please see: [http://sim.dlink.ca/images/faqs/How_do_I_change_the_80211_Mode_on_my_DIR_series_router/step3.jpg](http://sim.dlink.ca/images/faqs/How_do_I_change_the_80211_Mode_on_my_DIR_series_router/step3.jpg) That is what I'm asking you to try.

---

