---
title: "Atheros AR9285 Wireless Connection"
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by tiltsideways on 2010-06-03
I recently purchased an Asus K50 laptop and upgraded it to Lucid almost instantly. Pretty much everything works out of the box, with few exceptions, one of them being the wireless connection. 

I have attempted to use wicd, and wicd can pick up nearby networks, but cannot obtain the IP address.

Apologize for the cluttered mess:

**grep: **

02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
03:00.0 Ethernet controller [0200]: Atheros Communications Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller [1969:1026] (rev b0)

[B]
ifconfig: [/B]

eth0      Link encap:Ethernet  HWaddr 48:5b:39:11:38:e2  
          inet addr:152.10.109.82  Bcast:152.10.111.255  Mask:255.255.252.0
          inet6 addr: fe80::4a5b:39ff:fe11:38e2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27221 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18785 errors:0 dropped:0 overruns:0 carrier:9
          collisions:0 txqueuelen:1000 
          RX bytes:23008535 (23.0 MB)  TX bytes:2910238 (2.9 MB)
          Interrupt:29 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 1c:4b:d6:73:e8:ce  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

**iwconfig: **

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"f2\x0D\xB71X\xA3Z%]\x05\x17X\xE9^\xD4\xAB\xB2\xCD\xC6\x9B\xB4T\x11\x0E\x82tA!=\xDC\x87"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

**lsmod:**

Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
fbcon                  35102  71 
snd_hda_codec_via      27111  1 
tileblit                2031  1 fbcon
snd_hda_intel          22005  2 
font                    7557  1 fbcon
snd_hda_codec          74201  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
bitblit                 4707  1 fbcon
snd_pcm_oss            35308  0 
softcursor              1189  1 bitblit
snd_mixer_oss          13746  1 snd_pcm_oss
vga16fb                11385  0 
snd_pcm                70886  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
vgastate                8961  1 vga16fb
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
arc4                    1153  2 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
ath9k                  67088  0 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ath9k_common            2551  1 ath9k
snd_timer              19098  2 snd_pcm,snd_seq
mac80211              209830  2 ath9k,ath9k_common
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  283218  3 
drm_kms_helper         29297  1 i915
uvcvideo               57022  0 
drm                   163143  4 i915,drm_kms_helper
snd                    54148  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath9k_hw              224171  2 ath9k,ath9k_common
videodev               34361  1 uvcvideo
soundcore               6620  1 snd
ath                     8073  2 ath9k,ath9k_hw
i2c_algo_bit            5028  1 i915
v4l1_compat            13251  2 uvcvideo,videodev
asus_laptop            17008  0 
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
cfg80211              130735  4 ath9k,ath9k_common,mac80211,ath
video                  17375  1 i915
intel_agp              24473  2 i915
agpgart                31788  2 drm,intel_agp
lp                      7028  0 
output                  1871  1 video
psmouse                63245  0 
led_class               2864  2 ath9k,asus_laptop
serio_raw               3978  0 
parport                32635  2 ppdev,lp
ahci                   32040  2 
atl1e                  27389  0 

**dmesg:**

