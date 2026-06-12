---
title: "set up a wireless connection"
date: 2009-12-10
forum: Networking &amp; Wireless
---

### Post by donofrij on 2009-12-10
I created a dual boot Windows/Ubuntu. Windows continues its wireless connection. However, I cannot get Ubuntu connected wirelessly with my Broadcom 4318 wireless adapter. I installed Ndiswrapper. I blacklisted the existing "info.linux.driver b43.pci-bridge" driver. I installed the Windows bcmwl5 .inf driver. 

When I open System/Adm/Windows Wireless Driver dialog box, a smaller dialog box opens stating "unable to see if hardware is present". After I click "OK", the Wireless Network Drivers box opens. On the left is the bcmwl5 driver, and following comment: "hardware present? Yes"

In iwconfig wlan0, it states "access point not associated"

I have a Linksys WRT54G router w/WPA2 security. 

Any help will be most appreciated as the only thing holding me up with transitioning completely from Windows to Linux is this wireless connection!

---

### Post by donofrij on 2009-12-14
-laptop:~$ lshw -c network[ 
WARNING: you should run this program as super-user. 
  *-network:0             
       description: Network controller 
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 2 
       bus info: pci@0000:06:02.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: driver=b43-pci-bridge latency=64 
       resources: irq:21 memory:c0204000-c0205fff 
  *-network:1 
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 6 
       bus info: pci@0000:06:06.0 
       logical name: eth0 
       version: 10 
       serial: 00:0f:b0:bc:0a:b7 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=128 maxlatency=64 mingnt=32 multicast=yes 
       resources: irq:22 ioport:a000(size=256) memory:c020a400-c020a4ff 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 2 
       logical name: wlan0 
       serial: 00:14:a5:2d:22:c4 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg 
-laptop:~$ lspci -v | grep Ethernet 
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
joseph@joseph-laptop:~$ sudo lspci -n 
00:00.0 0600: 1002:5950 (rev 01) 
00:01.0 0604: 1002:5a3f 
00:04.0 0604: 1002:5a36 
00:13.0 0c03: 1002:4374 
00:13.1 0c03: 1002:4375 
00:13.2 0c03: 1002:4373 
00:14.0 0c05: 1002:4372 (rev 11) 
00:14.1 0101: 1002:4376 
00:14.3 0601: 1002:4377 
00:14.4 0604: 1002:4371 
00:14.5 0401: 1002:4370 (rev 02) 
00:14.6 0703: 1002:4378 (rev 02) 
00:18.0 0600: 1022:1100 
00:18.1 0600: 1022:1101 
00:18.2 0600: 1022:1102 
00:18.3 0600: 1022:1103 
01:05.0 0300: 1002:5955 
06:02.0 0280: 14e4:4318 (rev 02) 
06:04.0 0607: 104c:8031 
06:04.2 0c00: 104c:8032 
06:04.3 0180: 104c:8033 
06:04.4 0805: 104c:8034 
06:06.0 0200: 10ec:8139 (rev 10) 
joseph@joseph-laptop:~$ lsmod 
Module                  Size  Used by 
isofs                  31620  1 
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat 
udf                    80900  0 
crc_itu_t               1852  1 udf 
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_atiixp             15720  2 
snd_atiixp_modem       11940  0 
snd_ac97_codec        101216  2 snd_atiixp,snd_atiixp_modem 
ac97_bus                1532  1 snd_ac97_codec 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss 
snd_seq_dummy           2656  0 
snd_pcm                75296  4 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss 
snd_seq_oss            28576  0 
arc4                    1660  2 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi 
ecb                     2524  2 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
pcmcia                 36808  0 
snd_timer              22276  2 snd_pcm,snd_seq 
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
joydev                 10272  0 
b43                   122136  0 
yenta_socket           24200  1 
snd                    59204  15 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
mac80211              181236  1 b43 
tifm_7xx1               5372  0 
sdhci_pci               7100  0 
usblp                  12636  0 
rsrc_nonstatic         11644  1 yenta_socket 
soundcore               7264  1 snd 
sdhci                  17472  1 sdhci_pci 
cfg80211               93052  2 b43,mac80211 
tifm_core               7832  1 tifm_7xx1 
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic 
i2c_piix4               9932  0 
snd_page_alloc          9156  3 snd_atiixp,snd_atiixp_modem,snd_pcm 
shpchp                 32272  0 
psmouse                56180  0 
led_class               4096  2 b43,sdhci 
serio_raw               5280  0 
k8temp                  4188  0 
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter 
x_tables               16544  1 ip_tables 
lp                      8964  0 
parport                35340  2 ppdev,lp 
usbhid                 38208  0 
usb_storage            52544  2 
8139too                22620  0 
video                  19380  0 
output                  2780  1 video 
radeon                636000  2 
ttm                    36212  1 radeon 
drm                   159584  4 radeon,ttm 
i2c_algo_bit            5760  1 radeon 
ssb                    35300  1 b43 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394 
8139cp                 19260  0 
mii                     5212  2 8139too,8139cp 
ati_agp                 6760  0 
agpgart                34988  3 ttm,drm,ati_agp 
joseph@joseph-laptop:~$ lsmod | grep b43 
b43                   122136  0 
mac80211              181236  1 b43 
cfg80211               93052  2 b43,mac80211 
led_class               4096  2 b43,sdhci 
ssb                    35300  1 b43 
joseph@joseph-laptop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

-laptop:~$ sudo ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:bc:0a:b7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:8372 (8.3 KB)  TX bytes:8372 (8.3 KB) 

-laptop:~$ sudo iwlist wlan0 
iwlist: unknown command `wlan0' (check 'iwlist --help'). 
-laptop:~$ iwlist --help 
Usage: iwlist [interface] scanning [essid NNN] [last] 
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 
-laptop:~$ iwlist lwan0 scanning 
lwan0     Interface doesn't support scanning.

---

