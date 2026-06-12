---
title: "wireless sometimes does not work. 12.04_Asus U33Jc_Intel N1000"
date: 2012-09-03
forum: Networking &amp; Wireless
---

### Post by sssuizaaa on 2012-09-03
Hello Everyone,

My wireless connection only works from time to time. All of a sudden stops working and it works again in an unpredictible (at least to me) period of time. It seems to connect to the network at all times but internet connection comes and disapears.

Any help with this would be greatly apreciated.

Thanks in advance

sssuizaaa

Here's some information:

```
                                   javier@javier-U33Jc:~$ cat /etc/lsb-release; uname -a 
 DISTRIB_ID=Ubuntu 
 DISTRIB_RELEASE=12.04 
 DISTRIB_CODENAME=precise 
 DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS" 
 Linux javier-U33Jc 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux 
 javier@javier-U33Jc:~$ lspci -nnk | grep -iA2 net 
 03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0083] 
     Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1305] 
     Kernel driver in use: iwlwifi 
 -- 
 05:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8131 Gigabit Ethernet [1969:1063] (rev c0) 
     Subsystem: ASUSTeK Computer Inc. Device [1043:1820] 
     Kernel driver in use: atl1c 
 javier@javier-U33Jc:~$ lsusb 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub 
 Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub 
 Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub 
 Bus 001 Device 003: ID 13d3:5122 IMC Networks  
 Bus 002 Device 003: ID 05bc:0102 3G Green Green Globe Co., Ltd  
 javier@javier-U33Jc:~$ iwconfig 
 lo        no wireless extensions. 
  
 wlan0     IEEE 802.11bgn  ESSID:"vodafoneF4CA"   
           Mode:Managed  Frequency:2.447 GHz  Access Point: 72:E8:7B:AE:F4:C8    
           Bit Rate=65 Mb/s   Tx-Power=14 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off 
           Power Management:off 
           Link Quality=55/70  Signal level=-55 dBm   
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
           Tx excessive retries:0  Invalid misc:179   Missed beacon:0 
  
 eth0      no wireless extensions. 
  
 javier@javier-U33Jc:~$ rfkill list all 
 0: phy0: Wireless LAN 
     Soft blocked: no 
     Hard blocked: no 
 javier@javier-U33Jc:~$ lsmod 
 Module                  Size  Used by 
 acpi_call              12623  0  
 rfcomm                 47604  0  
 bnep                   18281  2  
 bluetooth             180104  10 rfcomm,bnep 
 parport_pc             32866  0  
 ppdev                  17113  0  
 binfmt_misc            17540  1  
 joydev                 17693  0  
 snd_hda_codec_hdmi     32474  1  
 snd_hda_codec_realtek   224066  1  
 arc4                   12529  2  
 mxm_wmi                12979  0  
 snd_hda_intel          33773  5  
 snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel 
 snd_hwdep              13668  1 snd_hda_codec 
 snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
 snd_seq_midi           13324  0  
 snd_rawmidi            30748  1 snd_seq_midi 
 snd_seq_midi_event     14899  1 snd_seq_midi 
 snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event 
 snd_timer              29990  2 snd_pcm,snd_seq 
 snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq 
 snd                    78855  19 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 psmouse                87692  0  
 wmi                    19256  1 mxm_wmi 
 asus_laptop            24493  0  
 sparse_keymap          13890  1 asus_laptop 
 input_polldev          13896  1 asus_laptop 
 serio_raw              13211  0  
 mac_hid                13253  0  
 uvcvideo               72627  0  
 videodev               98259  1 uvcvideo 
 v4l2_compat_ioctl32    17128  1 videodev 
 iwlwifi               332525  0  
 i915                  472941  3  
 mac80211              506816  1 iwlwifi 
 drm_kms_helper         46978  1 i915 
 drm                   242038  4 i915,drm_kms_helper 
 cfg80211              205544  2 iwlwifi,mac80211 
 soundcore              15091  1 snd 
 snd_page_alloc         18529  2 snd_hda_intel,snd_pcm 
 i2c_algo_bit           13423  1 i915 
 video                  19596  1 i915 
 mei                    41616  0  
 lp                     17799  0  
 parport                46562  3 parport_pc,ppdev,lp 
 usbhid                 47199  0  
 hid                    99559  1 usbhid 
 atl1c                  41718  0  
 javier@javier-U33Jc:~$  
 

 

 

 

 root@javier-U33Jc:/home/javier# lsusb  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub  
 Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub  
 Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub  
 Bus 001 Device 003: ID 13d3:5122 IMC Networks  
 Bus 002 Device 003: ID 05bc:0102 3G Green Green Globe Co., Ltd  
 root@javier-U33Jc:/home/javier# lspci  
 00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)  
 00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev ff)  
 00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)  
 00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)  
 00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)  
 00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)  
 00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)  
 00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)  
 00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)  
 00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)  
 00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)  
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)  
 00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)  
 00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)  
 01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 310M] (rev ff)  
 03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000  
 04:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)  
 05:00.0 Ethernet controller: Atheros Communications Inc. AR8131 Gigabit Ethernet (rev c0)  
 ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)  
 ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05) 
 ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)  
 ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)  
 ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)  
 ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)  
 root@javier-U33Jc:/home/javier# ifconfig  
 eth0      Link encap:Ethernet  HWaddr 20:cf:30:45:65:69   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:1182 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:1170 errors:0 dropped:0 overruns:0 carrier:2  
           collisions:0 txqueuelen:1000  
           RX bytes:837186 (837.1 KB)  TX bytes:215214 (215.2 KB)  
           Interrupt:55  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:696 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:696 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:59902 (59.9 KB)  TX bytes:59902 (59.9 KB)  
 

 wlan0     Link encap:Ethernet  HWaddr 00:1e:64:4d:8f:a4   
           inet addr:192.168.0.222  Bcast:192.168.0.255  Mask:255.255.255.0  
           inet6 addr: fe80::21e:64ff:fe4d:8fa4/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:316 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:544 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:19242 (19.2 KB)  TX bytes:72983 (72.9 KB)  
 

 root@javier-U33Jc:/home/javier# iwconfig  
 lo        no wireless extensions.  
 

 wlan0     IEEE 802.11bgn  ESSID:"vodafoneF4CA"   
           Mode:Managed  Frequency:2.427 GHz  Access Point: 72:E8:7B:AE:F4:C8    
           Bit Rate=65 Mb/s   Tx-Power=14 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Encryption key:off  
           Power Management:off  
           Link Quality=70/70  Signal level=-38 dBm   
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:51   Missed beacon:0  
 

 eth0      no wireless extensions.  
 

 root@javier-U33Jc:/home/javier#  
  
```

