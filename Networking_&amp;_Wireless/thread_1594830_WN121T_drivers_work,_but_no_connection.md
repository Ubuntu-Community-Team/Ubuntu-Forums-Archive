---
title: "WN121T drivers work, but no connection"
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by KoffieBaard on 2010-10-12
I have a WN121T USB adapter for my wireless, which sporadically worked on 10.04, but after a upgrade to 10.10 I have never been able to get a connection again.
I still see the wireless adapter working, and when trying to connect to a WPA2 secured network (only thing available here, I do see about 5 other WPA2 secured networks I don't have access to) using the right password, he tries to connect, with a link quality of about 60/100, but it doesn't connect fully. 
I ran through all troubleshooters, and the only error i came across was: ndiswrapper (NdisMSetInformationComplete:2524): invalid task

But google doesn't provide a solution for this. Does this have to do with the AP being WPA2 secured or is there something else wrong?

I have also ran some diagnostics for you to see, but switching from ubuntu to windows somehow screwed up all the enters and spaces, and I don't really think they're useful as I have isolated the problem to that one error there.

Works perfectly on Windows 7 though.

---

### Post by KoffieBaard on 2010-10-13
```
WN121T USB 2.0 300 MBps Wireless-n adapter

lsusb

Bus 001 Device 003: ID 0846:7100 NetGear, Inc. WN121T RangeMax Next Wireless-N [Marvell TopDog]

iwconfig

wlan0     IEEE 802.11g  ESSID:"NETGEAR2008"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:22:3F:3A:C1:10   
          Bit Rate=300 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lsmod

Module                  Size  Used by
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  1 vfat
radeon                825934  0 
ttm                    56633  1 radeon
drm_kms_helper         30200  1 radeon
drm                   168054  3 radeon,ttm,drm_kms_helper
i2c_algo_bit            5168  1 radeon
parport_pc             26058  0 
ppdev                   5556  0 
binfmt_misc             6599  1 
snd_hda_codec_atihdmi     2411  1 
joydev                  8735  0 
snd_hda_codec_realtek   217980  1 
snd_hda_intel          22107  4 
snd_hda_codec          87552  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  3 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
usbhid                 36882  0 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
hid                    67742  1 usbhid
snd                    49006  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fglrx                2252513  0 
i7core_edac            15510  0 
edac_core              38630  3 i7core_edac
soundcore                880  1 snd
lp                      7342  0 
agpgart                32011  3 ttm,drm,fglrx
ndiswrapper           184207  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
parport                31492  3 parport_pc,ppdev,lp
usb_storage            40172  1 

dmesg

[   10.587408] ndiswrapper: driver wn121t (Marvell,09/29/2006,1.0.3.7) loaded
[   10.618494] type=1400 audit(1286899622.941:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1143 comm="apparmor_parser"
[   10.618622] type=1400 audit(1286899622.941:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi" pid=1147 comm="apparmor_parser"
[   10.618645] type=1400 audit(1286899622.941:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1146 comm="apparmor_parser"
[   10.618655] type=1400 audit(1286899622.941:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1148 comm="apparmor_parser"
[   10.618903] type=1400 audit(1286899622.941:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1143 comm="apparmor_parser"
[   10.619128] type=1400 audit(1286899622.941:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1143 comm="apparmor_parser"
[   10.619282] type=1400 audit(1286899622.941:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1146 comm="apparmor_parser"
[   11.313366] wlan0: ethernet device 00:1e:2a:39:f6:bd using NDIS driver: wn121t, version: 0x1000206, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:7100.F.conf
[   11.313380] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   11.313413] usbcore: registered new interface driver ndiswrapper
[   11.369572] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   11.492542] ppdev: user-space parallel port driver
[   12.825685] [drm] Initialized drm 1.1.0 20060810
[   12.851106] [drm] radeon defaulting to kernel modesetting.
[   12.851108] [drm] radeon kernel modesetting enabled.
[   13.382544] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   14.971179] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   15.436037] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   25.565962] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   36.134359] wlan0: no IPv6 routers present

sudo lshw -C network

*-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:2a:39:f6:bd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wn121t driverversion=1.56+Marvell,09/29/2006,1.0.3.7 link=no multicast=yes wireless=IEEE 802.11g

iwlist scan

          Cell 03 - Address: 00:22:3F:3A:C1:10
                    ESSID:"NETGEAR2008"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:55/100  Signal level:-73 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


```This is the list of commands I should post the result of according to the wireless ticket sticky, these are all made when there was no cnnection at all, except the iwconfig, which I took during connecting to a WPA2 secured network, but eventually disconnected before I had access to the internet.

---

