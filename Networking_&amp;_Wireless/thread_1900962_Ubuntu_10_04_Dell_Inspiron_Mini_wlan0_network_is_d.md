---
title: "Ubuntu 10 04 Dell Inspiron Mini wlan0 network is down"
date: 2011-12-27
forum: Networking &amp; Wireless
---

### Post by BARNESJS on 2011-12-27
while playing in the terminal i think i disconnected my wireless network,  i had 8.04 hardy heron and tried upgrading to 10.04 to try to fix the problem but it didn't get fixed,  i have looked at other posts but cant make sense of any of this output information,  im a ubuntu newbie, here is some info that i figured is helpful

it seems in a couple places the network is simply disconnected but i dont have a clue on how to reconnect it, i also dont know the cool trick for posting your terminal displace nicely in a post, sorry!

scotty@Hebert:~$ sudo lshw -C network
[sudo] password for scotty: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:24:e8:95:2c:03
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:24 ioport:2000(size=256) memory:d8410000-d8410fff(prefetchable) memory:d8400000-d840ffff(prefetchable) memory:d8420000-d843ffff(prefetchable)
  *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:d8000000-d8003fff
  *-network DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:23:08:6e:b5:c4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
scotty@Hebert:~$ lsmod
Module                  Size  Used by
btrfs                 462393  0 
zlib_deflate           19568  1 btrfs
crc32c                  2519  1 
libcrc32c                875  1 btrfs
ufs                    72774  0 
qnx4                    6484  0 
hfsplus                70800  0 
hfs                    40754  0 
minix                  25197  0 
ntfs                   94791  0 
vfat                    8933  0 
msdos                   6392  0 
fat                    47767  2 vfat,msdos
jfs                   172461  0 
xfs                   513478  0 
exportfs                3437  1 xfs
reiserfs              225481  0 
rtl8187                50680  0 
eeprom_93cx6            1333  1 rtl8187
binfmt_misc             6587  1 
rfcomm                 33421  4 
sco                     7917  2 
ppdev                   5259  0 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30624  16 rfcomm,bnep
joydev                  8740  0 
snd_hda_codec_realtek   203376  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
arc4                    1153  2 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
dell_wmi                1793  0 
b43                   163556  0 
uvcvideo               57374  0 
compal_laptop           2034  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
mac80211              205402  2 rtl8187,b43
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
dcdbas                  5422  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
psmouse                63677  0 
cfg80211              126144  3 rtl8187,b43,mac80211
btusb                  11053  2 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
i2c_isch                3311  0 
serio_raw               3978  0 
vga16fb                11385  1 
led_class               2864  2 rtl8187,b43
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
vgastate                8961  1 vga16fb
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usb_storage            39841  0 
r8169                  34140  0 
pata_sch                1963  2 
mii                     4381  1 r8169
ssb                    38934  1 b43
scotty@Hebert:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

pan0      Interface doesn't support scanning.

scotty@Hebert:~$ uname -mr
2.6.32-33-generic i686
scotty@Hebert:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:23:08:6e:b5:c4  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

scotty@Hebert:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
scotty@Hebert:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
scotty@Hebert:~$ /etc/network/interfaces
bash: /etc/network/interfaces: Permission denied
scotty@Hebert:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:24:E8:95:2C:03

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        00:23:08:6E:B5:C4

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points

---