---

### Post by sssuizaaa on 2012-09-03
Sorry, I forgot to include this:

I hope this is the information that is required. 

thanks 

sssuizaaa

```
javier@javier-U33Jc:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
javier@javier-U33Jc:~$ lsmod
Module                  Size  Used by
acpi_call              12623  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224066  1 
arc4                   12529  2 
mxm_wmi                12979  0 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  19 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                87692  0 
wmi                    19256  1 mxm_wmi
asus_laptop            24493  0 
sparse_keymap          13890  1 asus_laptop
input_polldev          13896  1 asus_laptop
serio_raw              13211  0 
mac_hid                13253  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
iwlwifi               332525  0 
i915                  472941  3 
mac80211              506816  1 iwlwifi
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
cfg80211              205544  2 iwlwifi,mac80211
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
mei                    41616  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
atl1c                  41718  0 
javier@javier-U33Jc:~$ 

```

---

### Post by sssuizaaa on 2012-09-14
Hey guys, I still have this problem.    	 	 	 	 	 	   I've found a post explaining how to post a wireless issue. So find below the required information.
 

 Additional information. The computer that cannot connect to the internet has another OS (windows) and I can connect always with no problem from windows. I have another computer that only has ubuntu. No problem connecting to internet from that computer either. So, apparently it is a problem of the ubuntu of this computer.


I hope somebody can help me.


sssuizaaa


