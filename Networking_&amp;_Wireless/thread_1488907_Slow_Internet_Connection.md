---
title: "Slow Internet Connection"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by kiasta on 2010-05-20
I installed Ubuntu on my little cousins Acer Aspire and the wireless internet speed is very slow, I usually get around 1.2 MB/s. I have applied the firefox tweak but that is not the issue. No matter what I use to download I cannot get anything faster than 75k (even updates). I have no idea what the problem is so if someone could point me in the right direction that would be great, otherwise I will need to revert back to windows which I do not want to do because she constantly crashes it :/.

There are no other people on the network I have it encrypted so its not that either I have tried google but everything on there is from 3 years ago or older and does not work.

Here is a speedtest:

 [IMG]http://www.speedtest.net/result/820971719.png[/IMG]



Sorry, I should have read the sticky first..

lspci:

```
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
03:00.0 VGA compatible controller: nVidia Corporation ION LE VGA (rev b1)
```lsusb:

```
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
03:00.0 VGA compatible controller: nVidia Corporation ION LE VGA (rev b1)
root@canna-desktop:/home/administrator# ^C
root@canna-desktop:/home/administrator# lsusb
Bus 002 Device 003: ID 046d:c058 Logitech, Inc. 
Bus 002 Device 002: ID 04f2:0402 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0846:4260 NetGear, Inc. WG111(v3) 54 Mbps Wireless [RealTek RTL8187B]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:01:6c:6f:9c:82  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:180 errors:0 dropped:0 overruns:0 frame:0
          TX packets:180 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12732 (12.7 KB)  TX bytes:12732 (12.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:3f:f9:38:15  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::222:3fff:fef9:3815/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:323678 errors:0 dropped:0 overruns:0 frame:0
          TX packets:269110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:300326704 (300.3 MB)  TX bytes:88038434 (88.0 MB)

```iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"belkin54g"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1C:DF:CD:9A:4E   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```lsmod:

```
Module                  Size  Used by
btrfs                 458906  0 
zlib_deflate           19568  1 btrfs
crc32c                  2519  1 
libcrc32c                875  1 btrfs
ufs                    72774  0 
qnx4                    6484  0 
hfsplus                70800  0 
hfs                    40754  0 
minix                  25197  0 
ntfs                   94791  0 
vfat                    8901  0 
msdos                   6392  0 
fat                    47767  2 vfat,msdos
jfs                   172650  0 
xfs                   513904  0 
exportfs                3437  1 xfs
reiserfs              225633  0 
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
snd_hda_codec_nvhdmi     3840  1 
snd_hda_codec_realtek   203168  1 
ppdev                   5259  0 
snd_hda_intel          21877  4 
snd_hda_codec          74201  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
arc4                    1153  2 
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rtl8187                50680  0 
mac80211              204922  1 rtl8187
fbcon                  35102  72 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
led_class               2864  1 rtl8187
cfg80211              126485  2 rtl8187,mac80211
eeprom_93cx6            1333  1 rtl8187
snd                    54148  20 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63245  0 
serio_raw               3978  0 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
shpchp                 28820  0 
nvidia               9932176  80 
soundcore               6620  1 snd
agpgart                31724  1 nvidia
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_nforce2             5199  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67032  1 usbhid
ahci                   32008  2 
forcedeth              49556  0 

```Network Config:

```
*-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:01:6c:6f:9c:82
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:20 memory:fae7d000-fae7dfff ioport:d080(size=8) memory:fae7e800-fae7e8ff memory:fae7e400-fae7e40f
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:22:3f:f9:38:15
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.2 multicast=yes wireless=IEEE 802.11bg

```Ubuntu Version: 10.04

Kernel Version: 2.6.32-22-generic i686

I didn't add the kernel boot message because there was too much information for the shell and I couldn't copy everything.

---

### Post by kiasta on 2010-05-23
Any suggestions? I'm still encountering the problem, I've disabled ipv6, I've run ```
sudo pppoeconf
``` and it says wlan0 MTU is set to 1492 (or maybe 1495) and needs to be 1500, along with this message:```
          | Sorry, I scanned 2 interfaces, but the Access             &#9474; 
          &#9474; Concentrator of your provider did not respond. Please    &#9474; 
          &#9474; check your network and modem cables. Another reason      &#9474; 
          &#9474; for the scan failure may also be another running pppoe   &#9474; 
          &#9474; process which controls the modem.
```I used ```
sudo ifconfig wlan0 mtu 1500
``` but it it doesn't make any difference. I am completely at a loss, I would love to keep this on my cousins computer (so she wont crash the computer anymore) but I have no idea what the deal is with the internet speed. Any suggestions to get this thing working right?

---

### Post by kiasta on 2010-05-24
Forget it, I got it working.

---

### Post by juliua on 2010-05-24
What did you do to solve it?

---

