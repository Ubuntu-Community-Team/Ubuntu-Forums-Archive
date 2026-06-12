---
title: "Wifi Speed drops after few seconds  Ralink corp. RT3090"
date: 2013-05-13
forum: Networking &amp; Wireless
---

### Post by John Merlyn on 2013-05-13
Hi,

My wifi speed drops from ~600 kbps to >50 kbps within a few seconds after connecting to the wifi. There is no problem with speeds on my windows 7 environment nor my phone. I have tried other distros like fedora and Gnome Ubuntu but the problem remains. Due to these low speeds i cannot update or even check what the problem is any help will be appreciated. Below are the concerning details.
[B]

Machine Brand and Model (PC/Laptop):

Lenovo Idea pad z540

[/B][B]Wireless Brand, Model and Wireless Chipset:

[/B]lspci -nn | grep 'Wireless'
03:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]

[B]check interface:

[/B]iiwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"FRITZ!Box 6360 Cable"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 2A:65:11:90:7A:6C   
          Bit Rate=58.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:48  Invalid misc:3930   Missed beacon:0

[B]Check for modules:

[/B]smod
Module                  Size  Used by
joydev                 17693  0 
acer_wmi               28418  0 
psmouse                97485  0 
snd_hda_codec_realtek   224173  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_intel          33719  5 
rts5139               351188  0 
snd_hda_codec         127706  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
k10temp                13166  0 
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uvcvideo               72627  0 
serio_raw              13211  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_seq_midi           13324  0 
i2c_piix4              13301  0 
snd_rawmidi            30748  1 snd_seq_midi
ideapad_laptop         18234  0 
sparse_keymap          13890  2 acer_wmi,ideapad_laptop
parport_pc             32866  0 
rfcomm                 47604  0 
ppdev                  17113  0 
snd_seq_midi_event     14899  1 snd_seq_midi
bnep                   18281  2 
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
bluetooth             180153  10 rfcomm,bnep
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
arc4                   12529  2 
snd                    79041  20 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rt2800pci              18715  0 
rt2800lib              58967  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
rt2x00pci              14620  1 rt2800pci
rt2x00lib              55326  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              506862  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              205774  2 rt2x00lib,mac80211
eeprom_93cx6           12767  1 rt2800pci
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47238  0 
hid                    99636  1 usbhid
wmi                    19256  1 acer_wmi
radeon                808689  3 
video                  19651  0 
r8169                  62154  0 
ttm                    76949  1 radeon
drm_kms_helper         46978  1 radeon
drm                   241971  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13423  1 radeon


[B]Kernel boot messages
[/B]
dmesg | grep wlan
[   17.296922] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.298176] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   45.520119] wlan0: authenticate with 2a:65:11:90:7a:6c (try 1)
[   45.521947] wlan0: authenticated
[   45.536084] wlan0: associate with 2a:65:11:90:7a:6c (try 1)
[   45.539967] wlan0: RX AssocResp from 2a:65:11:90:7a:6c (capab=0x431 status=0 aid=2)
[   45.539974] wlan0: associated
[   45.539980] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[   45.548850] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   56.480066] wlan0: no IPv6 routers present

[B]Network configuration


[/B]
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 05
       serial: f0:de:f1:bd:bc:4e
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:1000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 64:27:37:54:c6:71
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.2.0-41-generic firmware=0.34 ip=192.168.178.59 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f0100000-f010ffff

[B]Scan for networks:
[/B]iwlist scan
lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: 2A:65:11:90:7A:6C
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 6360 Cable"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000019b3cb843
                    Extra: Last beacon: 40692ms ago
                    IE: Unknown: 0014465249545A21426F782036333630204361626C65
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEF111BFFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 331AEF111BFFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: 34160B001700000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F20201010E0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F

**Ubuntu Version** 
lsb_release -d
Description:    Ubuntu 12.04.2 LTS

[B]Kernel/architecture (including 32 vs. 64 bit):

[/B]3.2.0-41-generic x86_64
 

[B]Restarting the network:
[/B]
sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...

---

