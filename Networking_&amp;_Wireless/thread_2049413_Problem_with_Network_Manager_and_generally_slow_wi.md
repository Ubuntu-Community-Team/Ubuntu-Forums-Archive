---
title: "Problem with Network Manager and generally slow wireless using 12.04"
date: 2012-08-28
forum: Networking &amp; Wireless
---

### Post by silver-grey on 2012-08-28
I am running Ubuntu 12.04 on a Toshiba Satellite L755.  I have had several issues with my wireless, including
- wireless does not automatically refresh (for example, if I take my laptop from home to work, Network Manager claims I am still 'connected' to my home wireless network and does not update the list of available networks, or connect me to my work wireless network.  I can manually disconnect from the home network and reconnect to the work network, but this can take several minutes)
- Network Manager is unresponsive
- Signal lost, but Network Manager still indicates a strong connection
- General slow internet

Given the above list, is my problem with Network Manager or some other aspect of my settings?  If the problem is Network Manager, is there a way to troubleshoot it or should I replace it entirely?  I am a Ubuntu newbie, so very basic instructions would be appreciated.

My detailed information is below (apologies for the infodump, but I wasn't sure which parts were relevant)

lspci
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b4)
00:1c.6 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
03:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet (rev c1)

```iwconfig
```
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"RedRover"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:24:6C:D1:2F:01   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:102   Missed beacon:0

eth0      no wireless extensions.
```lsmod
```
Module                  Size  Used by
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
dm_crypt               22528  1 
joydev                 17393  0 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_conexant    52554  1 
arc4                   12473  2 
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
snd_rawmidi            25424  1 snd_seq_midi
psmouse                72919  0 
serio_raw              13027  0 
rtl8192ce              75491  0 
rtl8192c_common        69519  1 rtl8192ce
rtlwifi                95804  1 rtl8192ce
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              436455  3 rtl8192ce,rtl8192c_common,rtlwifi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
cfg80211              178679  2 rtlwifi,mac80211
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
toshiba_acpi           18158  0 
snd                    62064  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sparse_keymap          13658  1 toshiba_acpi
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mei                    36570  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
i915                  414739  3 
drm_kms_helper         45466  1 i915
atl1c                  36718  0 
drm                   197692  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
wmi                    18744  1 toshiba_acpi

```sudo lshw -C network
```
  *-network               
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 9c:b7:0d:dc:00:14
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.2.0-29-generic-pae firmware=N/A ip=10.32.69.142 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:3000(size=256) memory:c0500000-c0503fff
  *-network
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c1
       serial: 04:7d:7b:a5:12:97
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:c0400000-c043ffff ioport:2000(size=128)
```iwlist scan
```
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:24:6C:D1:2F:01
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:off
                    ESSID:"RedRover"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s
                    Mode:Master
                    Extra:tsf=000000169337b508
                    Extra: Last beacon: 32524ms ago
                    IE: Unknown: 0008526564526F766572
                    IE: Unknown: 01078B0C1296182430
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000

eth0      Interface doesn't support scanning.

```uname -mr
```
3.2.0-29-generic-pae i686
```

Thank you very much for any help you can give.

---

### Post by beboylips on 2012-08-30
May I suggest Wicd as a replacement. It's a connection manager like NetworkManager + it's gnome GUI.

Edit: Also found the driver for your card at the Realtek website. May be useful if you want to try use theirs instead of the one implemented in Linux. [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=272&DownTypeID=3&GetDown=false&Downloads=true#2292](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=272&DownTypeID=3&GetDown=false&Downloads=true#2292)

---

