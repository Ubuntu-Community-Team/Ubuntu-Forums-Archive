---
title: "sony vaio wireless connection"
date: 2011-03-14
forum: Networking &amp; Wireless
---

### Post by yoq_bise on 2011-03-14
Hello,

My wireless connects and then in a few seconds disconnects and then again connects..... and so on. 
And even it seems to be connected I cannot reach any website. Could you please help me?

Below there are some information probably needed 

** 1 ) Machine Brand and Model (PC/Laptop):**[INDENT]     Sony vaio VPCM13M1E (Netbook)
[/INDENT]** 2 ) Wireless Brand, Model and Wireless Chipset: (I believe it should be one of these)**[INDENT]     01:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
    02:00.5 Ethernet controller: JMicron Technology Corp. JMC260 PCI Express Fast Ethernet Controller (rev 02)
[/INDENT]** 3 ) check interface:**
** a) ifconfig wlan0**
    [INDENT] wlan0     Link encap:Ethernet  HWaddr 90:fb:a6:fe:ce:3d  
          inet addr:128.141.147.107  Bcast:128.141.255.255  Mask:255.255.0.0
          inet6 addr: fe80::92fb:a6ff:fefe:ce3d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3813 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:441760 (441.7 KB)  TX bytes:24804 (24.8 KB)