```
javier@javier-U33Jc:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev ff)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 310M] (rev ff)
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
04:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
05:00.0 Ethernet controller: Atheros Communications Inc. AR8131 Gigabit Ethernet (rev c0)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
javier@javier-U33Jc:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 13d3:5122 IMC Networks 
Bus 002 Device 003: ID 05bc:0102 3G Green Green Globe Co., Ltd 
javier@javier-U33Jc:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 20:cf:30:45:65:69  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:55 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1857 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1857 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:120883 (120.8 KB)  TX bytes:120883 (120.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:64:4d:8f:a4  
          inet addr:192.168.0.222  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:64ff:fe4d:8fa4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:515 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2088 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:63697 (63.6 KB)  TX bytes:214919 (214.9 KB)

javier@javier-U33Jc:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"vodafoneF4CA"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 72:E8:7B:AE:F4:C8   
          Bit Rate=65 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=67/70  Signal level=-43 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0

eth0      no wireless extensions.

javier@javier-U33Jc:~$ lsmod
Module                  Size  Used by
usbhid                 47199  0 
hid                    99559  1 usbhid
acpi_call              12623  0 
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
binfmt_misc            17540  1 
joydev                 17693  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224173  1 
arc4                   12529  2 
mxm_wmi                12979  0 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
asus_laptop            24493  0 
sparse_keymap          13890  1 asus_laptop
input_polldev          13896  1 asus_laptop
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    19256  1 mxm_wmi
mac_hid                13253  0 
iwlwifi               332525  0 
psmouse                87692  0 
mac80211              506816  1 iwlwifi
serio_raw              13211  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
cfg80211              205544  2 iwlwifi,mac80211
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  473035  3 
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
mei                    41616  0 
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
atl1c                  41718  0 
javier@javier-U33Jc:~$ dmesg | grep "wlan0"
[   21.598928] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.599922] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.876042] wlan0: authenticate with 72:e8:7b:ae:f4:c8 (try 1)
[   23.878685] wlan0: authenticated
[   23.878989] wlan0: associate with 72:e8:7b:ae:f4:c8 (try 1)
[   23.882895] wlan0: RX AssocResp from 72:e8:7b:ae:f4:c8 (capab=0x411 status=0 aid=3)
[   23.882900] wlan0: associated
[   23.888005] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   35.867048] wlan0: no IPv6 routers present
javier@javier-U33Jc:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:1e:64:4d:8f:a4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-30-generic firmware=39.31.5.1 build 35138 ip=192.168.0.222 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:52 memory:d6000000-d6001fff
  *-network
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: c0
       serial: 20:cf:30:45:65:69
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:55 memory:d3800000-d383ffff ioport:9000(size=128)
javier@javier-U33Jc:~$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 72:E8:7B:AE:F4:C8
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"vodafoneF4CA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000af67213b
                    Extra: Last beacon: 105292ms ago
                    IE: Unknown: 000C766F6461666F6E6546344341
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A8C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020000127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706455320010D10
                    IE: Unknown: DD1E00904C338C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401000700000000000000000000000000000000000000

eth0      Interface doesn't support scanning.

javier@javier-U33Jc:~$ lsb_release -d
Description:    Ubuntu 12.04.1 LTS
javier@javier-U33Jc:~$ uname -mr
3.2.0-30-generic x86_64
javier@javier-U33Jc:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 
javier@javier-U33Jc:~$ 

```

---

### Post by sssuizaaa on 2012-09-14
Additional information.

I connect the computer directly to the router with a cable and then I have internet connection. Restart the computer, login and then I remove the cable. Then wireless works. It works for a while of course, hours, a couple of days.....

Does this ring any bell???

sssuizaaa

---

### Post by chili555 on 2012-09-14
Please try temporarily:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```If it helps, we'll write a quick file to make it persistent.

---

### Post by sssuizaaa on 2012-09-16
clili555

First of all, thank you for your response. I was starting to think  I was alone in the middle of the desert. Second, I'm sorry for the late response, I could not access my laptop for the last two days

Third and probably more important. It does work!!. Thank you very much. So, what's next? and if it is not too much hassle. Could you tell me what the problem was??

Regards and thank you again.

sssuizaaa

---

### Post by chili555 on 2012-09-16
The problem is that there is a flaw somewhere in the driver or wpa_supplicant or their interaction that make N speeds difficult or impossible. We disabled it. Let's make the change persistent:```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```Add a single line:```
options iwlwifi 11n_disable=1
```Proofread carefully, save and close gedit.

You should be all set! Please use thread tools at the top to mark Solved.

---

### Post by sssuizaaa on 2012-09-16
chili 555

Thank you very much again. This was driving me crazy!

Cheers

sssuizaaa

---

### Post by foname on 2013-02-26
Thank you so much.. you save my days... I have been looking for this solution for many days.. :)

---

