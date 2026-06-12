---
title: "d-link wua-1340 usb wireless intermittent connectivity"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by Foxuvius on 2009-02-10
[FONT="Arial"]Hi!  I have installed Ubunutu 8.10 on a formerly WinXP PC.  The install is fine.  The problem I am having is that I have a d-link wua-1340 usb wireless network card.  It almost always connects via network manager. However it rarely serves web onto the desktop.  i.e. Firefox, Pidgin, and Update cannot connect via their various ports.  

Based on other threads I have run the following commands to determine configuration.  It's long list.

If anyone has any suggestions I would really appreciate it.[/FONT]  
[FONT="Courier New"]
[SIZE="3"]**sudo lshw -C Network**[/SIZE]

  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 10
       serial: 00:16:76:4e:92:57
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:58:9e:3a:ca
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.16 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: de:6d:d7:a5:07:06
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


[SIZE="3"]**sudo lspci**[/SIZE]

00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:03.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)



**[SIZE="3"]sudo ifconfig && iwconfig[/SIZE]**
eth1      Link encap:Ethernet  HWaddr 00:16:76:4e:92:57  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xde00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:83 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4279 (4.2 KB)  TX bytes:4279 (4.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:58:9e:3a:ca  
          inet addr:192.168.0.16  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3890 (3.8 KB)  TX bytes:4215 (4.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1E-58-9E-3A-CA-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.


wlan0     IEEE 802.11bg  ESSID:"WLAN"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:13:F7:AB:24:B6   
          Bit Rate=54 Mb/s   Tx-Power=23 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=67/100  Signal level:-78 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
pan0      no wireless extensions.



[SIZE="3"]**lsmod**[/SIZE]
Module                  Size  Used by
af_packet              25728  4 
binfmt_misc            16904  1 
radeon                147616  2 
drm                    86056  3 radeon
rfcomm                 44432  0 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,sco,bnep,l2cap
ppdev                  15620  0 
speedstep_lib          12676  0 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  0 
freq_table             12672  2 cpufreq_stats,cpufreq_ondemand
video                  25232  0 
output                 11008  1 video
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
pci_slot               12680  0 
wmi                    14504  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
lp                     17156  0 
snd_hda_intel         384176  3 
tuner_simple           22288  1 
snd_pcm_oss            46848  0 
tuner_types            21888  1 tuner_simple
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
wm8775                 13740  0 
cx25840                35760  0 
snd_seq_dummy          10884  0 
evdev                  17696  6 
tuner                  33096  0 
arc4                    9984  2 
serio_raw              13444  0 
ivtv                  151204  0 
psmouse                45200  0 
ecb                    10880  2 
videodev               41344  2 tuner,ivtv
v4l1_compat            22404  1 videodev
compat_ioctl32          9344  1 ivtv
crypto_blkcipher       25476  1 ecb
snd_seq_oss            38528  0 
i2c_algo_bit           14340  1 ivtv
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
cx2341x                21124  1 ivtv
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
pcspkr                 10624  0 
v4l2_common            19840  5 wm8775,cx25840,tuner,ivtv,cx2341x
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
tveeprom               20228  1 ivtv
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
rt73usb                30464  0 
crc_itu_t              10112  1 rt73usb
rt2x00usb              18816  1 rt73usb
rt2x00lib              36224  2 rt73usb,rt2x00usb
rfkill                 17176  1 rt2x00lib
led_class              12164  1 rt2x00lib
mac80211              216820  2 rt2x00usb,rt2x00lib
cfg80211               32392  2 rt2x00lib,mac80211
lirc_mceusb2           20228  0 
lirc_dev               20020  1 lirc_mceusb2
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
button                 14224  0 
i2c_piix4              16144  0 
i2c_core               31892  9 tuner_simple,wm8775,cx25840,tuner,ivtv,i2c_algo_bit,v4l2_common,tveeprom,i2c_piix4
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
ati_agp                14988  0 
agpgart                42184  2 drm,ati_agp
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
pata_acpi              12160  0 
ata_generic            12932  0 
8139too                31616  0 
pata_atiixp            12800  0 
sata_sil               15752  2 
8139cp                 27520  0 
mii                    13440  2 8139too,8139cp
ohci_hcd               32016  0 
ehci_hcd               43788  0 
libata                178208  4 pata_acpi,ata_generic,pata_atiixp,sata_sil
usbcore               149360  6 rt73usb,rt2x00usb,lirc_mceusb2,ohci_hcd,ehci_hcd
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 



**[SIZE="3"]iwlist scan[/SIZE]**
lo        Interface doesn't support scanning.
eth1      Interface doesn't support scanning.
wmaster0  Interface doesn't support scanning.
wlan0     Scan completed :
          Cell 01 - Address: 00:13:F7:AB:24:B6
                    ESSID:"WLAN"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=67/100  Signal level:-78 dBm  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=00000000885401c9
                    Extra: Last beacon: 44ms ago
pan0      Interface doesn't support scanning.


[SIZE="3"]**uname -a**[/SIZE]
Linux alan-desktop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux[/FONT]

Again, if anyone has any suggestions that would be great.

---

### Post by Foxuvius on 2009-02-11
I just want to add the computer is an MDG (generic Canadian PC maker) with an Intel processor 3.06 ghz.

---

