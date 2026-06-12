---
title: "D-Link 552 not recognized by Ubuntu, No wifi section either"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by theasian100 on 2009-07-09
Hey, Im running on an old comp, its a compaq 6000z, Its running on a 2400+ AMD CPU,

00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:08.0 Network controller: Atheros Communications Inc. AR5416 802.11abgn Wireless PCI Adapter (rev 01)
00:09.0 Communication controller: Agere Systems LT WinModem (rev 02)
00:0a.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 05)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

eth0      Link encap:Ethernet  HWaddr 00:40:ca:43:d0:83  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::240:caff:fe43:d083/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1803 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1588 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2010223 (1.9 MB)  TX bytes:248793 (242.9 KB)
          Interrupt:16 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1032 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1032 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:51600 (50.3 KB)  TX bytes:51600 (50.3 KB)

lo        no wireless extensions.

eth0      no wireless extensions.


Module                  Size  Used by
isofs                  36388  1 
udf                    88740  0 
ipv6                  267908  8 
savage                 33920  2 
drm                    82452  3 savage
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61028  4 rfcomm,l2cap
ppdev                  10372  0 
cpufreq_stats           7104  0 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
video                  19856  0 
output                  4736  1 video
container               5632  0 
sbs                    15112  0 
dock                   11280  0 
sbshc                   7680  1 sbs
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
sbp2                   24072  0 
lp                     12324  0 
snd_via82xx            29464  3 
gameport               16008  1 snd_via82xx
snd_ac97_codec        101028  1 snd_via82xx
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9728  1 snd_via82xx
snd_seq_dummy           4868  0 
i2c_prosavage           5120  0 
i2c_algo_bit            7300  1 i2c_prosavage
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
i2c_viapro              9876  0 
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_core               24832  3 i2c_prosavage,i2c_algo_bit,i2c_viapro
snd                    56996  18 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
via_ircc               27796  0 
via_agp                11136  1 
irda                  203068  1 via_ircc
button                  9232  0 
agpgart                34760  2 drm,via_agp
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
soundcore               8800  1 snd
crc_ccitt               3072  1 irda
evdev                  13056  3 
ndiswrapper           192920  0 
pcspkr                  4224  0 
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
usbhid                 32128  0 
hid                    38784  1 usbhid
sg                     36880  0 
sr_mod                 17956  1 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
pata_acpi               8320  0 
ata_generic             8324  0 
floppy                 59588  0 
pata_via               13316  3 
libata                159600  3 pata_acpi,ata_generic,pata_via
ehci_hcd               37900  0 
uhci_hcd               27024  0 
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ohci1394               33584  0 
usbcore               146412  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd
8139cp                 24704  0 
8139too                27520  0 
mii                     6400  2 8139cp,8139too
ieee1394               93752  2 sbp2,ohci1394
thermal                16796  0 
processor              36488  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 


  *-network:0 UNCLAIMED   
       description: Network controller
       product: AR5416 802.11abgn Wireless PCI Adapter
       vendor: Atheros Communications Inc.
       physical id: 8
       bus info: pci@0000:00:08.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=32
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 10
       serial: 00:40:ca:43:d0:83
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.3 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s




Ubuntu 8.04.3 LTS
2.6.24-24-generic i686

Im not real sure of what most of this stuff means, but please help me get this working, I need the Wifi to show up please!

---

### Post by superprash2003 on 2009-07-09
read this [http://forums.linuxmint.com/viewtopic.php?f=53&t=10209](http://forums.linuxmint.com/viewtopic.php?f=53&t=10209)

---

### Post by theasian100 on 2009-07-09
Im trying to do the above, and i get a problem when i get to the 
"svn co http://svn.madwifi.org/madwifi/trunk"
part, in my terminal, it shows this message

svn: PROPFIND request failed on '/madwifi-trunk'
svn: PROPFIND of '/madwifi-trunk': Could not resolve hostname `snapshots.madwifi.org': No address associated with hostname ([http://snapshots.madwifi.org](http://snapshots.madwifi.org))

---

### Post by theasian100 on 2009-07-09
Bump

---

### Post by Sankou on 2009-07-09
> 
*-network:0 UNCLAIMED   
       description: Network controller
       product: AR5416 802.11abgn Wireless PCI Adapter
       vendor: Atheros Communications Inc.
       physical id: 8
       bus info: pci@0000:00:08.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=32
This is your wireless adapter. Unclaimed means that there is no driver attached to it. All you need to do is download the driver.

[http://driverscollection.com/?file_cid=390167517302a3000180e546212](http://driverscollection.com/?file_cid=390167517302a3000180e546212)

You also need to install ndiswrapper

[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.50-1ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.50-1ubuntu1_all.deb)

That link should be it, otherwise (if you have internet some other way on the laptop) go to add programs and type ndiswrapper in the search and install from there.

In the driver download will be a .sys and .inf file in the driver section. Put them in the same folder on your desktop. Open a terminal

cd ~/Desktop/enter the name of the folder with the drivers here

then run
```

sudo ndiswrapper -i net5416.inf

```That will install the driver.

Check this by entering:
```

ndiswrapper -l

```It should come up as driver install and device present. Then enter:
```

sudo ndiswrapper -m

```Then maybe
```

sudo modprobe ndiswrapper

```If it doesn't work after that, try rebooting.

After your done, post the output of
lshw -C Network

---

### Post by Sankou on 2009-07-09
You can also try this:

[http://h1.ripway.com/bts/ANT.zip](http://h1.ripway.com/bts/ANT.zip)

It's an automated ndiswrapper troubleshooting guide that I put together. 

Hope it helps.

---