[/INDENT]** b) iwconfig wlan0**
[INDENT] wlan0     IEEE 802.11bgn  ESSID:"CERN"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:20:A6:72:83:F3   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=70/70  Signal level=28 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/INDENT]** 4 ) Check for modules: (lsmod) I don't know which one is related**
[INDENT] Module                  Size  Used by
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_realtek   218492  1 
rt2860sta             504366  0 
rfcomm                 33811  4 
arc4                    1165  2 
snd_hda_intel          22235  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
rt2800pci               8565  0 
i915                  295435  5 
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
rt2800lib              28961  1 rt2800pci
rt2x00usb               9779  1 rt2800lib
snd_seq_midi            4588  0 
sco                     7998  2 
rt2x00pci               6029  1 rt2800pci
crc_ccitt               1351  2 rt2860sta,rt2800pci
drm_kms_helper         30200  1 i915
rt2x00lib              27307  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
snd_rawmidi            17783  1 snd_seq_midi
bnep                    9542  2 
mac80211              231959  3 rt2x00usb,rt2x00pci,rt2x00lib
snd_seq_midi_event      6047  1 snd_seq_midi
l2cap                  37008  16 rfcomm,bnep
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
drm                   168060  5 i915,drm_kms_helper
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
btusb                  10969  2 
uvcvideo               55847  0 
intel_agp              26566  2 i915
sony_laptop            29088  0 
bluetooth              50500  9 rfcomm,sco,bnep,l2cap,btusb
cfg80211              144694  2 rt2x00lib,mac80211
snd                    49038  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
jmb38x_ms               7387  0 
joydev                  8767  0 
videodev               43098  1 uvcvideo
psmouse                59033  0 
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
v4l1_compat            13359  2 uvcvideo,videodev
serio_raw               4022  0 
memstick                8249  1 jmb38x_ms
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
eeprom_93cx6            1345  1 rt2800pci
output                  1883  1 video
agpgart                32011  2 drm,intel_agp
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
sdhci_pci               6339  0 
sdhci                  15890  1 sdhci_pci
jme                    29882  0 
led_class               2633  2 rt2x00lib,sdhci
mii                     4425  1 jme
[/INDENT]** 5 ) Kernel boot messages (dmesg | grep "wlan0")**
[INDENT] [   28.482474] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.088344] wlan0: direct probe to 00:0f:61:57:c2:72 (try 1)
[   31.288045] wlan0: direct probe to 00:0f:61:57:c2:72 (try 2)
[   31.484549] wlan0: direct probe to 00:0f:61:57:c2:72 (try 3)
[   31.684581] wlan0: direct probe to 00:0f:61:57:c2:72 timed out
[   42.328313] wlan0: authenticate with 00:20:a6:72:83:f3 (try 1)
[   42.331544] wlan0: authenticated
[   42.331640] wlan0: associate with 00:20:a6:72:83:f3 (try 1)
[   42.336203] wlan0: RX AssocResp from 00:20:a6:72:83:f3 (capab=0x421 status=0 aid=13)
[   42.336213] wlan0: associated
[   42.337506] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   50.288684] wlan0: deauthenticating from 00:20:a6:72:83:f3 by local choice (reason=3)
[   50.313941] wlan0: direct probe to 00:0f:61:57:c2:72 (try 1)
[   50.512109] wlan0: direct probe to 00:0f:61:57:c2:72 (try 2)
[   50.712644] wlan0: direct probe to 00:0f:61:57:c2:72 (try 3)
[   50.912576] wlan0: direct probe to 00:0f:61:57:c2:72 timed out
[   52.432047] wlan0: no IPv6 routers present
[   61.556226] wlan0: authenticate with 00:20:a6:72:83:f3 (try 1)
[   61.558614] wlan0: authenticated
[   61.558708] wlan0: associate with 00:20:a6:72:83:f3 (try 1)
[   61.561086] wlan0: deauthenticated from 00:20:a6:72:83:f3 (Reason: 6)
[   66.908232] wlan0: authenticate with 00:20:a6:72:83:f3 (try 1)
[   66.909695] wlan0: authenticated
[   66.909794] wlan0: associate with 00:20:a6:72:83:f3 (try 1)
[   66.911688] wlan0: RX AssocResp from 00:20:a6:72:83:f3 (capab=0x421 status=0 aid=13)
[   66.911697] wlan0: associated
[  370.292158] wlan0: deauthenticating from 00:20:a6:72:83:f3 by local choice (reason=3)
[  370.313242] wlan0: direct probe to 00:0f:61:59:5a:a2 (try 1)
[  370.512145] wlan0: direct probe to 00:0f:61:59:5a:a2 (try 2)
[  370.712149] wlan0: direct probe to 00:0f:61:59:5a:a2 (try 3)
[  370.912141] wlan0: direct probe to 00:0f:61:59:5a:a2 timed out
[  381.560612] wlan0: direct probe to 00:20:a6:75:69:cf (try 1)
[  381.760103] wlan0: direct probe to 00:20:a6:75:69:cf (try 2)
[  381.960103] wlan0: direct probe to 00:20:a6:75:69:cf (try 3)
[  382.160104] wlan0: direct probe to 00:20:a6:75:69:cf timed out
[  386.917080] wlan0: direct probe to 00:0f:61:59:5a:a2 (try 1)
[  387.116189] wlan0: direct probe to 00:0f:61:59:5a:a2 (try 2)
[  387.316249] wlan0: direct probe to 00:0f:61:59:5a:a2 (try 3)
[  387.516254] wlan0: direct probe to 00:0f:61:59:5a:a2 timed out
[  398.160427] wlan0: authenticate with 00:20:a6:72:83:f3 (try 1)
[  398.199710] wlan0: authenticated
[  398.199794] wlan0: associate with 00:20:a6:72:83:f3 (try 1)
[  398.201670] wlan0: RX AssocResp from 00:20:a6:72:83:f3 (capab=0x421 status=0 aid=7)
[  398.201682] wlan0: associated
[ 2185.148209] wlan0: deauthenticating from 00:20:a6:72:83:f3 by local choice (reason=3)
[ 2186.449538] wlan0: authenticate with 00:20:a6:72:83:f3 (try 1)
[ 2186.452462] wlan0: authenticated
[ 2186.452673] wlan0: associate with 00:20:a6:72:83:f3 (try 1)
[ 2186.454458] wlan0: RX AssocResp from 00:20:a6:72:83:f3 (capab=0x421 status=0 aid=3)
[ 2186.454474] wlan0: associated
[/INDENT]** 6 ) Network configuration (sudo lshw -C network)**
[INDENT]   *-network               
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       serial: 90:fb:a6:fe:ce:3d
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.35-27-generic firmware=N/A ip=128.141.147.107 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:fe900000-fe90ffff
  *-network
       description: Ethernet interface
       product: JMC260 PCI Express Fast Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:02:00.5
       logical name: eth0
       version: 02
       serial: 54:42:49:ec:9d:0a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.6 duplex=full ip=128.141.137.55 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:42 memory:fe800000-fe803fff ioport:e100(size=128 ) ioport:e000(size=256)
[/INDENT]** 7 ) Scan for networks: (iwlist scan)**
[INDENT] lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:20:A6:72:83:F3
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=28 dBm  
                    Encryption key: off
                    ESSID:"CERN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000033ab2e17721
                    Extra: Last beacon: 13828ms ago
                    IE: Unknown: 00044345524E
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
[/INDENT]** 8 ) Ubuntu Version: lsb_release -d**
[INDENT] Description:    Ubuntu 10.10
[/INDENT]** 9 ) Kernel/architecture (including 32 vs. 64 bit): **
[INDENT] 2.6.35-27-generic i686
[/INDENT]** 10 ) Restarting the network:**
[INDENT]  * Reconfiguring network interfaces...                                                                                Ignoring unknown interface wlan0=wlan0.
Ignoring unknown interface eth0=eth0.
                                                                                                               [ OK ][/INDENT]

---

### Post by yoq_bise on 2011-03-15
Anybody there????

---

