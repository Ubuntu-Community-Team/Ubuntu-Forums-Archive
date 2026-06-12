---
title: "Slow transfer speeds over WLAN only on Ubuntu computer"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by ryuko2007 on 2009-01-20
So I recently installed Ubuntu on a tower I build from spare parts(not terribly old) that I had left over after upgrading several computers. After getting ubuntu [correctly] installed on the box I set about configuring my samba fileshare and whatnot. I'm using an external hard drive connected through firewire400 as my network storage device, I get good read/write speeds (about 24-26MBps) locally, meaning from the tower to the hard drive but whenever I try to transfer files to and from the server through the network I'm getting excessivly slow speeds, usually around 800KBps to 1MBps. I have tested other computers on the network and filesharing between them doesnt seem to be an issue, i can usally get around 10-12MBps. On the tower I'm using a usb wireless adapter plugged into a usb 2.0 port. I'm wondering If you guys think my issue could be some setting on Ubuntu, or if it could be an issue with my hardware. Thanks in advance for the help. In case it matters this is my first go with Ubuntu(or linux for that matter) however I am comfortable with the terminal if I need to use it

--Edit-- Just read note about what to include when posting for help

Make/Model - Custome built, using DFI N4F Ultra D Lanparty Motherboard

$ sudo lsusb

Bus 002 Device 019: ID 045e:0027 Microsoft Corp. SideWinder PnP GamePad
Bus 002 Device 018: ID 124b:4d01 Nyko (Honey Bee) Airflo EX Joystick
Bus 002 Device 017: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 002 Device 005: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 002 Device 004: ID 03f0:4c11 Hewlett-Packard PSC 1500 series
Bus 002 Device 003: ID 050d:705c Belkin Components F5D7050 v4000 Wireless Adapter
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"4997YoungRd"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1D:7E:E2:3F:DA   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=79/100  Signal level:35/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:01:29:f6:7f:78  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:01:29:f6:36:6c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth0:avahi Link encap:Ethernet  HWaddr 00:01:29:f6:7f:78  
          inet addr:169.254.7.138  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6772 (6.7 KB)  TX bytes:6772 (6.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:b3:8b:f5  
          inet addr:10.23.2.102  Bcast:10.23.2.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:feb3:8bf5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:880084 errors:0 dropped:0 overruns:0 frame:0
          TX packets:958015 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:187612589 (187.6 MB)  TX bytes:529959470 (529.9 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-50-B3-8B-F5-62-66-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


$ lsmod

Module                  Size  Used by
sidewinder             19328  0 
gameport               19468  1 sidewinder
isofs                  40100  0 
udf                    88228  0 
crc_itu_t              10112  1 udf
binfmt_misc            16904  1 
sco                    18308  0 
bridge                 56980  0 
stp                    10628  1 bridge
rfcomm                 44432  0 
bnep                   20480  0 
l2cap                  30464  4 rfcomm,bnep
bluetooth              61924  4 sco,rfcomm,bnep,l2cap
ppdev                  15620  0 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
cpufreq_ondemand       14988  0 
freq_table             12672  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    14600  0 
cpufreq_powersave       9856  0 
container              11520  0 
sbs                    19464  0 
pci_slot               12552  0 
video                  25104  0 
output                 11008  1 video
sbshc                  13440  1 sbs
wmi                    14504  0 
battery                18436  0 
ipv6                  263460  16 
af_packet              25600  8 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
parport_pc             39460  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
loop                   23180  0 
nvidia               7103684  34 
pcspkr                 10624  0 
agpgart                42184  1 nvidia
k8temp                 12416  0 
shpchp                 38036  0 
pci_hotplug            35236  1 shpchp
joydev                 18240  0 
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25348  1 ecb
evdev                  17696  6 
zd1211rw               53124  0 
usblp                  20352  0 
mac80211              216692  1 zd1211rw
cfg80211               32392  1 mac80211
snd_intel8x0           37532  3 
snd_ac97_codec        110372  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46720  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83332  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38400  0 
button                 14224  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29832  2 snd_pcm,snd_seq
i2c_nforce2            14596  0 
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_core               31892  2 nvidia,i2c_nforce2
snd                    63268  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16264  2 snd_intel8x0,snd_pcm
ext3                  133000  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
usbhid                 35968  0 
hid                    50560  1 usbhid
sbp2                   29708  1 
sd_mod                 42264  5 
crc_t10dif              9984  1 sd_mod
sr_mod                 22212  0 
cdrom                  43040  1 sr_mod
sg                     39220  0 
sata_nv                30472  0 
pata_acpi              12160  0 
pata_amd               18436  2 
ata_generic            12804  0 
skge                   48272  0 
ohci1394               38192  1 
libata                176032  4 sata_nv,pata_acpi,pata_amd,ata_generic
ieee1394               96452  2 sbp2,ohci1394
forcedeth              61968  0 
scsi_mod              155212  5 sbp2,sd_mod,sr_mod,sg,libata
dock                   16656  1 libata
ohci_hcd               32144  0 
ehci_hcd               43916  0 
usbcore               149360  6 zd1211rw,usblp,usbhid,ohci_hcd,ehci_hcd
thermal                23708  0 
processor              42284  1 thermal
fan                    12420  0 
fbcon                  47392  0 
tileblit               10752  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60700  5 


$ dmesg | grep wlan
[  114.239187] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  179.267053] wlan0: authenticate with AP 00:1d:7e:e2:3f:da
[  179.270237] wlan0: authenticated
[  179.270244] wlan0: associate with AP 00:1d:7e:e2:3f:da
[  179.273048] wlan0: RX AssocResp from 00:1d:7e:e2:3f:da (capab=0x431 status=0 aid=2)
[  179.273054] wlan0: associated
[  179.273273] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  190.250007] wlan0: no IPv6 routers present

---

### Post by MaindotC on 2009-02-05
I only get 24 mbps with my F5D7050 :(  I'm also looking for a way to fix this!  I have a similar output to yours except my lsmod for the wireless module is:
```

ieee80211softmac       34688  1 zd1211rw
ieee80211              38344  2 zd1211rw,ieee80211softmac
ieee80211_crypt         8192  1 ieee80211

```

---