[   25.292022] eth0: no IPv6 routers present
[   36.361404] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   36.688776] ATL1E 0000:03:00.0: irq 29 for MSI/MSI-X
[   36.688944] ATL1E 0000:03:00.0: ATL1E: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   36.689317] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   36.689507] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   36.793937] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.819162] wlan0: direct probe to AP 00:0b:86:c1:19:e1 (try 1)
[   38.826311] wlan0: direct probe to AP 00:0b:86:c1:23:21 (try 1)
[   38.829049] wlan0: direct probe responded
[   38.829054] wlan0: authenticate with AP 00:0b:86:c1:23:21 (try 1)
[   38.830932] wlan0: authenticated
[   38.830958] wlan0: associate with AP 00:0b:86:c1:23:21 (try 1)
[   38.832514] __ratelimit: 9 callbacks suppressed
[   38.832517] type=1503 audit(1275587622.914:15):  operation="open" pid=1620 parent=1609 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/lib/wicd/dhclient.conf"
[   38.834084] wlan0: RX AssocResp from 00:0b:86:c1:23:21 (capab=0x421 status=0 aid=2)
[   38.834088] wlan0: associated
[   38.834448] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   38.849079] wlan0: deauthenticating from 00:0b:86:c1:23:21 by local choice (reason=3)
[   47.209047] eth0: no IPv6 routers present
[   48.872033] wlan0: no IPv6 routers present
[   79.102339] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   79.342839] ATL1E 0000:03:00.0: irq 29 for MSI/MSI-X
[   79.342997] ATL1E 0000:03:00.0: ATL1E: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   79.343989] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   79.344656] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   79.515565] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   79.771125] ATL1E 0000:03:00.0: irq 29 for MSI/MSI-X
[   79.771312] ATL1E 0000:03:00.0: ATL1E: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   79.771806] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   79.772156] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   79.953025] ATL1E 0000:03:00.0: irq 29 for MSI/MSI-X
[   79.953182] ATL1E 0000:03:00.0: ATL1E: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   79.954126] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   79.954680] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   81.998990] type=1503 audit([1275587666]("http://wncln.wncln.org/search/i?1275587666&startLimit=&searchscope=1&SORT=A&endLimit=&sid=libxasu").078:16):  operation="open" pid=1791 parent=1772 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/lib/wicd/dhclient.conf"
[   90.248070] eth0: no IPv6 routers present
[ 1422.586865] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1422.838664] ATL1E 0000:03:00.0: irq 29 for MSI/MSI-X
[ 1422.838822] ATL1E 0000:03:00.0: ATL1E: eth0 NIC Link is Up<100 Mbps Full Duplex>
[ 1422.839798] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1422.840418] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1422.973913] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1425.030391] wlan0: direct probe to AP 00:0b:86:c1:19:e1 (try 1)
[ 1425.042909] type=1503 audit(1275589009.123:17):  operation="open" pid=2346 parent=2334 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/lib/wicd/dhclient.conf"
[ 1425.057702] wlan0: direct probe to AP 00:0b:86:c1:23:21 (try 1)
[ 1425.061640] wlan0: direct probe responded
[ 1425.061643] wlan0: authenticate with AP 00:0b:86:c1:23:21 (try 1)
[ 1425.064053] wlan0: authenticated
[ 1425.064078] wlan0: associate with AP 00:0b:86:c1:23:21 (try 1)
[ 1425.068378] wlan0: RX AssocResp from 00:0b:86:c1:23:21 (capab=0x421 status=0 aid=1)
[ 1425.068383] wlan0: associated
[ 1425.068878] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1425.081095] wlan0: deauthenticating from 00:0b:86:c1:23:21 by local choice (reason=3)
[ 1433.380062] eth0: no IPv6 routers present
[ 1435.256061] wlan0: no IPv6 routers present
[ 1447.028436] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1447.307449] ATL1E 0000:03:00.0: irq 29 for MSI/MSI-X
[ 1447.307640] ATL1E 0000:03:00.0: ATL1E: eth0 NIC Link is Up<100 Mbps Full Duplex>
[ 1447.308205] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1447.308558] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1447.476511] ATL1E 0000:03:00.0: irq 29 for MSI/MSI-X
[ 1447.476666] ATL1E 0000:03:00.0: ATL1E: eth0 NIC Link is Up<100 Mbps Full Duplex>
[ 1447.478268] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1447.478583] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1449.524806] type=1503 audit(1275589033.606:18):  operation="open" pid=2417 parent=2402 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/lib/wicd/dhclient.conf"
[ 1458.344052] eth0: no IPv6 routers present[B]

sudo lshw -C network:[/B]

*-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 1c:4b:d6:73:e8:ce
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet  physical wireless
       configuration: broadcast=yes driver=ath9k  driverversion=2.6.32-22-generic-pae firmware=N/A latency=0 link=no  multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:feaf0000-feafffff
  *-network
       description: Ethernet interface
       product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 48:5b:39:11:38:e2
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet  physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E  driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=152.10.109.82  latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:febc0000-febfffff ioport:ec00(size=128)

**iwlist scan:**

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

---

### Post by tiltsideways on 2010-06-04
Still unable to figure this out. Thought it might be an issue with Wicd, but same issue with Wifi Radar. I can detect wireless networks from my apartment, but when I try to connect to them, I get garbled letters, numbers, and symbols. Wired connection works just fine.

---

### Post by harry003 on 2010-06-04
Windows 7 drivers probably do not work with your card.

Find an XP driver and run ndiswrapper and it should work.

At least that was my experience.

---

### Post by tiltsideways on 2010-06-08
Thanks for the suggestion! Downloaded the graphical interface and sought out a driver on the Atheros.cz page. Rebooted. Doesn't seem to be working. 

Tried downloading the latest compat-wireless and seeking out the ath9k drivers. Rebooted. 

Oddly, now, when I attempt to use WICD to connect wirelessly, it calls every network "None."

Still no luck. Throwing in the towel for the day.

---

