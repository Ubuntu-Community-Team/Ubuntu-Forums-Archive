---
title: "wireless on a new desktop -- f5d6050"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by bedake on 2009-01-12
I just installed Ubuntu on a new desktop and I am trying to get wireless working.  I have a belkin f5d6050 that is recognized by ubuntu but not by the network manager.

Here is the output of various commands.


> 
bedake@BCU-L:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  Nickname:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.



> bedake@BCU-L:~$ lsmod
Module                  Size  Used by
ipv6                  263972  14 
af_packet              25728  2 
binfmt_misc            16904  1 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
rfcomm                 44432  0 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 sco,bnep,rfcomm,l2cap
ppdev                  15620  0 
cpufreq_ondemand       14988  0 
cpufreq_stats          13188  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
container              11520  0 
sbs                    19464  0 
video                  25104  0 
output                 11008  1 video
pci_slot               12552  0 
sbshc                  13440  1 sbs
wmi                    14504  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
joydev                 18368  0 
snd_rawmidi            29824  1 snd_seq_midi
cfi_cmdset_0002        30720  1 
cfi_util               11392  1 cfi_cmdset_0002
jedec_probe            19968  0 
snd_hda_intel         381488  5 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
cfi_probe              13568  0 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
gen_probe              11264  2 jedec_probe,cfi_probe
ck804xrom              13060  0 
snd_pcm                83204  3 snd_hda_intel,snd_pcm_oss
at76_usb              101732  0 
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mtd                    23560  3 cfi_cmdset_0002,ck804xrom
psmouse                45200  0 
evdev                  17696  8 
fglrx                1813960  31 
chipreg                11012  3 jedec_probe,cfi_probe,ck804xrom
snd_timer              29960  2 snd_seq,snd_pcm
serio_raw              13444  0 
snd                    63268  18 snd_seq_oss,snd_rawmidi,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_pcm,snd_seq_device,snd_timer
pcspkr                 10624  0 
i2c_nforce2            14468  0 
soundcore              15328  1 snd
map_funcs               9984  1 ck804xrom
agpgart                42184  1 fglrx
i2c_core               31892  1 i2c_nforce2
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
button                 14224  0 
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
sata_nv                30600  0 
pata_acpi              12160  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
ohci1394               37936  0 
ieee1394               96324  2 sbp2,ohci1394
pata_amd               18692  2 
ata_generic            12932  0 
forcedeth              61328  0 
libata                177312  4 sata_nv,pata_acpi,pata_amd,ata_generic
scsi_mod              155212  5 sbp2,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ohci_hcd               31888  0 
ehci_hcd               43276  0 
usbcore               148848  5 at76_usb,usbhid,ohci_hcd,ehci_hcd
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 





> bedake@BCU-L:~$ sudo lshw -C network
[sudo] password for bedake: 
  *-network:0 DISABLED    
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:30:bd:66:8a:87
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=at76_usb driverversion=0.14beta1 firmware=0.100.5-78 wireless=IEEE 802.11b
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ca:19:bd:90:58:ed
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
bedake@BCU-L:~$ 



---

### Post by bedake on 2009-01-12
I edited the first post to provide more information.


It says wlan0 is disabled, how does one enable it?

---

### Post by bedake on 2009-01-13
My apologies for the shameless bump,

I have had no success  in finding a solution for my problem after much searching.  Earlier in the day, I unplugged the belkin f5d6050 wireless adapter and restarted, upon booting, network manager displays that the wireless networks are unmanaged and wlan0 is not displayed as it should be.

Seeing this I ran iwlist wlan0 scan and was able to successfully scan for networks.  Upon running nm-tool:

> bedake@BCU-L:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 ----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        00:04:4B:03:2E:31

  Capabilities:
    Supported:       yes
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Settings

  IPv4 Settings:
    Address:         76.181.71.194
    Prefix:          19 (255.255.224.0)
    Gateway:         76.181.64.1

    DNS:             65.24.7.10
    DNS:             65.24.7.11


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            at76_usb
  State:             unmanaged
  Default:           no
  HW Address:        00:00:00:00:00:00

  Capabilities:
    Supported:       yes

  Wireless Settings
    WEP Encryption:  yes

  Wireless Access Points



I see that wlan0 state is unmanaged, is this related?  I assume I want to make it managed, how does one go about this?

Thank you very much for any insight.

---

### Post by bedake on 2009-01-17
I am still unable to get this working, I am at a loss for any more information to provide.  This is a shameless bump.

Thanks

---

### Post by bedake on 2009-01-28
bump again

---

