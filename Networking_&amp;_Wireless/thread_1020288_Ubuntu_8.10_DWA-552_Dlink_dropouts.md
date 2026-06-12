---
title: "Ubuntu 8.10 DWA-552 Dlink dropouts"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by madmagic on 2008-12-24
As the title suggests, im having problems with my dlink card dropping out. Every now and then "every few mins" i loose connection to my dlink gigabit router. I am trying to move over from vista to ubuntu, and the wireless card is whats stoping me right now. Now, the card does reconnect a min later though. So it is keeping a connection, i can reach the internet. I noticed this when i was doing the updates for Ubuntu. I have tried every thing i could (including Ndiswrapper which i got the driver installed, but i couldnt connect to any wireless access points. At which point i had to do a reinstall to get the wireless working again). My computer is an acer built computer with a 8800 gt oc nvidia video card, 3 gigs of ram, a dlink dwa-552 wireless card (added to a pci slot). I dont remember what the motherboard is, sorry. If i left out any information ill be glad to post it.

lspci
```

03:01.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)

```

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:1c:25:8a:d1:70  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:222 errors:0 dropped:0 overruns:0 frame:0
          TX packets:222 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13904 (13.9 KB)  TX bytes:13904 (13.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:58:ec:cc:d5  
          inet addr:192.168.0.191  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:58ff:feec:ccd5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2056 (2.0 KB)  TX bytes:5459 (5.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1E-58-EC-CC-D5-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

iwconfig

```

wlan0     IEEE 802.11bgn  ESSID:"blue2"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:1E:58:41:0C:3D   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:5862-5D03-EE0B-5632-D537-8E42-18AF-2DF4-1FB7-8E17-B9E5-549E-FC48-D813-1EAF-247E [3]   Security mode:open
          Power Management:off
          Link Quality=56/100  Signal level:-59 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

lsmod
("mac80211              253440  1 ath9k" I think thats the one im looking for)
```

Module                  Size  Used by
aes_x86_64             16384  1 
aes_generic            36392  1 aes_x86_64
ipv6                  314312  14 
nls_iso8859_1          13568  2 
nls_cp437              15232  2 
vfat                   21120  2 
isofs                  44072  1 
fat                    64824  1 vfat
udf                    93480  0 
crc_itu_t              10496  1 udf
af_packet              29568  4 
binfmt_misc            18700  1 
rfcomm                 51104  0 
bridge                 64544  0 
stp                    11268  1 bridge
bnep                   23168  2 
sco                    20612  2 
l2cap                  33280  6 rfcomm,bnep
bluetooth              70820  6 rfcomm,bnep,sco,l2cap
ppdev                  16904  0 
powernow_k8            23684  0 
cpufreq_userspace      12420  0 
cpufreq_stats          14468  0 
cpufreq_powersave      10368  0 
cpufreq_ondemand       16400  3 
freq_table             13568  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    16392  0 
video                  28948  0 
output                 11776  1 video
sbs                    22288  0 
sbshc                  14592  1 sbs
pci_slot               13704  0 
container              12288  0 
battery                21128  0 
iptable_filter         11520  0 
ip_tables              28176  1 iptable_filter
x_tables               31752  1 ip_tables
ac                     13448  0 
sbp2                   32652  0 
lp                     19588  0 
snd_hda_intel         489264  3 
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                99208  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            42368  0 
arc4                   10368  2 
snd_seq_midi           15872  0 
ecb                    11520  2 
crypto_blkcipher       27780  1 ecb
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ath9k                 296120  0 
snd_timer              34320  2 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                51612  0 
mac80211              253440  1 ath9k
led_class              13192  0 
snd                    79432  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                 11136  0 
serio_raw              14596  0 
cfg80211               37136  1 mac80211
wmi                    15808  0 
soundcore              16800  1 snd
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm
i2c_piix4              17936  0 
i2c_core               36128  1 i2c_piix4
joydev                 20736  0 
evdev                  20512  10 
parport_pc             44200  1 
parport                50096  3 ppdev,lp,parport_pc
shpchp                 42140  0 
button                 15904  0 
pci_hotplug            39472  1 shpchp
ext2                   81296  1 
mbcache                17924  1 ext2
usb_storage            92864  2 
libusual               31784  1 usb_storage
usbhid                 39776  1 
hid                    59072  1 usbhid
sd_mod                 45864  6 
sr_mod                 24644  1 
cdrom                  47784  1 sr_mod
crc_t10dif             10240  1 sd_mod
pata_atiixp            14208  0 
sg                     45408  0 
pata_acpi              13568  0 
ohci1394               41524  0 
ieee1394              110592  2 sbp2,ohci1394
ehci_hcd               48908  0 
ata_generic            14212  0 
ohci_hcd               34972  0 
ahci                   43148  2 
usbcore               175376  7 usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd
sky2                   61444  0 
libata                200160  4 pata_atiixp,pata_acpi,ata_generic,ahci
scsi_mod              183160  6 sbp2,usb_storage,sd_mod,sr_mod,sg,libata
dock                   18464  1 libata
thermal                27424  0 
processor              47800  2 powernow_k8,thermal
fan                    13576  0 
fbcon                  51200  0 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit
fuse                   68288  3 

```



dmesg | grep "ath9k"
```

[   18.186647] ath9k: 0.1
[   18.193210] ath9k 0000:03:01.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   18.639017] phy0: Selected rate control algorithm 'ath9k_rate_control'

```

---

### Post by madmagic on 2008-12-24
bump~ I did post this a little late lastnight, but todays another day

---

### Post by madmagic on 2008-12-24
~bump again

---

### Post by Juggercat on 2009-02-09
I can confirm the exact same problem...
I am also currently trying to find a solution... but my only ability involves googling... :P

So it would be awesome if someone could check this out... :D

---

