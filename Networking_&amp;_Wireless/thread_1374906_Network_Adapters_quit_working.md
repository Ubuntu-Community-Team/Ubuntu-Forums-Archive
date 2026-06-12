---
title: "Network Adapters quit working"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by Myiagros on 2010-01-07
I've run into this problem a couple times now since switching to 9.10 and it seems to happen after some updates.

I'm running a Dell Inspiron 1501 and had no issues using the b43-fwcutter to get the wireless working. I have been using wicd for my network manager.

Yesterday before leaving from work I installed some system updates and shut down. This morning when i came in I booted up and when logging in wicd was asking for authorization to use the network adapters. After putting in my password everything started up but wicd would not start. Under Network Tools I checked the adapters and nothing was up, ifconfig confirmed this.

After restarting again wicd again asked for authorization, still no change to the adapters so I removed wicd. Now the b43-fwcutter driver is not being shown as activated and I have no way to connect to the internet with my laptop, just my desktop, so I am unable to use the package manager to reinstall it as well as wicd.

As I stated earlier this has happened a few times, at least 2-3, and I've had to do a complete reinstall of Ubuntu and all my programs which is nothing short of a pain.

Is there any solution to this problem or will I just have to do another reinstall and spend a few hours downloading everything again?

---

### Post by pedro_orange on 2010-01-07
Run:

> lshw -C network

See if your wireless device is bound to a driver. Ensure it's loaded with:

> lsmod

You can also check:

> iwconfig

To see if the kernel can see it.
Your card make / model would be helpful from a troubleshooting / Googling point of view.

---

### Post by Myiagros on 2010-01-07
lshw -C network

>   *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:c0200000-c0203fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:92:39:77
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:21 memory:c0300000-c0301fff
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1b:fc:e9:75:fc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yeslsmod

> Module                  Size  Used by
isofs                  31620  0 
udf                    80900  0 
crc_itu_t               1852  1 udf
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
cbc                     3516  715 
aes_i586                8124  716 
aes_generic            27484  1 aes_i586
binfmt_misc             8356  1 
ppdev                   6688  0 
vboxnetflt             84840  0 
vboxnetadp             78344  0 
vboxdrv               121160  1 vboxnetflt
joydev                 10272  0 
dm_crypt               12928  0 
snd_hda_codec_idt      59844  1 
arc4                    1660  2 
iptable_filter          3100  0 
ecb                     2524  3 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
dell_wmi                2564  0 
dell_laptop             8128  0 
dcdbas                  7292  1 dell_laptop
b43                   122136  0 
mac80211              181076  1 b43
cfg80211               93052  2 b43,mac80211
sdhci_pci               7100  0 
sdhci                  17472  1 sdhci_pci
led_class               4096  2 b43,sdhci
snd_seq_dummy           2656  0 
psmouse                56500  0 
serio_raw               5280  0 
ricoh_mmc               3676  0 
k8temp                  4188  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
i2c_piix4               9932  0 
shpchp                 32272  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
usbhid                 38208  0 
b44                    28684  0 
usb_storage            52576  1 
mii                     5212  1 b44
video                  19380  0 
output                  2780  1 video
ssb                    35300  2 b43,b44
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
ati_agp                 6760  0 
agpgart                34988  3 ttm,drm,ati_agpiwconfig

> wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


---

### Post by pedro_orange on 2010-01-08
That says you're adapter is working and that it is just not associated to an access point. Can't you see it under networking?

You should find all the information here: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

