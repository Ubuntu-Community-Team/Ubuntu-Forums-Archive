---
title: "Using dual wlancards in ubuntu (broadcom/Atheros)"
date: 2010-01-28
forum: Networking &amp; Wireless
---

### Post by axelswe on 2010-01-28
Hi everybody! Made the switch to linux around new years eve and haven't looked back since =).
After installing linux, and the the proprietory driver, wlan (broadcomcard) worked with no further configuration except for inputing my wep-key.
Now im trying to install a second wlan-card(Atheros AR5007G-card), and it seems to atleast be recognized by my computer, but i can't switch to using that interface to connect to wireless. Or interact with it.

Down below you can read many output of all th different commands listed. But I think these *edited* outputs are the most significant ones:

**axel@axel-desktop ~ $ lspci**
```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
**03:07.0 Ethernet controller: Atheros Communications Inc. AR5007G Wireless Network Adapter (rev 01)**
```**axel@axel-****desktop ~ $ lsmod**
```
Module                  Size  Used by
b43                   181340  0 
ath5k                 134632  0 
mac80211              243496  2 b43,ath5k
ath                    10784  1 ath5k
iptable_filter          3872  0 
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
r8169                  38884  0 
mii                     6368  1 r8169
```**axel@axel-desktop ~ $ dmesg | grep ath**
```
[   17.456408] ath5k 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   17.456479] ath5k 0000:03:07.0: registered as 'phy0'
[   17.459633] ath5k phy0: POST Failed !!!
[   17.459648] ath5k 0000:03:07.0: PCI INT A disabled
[   17.459698] ath5k: probe of 0000:03:07.0 failed with error -11
```**axel@axel-desktop ~ $ sudo lshw -C network**
```

 *-network:1 **UNCLAIMED**
       description: Ethernet controller
       product: AR5007G Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 7
       bus info: pci@0000:03:07.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=168 maxlatency=28 mingnt=10
       resources: memory:fafe0000-fafeffff

```**F**rom what i can tell, the ath5k driver/module has been loaded, and the "unclaimed" output should mean that nothing is trying to use that interface.
Is it possible to use the two cards at once? or at least switch in between the two?

Thanks in advance
/Axel


----------------------------------------------------------------------------------------
**COMPLETE output**
```

Machine: Custom built: Asus motherboard, amd 64 processor, 4 gig ram
Linux Mint 8 Helena(karmic based) - x64 Edition.

axel@axel-desktop ~ $ lspci
[CODE]02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
03:07.0 Ethernet controller: Atheros Communications Inc. AR5007G Wireless Network Adapter (rev 01)
```axel@axel-desktop ~ $ ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:24:8c:d4:2f:41  
          inet addr:85.225.211.251  Bcast:85.225.211.255  Mask:255.255.252.0
          inet6 addr: fe80::224:8cff:fed4:2f41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25259820 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29105278 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14534455667 (14.5 GB)  TX bytes:27855603810 (27.8 GB)
          Interrupt:27 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18023 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18023 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1205432 (1.2 MB)  TX bytes:1205432 (1.2 MB)

wlan0     Link encap:Ethernet  HWaddr 00:24:8c:b3:68:c2  
          inet addr:85.225.208.95  Bcast:85.225.211.255  Mask:255.255.252.0
          inet6 addr: fe80::224:8cff:feb3:68c2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30235 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5452 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2753177 (2.7 MB)  TX bytes:1957968 (1.9 MB)
