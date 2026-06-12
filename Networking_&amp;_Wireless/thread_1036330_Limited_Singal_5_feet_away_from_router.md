---
title: "Limited Singal 5 feet away from router"
date: 2009-01-10
forum: Networking &amp; Wireless
---

### Post by Cpuboye11 on 2009-01-10
1 ) Machine Brand and Model (PC/Laptop):

Dell Inspriron 2650

2 ) Wireless Brand, Model and Wireless Chipset:

```
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
```


Back of card

VcTnet AirXpress PC11br 11MBPS

3 ) check interface:

```
warning@warning:~$ iwconfig wlan0
wlan0     IEEE 802.11b  ESSID:"Kyles"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:6C:25:21:A4   
          Bit Rate=5.5 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=31/100  Signal level:-130 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

4 ) Check for modules:

```
warning@warning:~$ lsmod | grep "wlan_module_name"
warning@warning:~$ lsmod
Module                  Size  Used by
ndiswrapper           196380  0 
af_packet              25728  4 
binfmt_misc            16904  1 
ipv6                  263972  12 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
rfcomm                 44432  0 
sco                    18308  2 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 bnep,rfcomm,sco,l2cap
ppdev                  15620  0 
speedstep_ich          11920  0 
speedstep_lib          12676  1 speedstep_ich
cpufreq_stats          13188  0 
cpufreq_ondemand       14988  1 
cpufreq_powersave       9856  0 
freq_table             12672  3 speedstep_ich,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
pci_slot               12552  0 
wmi                    14504  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
lp                     17156  0 
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
rtl8180                36352  0 
mac80211              216820  1 rtl8180
eeprom_93cx6           10240  1 rtl8180
cfg80211               32392  2 rtl8180,mac80211
joydev                 18368  0 
pcmcia                 43052  0 
dcdbas                 15008  0 
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
snd_intel8x0           37532  3 
snd_ac97_codec        111652  1 snd_intel8x0
evdev                  17696  10 
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
battery                18436  0 
container              11520  0 
snd_seq_dummy          10884  0 
ac                     12292  0 
video                  25104  0 
output                 11008  1 video
serio_raw              13444  0 
psmouse                45200  0 
yenta_socket           31756  2 
rsrc_nonstatic         19072  1 yenta_socket
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
button                 14224  0 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                 10624  0 
intel_agp              33724  1 
soundcore              15328  1 snd
agpgart                42184  1 intel_agp
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
ext3                  133256  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
pata_acpi              12160  0 
ata_piix               24580  2 
ata_generic            12932  0 
libata                177312  3 pata_acpi,ata_piix,ata_generic
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
3c59x                  48936  0 
mii                    13440  1 3c59x
uhci_hcd               30736  0 
usbcore               148848  3 ndiswrapper,uhci_hcd
thermal                23708  0 
processor              42156  2 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 
warning@warning:~$ 


```



Ubuntu: 8.10

Okay heres the thing... The wireless card I'm using , VcTnet works but has very low signal strength. I don't know why... I have two of them and they work in windows very well. But neither of them work in Ubuntu or Puppy. They are PCMCIA or w/e it is.

What are they doing?

Well they connect to the network but after they connect they have 0-1 bar of signal strength while less then 5 feet from the router. I don't know what is casing this because this is the only brand/device that has done this.  I boot in to windows and i try it- it gets full service... Why? how do i fix this, is it possbile?

Thanks, 
Kyle 


By the way. I tried loading the driver i use within windows in to the tool called windows wireless drivers and it doesn't take it... And it is a .inf file.

---

