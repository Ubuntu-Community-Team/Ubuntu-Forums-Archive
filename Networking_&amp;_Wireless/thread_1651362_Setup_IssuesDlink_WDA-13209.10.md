---
title: "Setup Issues/Dlink WDA-1320/9.10"
date: 2010-12-23
forum: Networking &amp; Wireless
---

### Post by kungfudriveby on 2010-12-23
Hello all, thank you for checking my post. I have spent all day  (literally) trying to get a computer set up with ubuntu minimal and  xbmc. I have been having the worst time. I finally got ubuntu and xbmc  installed and running well. I have tried dozens of tutorials and guides  and none seem to get me anywhere on getting this wireless setup. The  system is an old 2.8 P4, 2.5gb ram, geforce 5200 256mb ram. the card is a  pci dlink wda-1320. At first it had Ath5k drivers installed. Spent a  while trying to get that to work with various edits to interfaces.conf  and wpa_supplicant.conf. I ended up putting the madwifi drivers on but  that did not seem to help. Im sure there will be more info needed on  what exactly I did and did not do, but this is what I have so far. I  have honestly spent around 8 hours straight on this. More info (All this  info i pulled from how it currently sits from being booted):

Kernel: 2.6.31-22-generic i686

Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (re    v 01)

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:0c:6e:dd:0f:6b
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:fedd:f6b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:543 errors:0 dropped:0 overruns:0 frame:0
          TX packets:204 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:60742 (60.7 KB)  TX bytes:26764 (26.7 KB)
          Interrupt:17 Base address:0xb800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11b  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```lsmod
```

Module                  Size  Used by
snd_intel8x0           30168  2
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0
wlan_scan_sta          11996  0
snd_seq_oss            28608  0
snd_seq_midi            6464  0
ath_rate_sample        11964  1
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ath_pci                92316  0
snd_timer              22276  3 snd_pcm,snd_seq
wlan                  198736  4 wlan_scan_sta,ath_rate_sample,ath_pci
i915                  227528  0
drm                   160096  1 i915
ppdev                   6688  0
i2c_algo_bit            5760  1 i915
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lp                      8964  0
ath_hal               192272  3 ath_rate_sample,ath_pci
intel_agp              27996  2 i915
parport_pc             31940  1
nvidia               7089800  34
agpgart                34988  3 drm,intel_agp,nvidia
snd                     59236  12  snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
video                  19380  1 i915
iptable_filter          3100  0
parport                35340  3 ppdev,lp,parport_pc
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
shpchp                 32272  0
serio_raw               5280  0
output                  2780  1 video
8139too                22620  0
8139cp                 19260  0
mii                     5212  2 8139too,8139cp
floppy                 54916  0
xbmc@media:~$

```lshw -C network
```
*-network:0 DISABLED
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: wifi0
       version: 01
       serial: 00:15:e9:89:9a:3e
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11b
       resources: irq:21 memory:ce000000-ce00ffff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: d
       bus info: pci@0000:01:0d.0
       logical name: eth0
       version: 10
       serial: 00:0c:6e:dd:0f:6b
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=8139too  driverversion=0.9.28 duplex=full ip=192.168.1.65 latency=64 link=yes  maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:17 ioport:b800(size=256) memory:cc800000-cc8000ff

```Network Restart
```
*  Reconfiguring network  interfaces...                                              There is  already a pid file /var/run/dhclient.eth0.pid with pid 767
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:0c:6e:dd:0f:6b
Sending on   LPF/eth0/00:0c:6e:dd:0f:6b
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:0c:6e:dd:0f:6b
Sending on   LPF/eth0/00:0c:6e:dd:0f:6b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 192.168.1.65 from 192.168.1.254
DHCPREQUEST of 192.168.1.65 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.65 from 192.168.1.254
bound to 192.168.1.65 -- renewal in 40740 seconds.
ioctl[SIOCGIFFLAGS]: No such device
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
wifi0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up wlan0.
```It's almost 2am now and I just pulled out my last strand of hair, please be kind :wink:

---