```axel@axel-desktop ~ $ iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"B2_private_E7"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:01:38:AE:A3:AA   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```axel@axel-desktop ~ $ lsmod
```
Module                  Size  Used by
isofs                  36424  0 
udf                    88136  0 
crc_itu_t               2336  1 udf
dm_crypt               14888  0 
binfmt_misc            10220  1 
arc4                    2144  2 
ecb                     3296  2 
snd_hda_codec_atihdmi     4320  1 
snd_hda_codec_realtek   277860  1 
b43                   181340  0 
ath5k                 134632  0 
mac80211              243496  2 b43,ath5k
ath                    10784  1 ath5k
iptable_filter          3872  0 
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
snd_hda_intel          31880  5 
snd_hda_codec          87584  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
ppdev                   8232  0 
snd_seq_oss            33440  0 
joydev                 13088  0 
parport_pc             37352  1 
cfg80211              152616  4 b43,ath5k,mac80211,ath
led_class               5256  2 b43,ath5k
asus_atk0110            9472  0 
amd64_edac_mod         26688  0 
edac_core              48876  1 amd64_edac_mod
psmouse                57124  0 
serio_raw               6596  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
lp                     11908  0 
parport                40528  3 ppdev,parport_pc,lp
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  21 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
fglrx                2279192  65 
i2c_piix4              11728  0 
dm_raid45              78504  0 
xor                     5456  1 dm_raid45
hid_microsoft           4292  0 
usbhid                 43968  0 
usb_storage            66016  0 
ssb                    52080  1 b43
pcmcia                 40116  2 b43,ssb
pcmcia_core            42692  3 b43,ssb,pcmcia
r8169                  38884  0 
mii                     6368  1 r8169
```axel@axel-desktop ~ $ dmesg | grep ath
```
[   17.456408] ath5k 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   17.456479] ath5k 0000:03:07.0: registered as 'phy0'
[   17.459633] ath5k phy0: POST Failed !!!
[   17.459648] ath5k 0000:03:07.0: PCI INT A disabled
[   17.459698] ath5k: probe of 0000:03:07.0 failed with error -11
```axel@axel-desktop ~ $ dmesg | grep wlan
```
[   18.664857] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.930190] wlan0: deauthenticating from 00:01:38:ae:a3:aa by local choice 
```(reason=3)
```
[   28.931487] wlan0: direct probe to AP 00:01:38:ae:a3:aa (try 1)
[   28.933810] wlan0: direct probe responded
[   28.933815] wlan0: authenticate with AP 00:01:38:ae:a3:aa (try 1)
[   28.935232] wlan0: authenticated
[   28.935248] wlan0: associate with AP 00:01:38:ae:a3:aa (try 1)
[   28.937371] wlan0: RX AssocResp from 00:01:38:ae:a3:aa (capab=0x471 status=0 aid=1)
[   28.937374] wlan0: associated
[   28.938282] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   39.820028] wlan0: no IPv6 routers present
[98166.171375] wlan0: deauthenticating from 00:01:38:ae:a3:aa by local choice (reason=3)
[98166.171498] wlan0: deauthenticating from 00:01:38:ae:a3:aa by local choice (reason=3)
[98166.362348] wlan0: deauthenticating from 00:01:38:ae:a3:aa by local choice (reason=3)
[98166.550190] wlan0: direct probe to AP 00:01:38:ae:a3:aa (try 1)
[98166.552103] wlan0: direct probe responded
[98166.552114] wlan0: authenticate with AP 00:01:38:ae:a3:aa (try 1)
[98166.553475] wlan0: authenticated
[98166.553520] wlan0: associate with AP 00:01:38:ae:a3:aa (try 1)
[98166.555480] wlan0: RX AssocResp from 00:01:38:ae:a3:aa (capab=0x471 status=0 aid=1)
[98166.555487] wlan0: associated
[98178.820290] wlan0: deauthenticating from 00:01:38:ae:a3:aa by local choice (reason=3)
[98178.820389] wlan0: deauthenticating from 00:01:38:ae:a3:aa by local choice (reason=3)
[98179.010900] wlan0: deauthenticating from 00:01:38:ae:a3:aa by local choice (reason=3)
[98179.210181] wlan0: direct probe to AP 00:01:38:ae:a3:aa (try 1)
[98179.211819] wlan0: direct probe responded
[98179.211826] wlan0: authenticate with AP 00:01:38:ae:a3:aa (try 1)
[98179.213230] wlan0: authenticated
[98179.213274] wlan0: associate with AP 00:01:38:ae:a3:aa (try 1)
[98179.215271] wlan0: RX AssocResp from 00:01:38:ae:a3:aa (capab=0x471 status=0 aid=1)
[98179.215279] wlan0: associated
[98245.610085] wlan0: deauthenticating from 00:01:38:ae:a3:aa by local choice (reason=3)
[98245.610268] wlan0: direct probe to AP 00:01:38:ae:a3:aa (try 1)
[98245.610308] wlan0: deauthenticating from 00:01:38:ae:a3:aa by local choice (reason=3)
[98246.302237] wlan0: Trigger new scan to find an IBSS to join
[98249.050671] wlan0: Trigger new scan to find an IBSS to join
[98252.713604] wlan0: Trigger new scan to find an IBSS to join
[98255.011314] wlan0: Trigger new scan to find an IBSS to join
[98256.691270] wlan0: no IPv6 routers present
[98257.821449] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[98257.821795] wlan0: deauthenticating from 00:01:38:ae:a3:aa by local choice (reason=3)
[98258.010181] wlan0: direct probe to AP 00:01:38:ae:a3:aa (try 1)
[98258.011849] wlan0: direct probe responded
[98258.011857] wlan0: authenticate with AP 00:01:38:ae:a3:aa (try 1)
[98258.013280] wlan0: authenticated
[98258.013315] wlan0: associate with AP 00:01:38:ae:a3:aa (try 1)
[98258.015318] wlan0: RX AssocResp from 00:01:38:ae:a3:aa (capab=0x471 status=0 aid=1)
[98258.015325] wlan0: associated
[98258.017533] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[98268.410047] wlan0: no IPv6 routers present
```axel@axel-desktop ~ $ dmesg | grep b43
```
[    1.478879] b43-pci-bridge 0000:03:06.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   17.464105] b43-phy1: Broadcom 4318 WLAN found (core revision 9)
[   17.644371] Registered led device: b43-phy1::tx
[   17.644382] Registered led device: b43-phy1::rx
[   17.644392] Registered led device: b43-phy1::assoc
[   17.644402] Registered led device: b43-phy1::radio
[   18.251292] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   18.352667] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   18.368363] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   18.381369] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   18.501296] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[98246.181325] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[98257.670103] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)
```axel@axel-desktop ~ $ sudo lshw -C network
```
[sudo] password for axel: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:24:8c:d4:2f:41
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=85.225.211.251 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:e800(size=256) memory:fbeff000-fbefffff memory:fbec0000-fbedffff(prefetchable)
  *-network:0
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:03:06.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:20 memory:fbffe000-fbffffff
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: AR5007G Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 7
       bus info: pci@0000:03:07.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=168 maxlatency=28 mingnt=10
       resources: memory:fafe0000-fafeffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:24:8c:b3:68:c2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=85.225.208.95 multicast=yes wireless=IEEE 802.11bg
```axel@axel-desktop ~ $ uname -mr
```
2.6.31-17-generic x86_64
```[/Code]

---

### Post by axelswe on 2010-01-30
bump

---

### Post by axelswe on 2010-02-07
bump II

---

