---
title: "2 soundcards problem"
date: 2007-06-29
forum: Multimedia &amp; Video
---

### Post by Nighto on 2007-06-29
Hi,

i have an Acer TravelMate 2480 with snd_hda_intel onboard soundcard, but it have some problems such as no sound output in headphone jack, which is essential to me. That is not related to alsa drivers, because happens in windoze too.
So, i bought a cheap 15-dollar c-media usb soundcard, which works perfectly, but it loads as /dev/dsp1. This is a problem to me, because i want it to be the main soundcard (leaving the shitty onboard soundcard as the secondary one). My laptop's bios have no option to disable the onboard soundcard, so i blacklisted the onboard soundcard module.
Very well. Theoretically, the usb (already plugged when booting the computer) should be the primary soundcard, because the onboard couldn't be loaded, but that's not what happens. When booting, there's no /dev/dsp, the usb soundcard continues to be listed as /dev/dsp1. I did a symlink between them (ln -s /dev/dsp1 /dev/dsp), now general system sound works, but some games (such as my beloved Frets On Fire) don't recognize it and continue trying to load the onboard soundcard:
```

nighto@persocon:~/FretsOnFire$ ./FretsOnFire
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
Traceback (most recent call last):
  File "/home/skyostil/src/cx_Freeze-3.0.3/initscripts/Console.py", line 27, in ?
  File "src/FretsOnFire.py", line 64, in ?
  File "src/GameEngine.py", line 149, in __init__
  File "src/Audio.py", line 49, in open
pygame.error: No available audio device

```

any suggestions?

Some perhaps useful info:

```

nighto@persocon:~/FretsOnFire$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
0a:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
nighto@persocon:~/FretsOnFire$ lsmod | grep snd_hda_intel
nighto@persocon:~/FretsOnFire$ 
nighto@persocon:~/FretsOnFire$ lsmod
Module                  Size  Used by
ipt_TCPMSS              4992  1 
xt_tcpmss               3200  1 
xt_tcpudp               4224  1 
iptable_mangle          3712  1 
ip_tables              13924  1 iptable_mangle
x_tables               17028  4 ipt_TCPMSS,xt_tcpmss,xt_tcpudp,ip_tables
pppoe                  15552  2 
pppox                   5000  1 pppoe
ppp_generic            29844  6 pppoe,pppox
slhc                    7680  1 ppp_generic
binfmt_misc            13064  1 
rfcomm                 41752  0 
l2cap                  26112  5 rfcomm
bluetooth              57444  4 rfcomm,l2cap
i915                   24576  4 
drm                    81812  5 i915
ppdev                  10116  0 
cpufreq_conservative     8200  0 
cpufreq_stats           7488  0 
cpufreq_ondemand        9356  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
cpufreq_userspace       5408  0 
dev_acpi               12164  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
sony_acpi               6284  0 
container               5248  0 
dock                   10424  0 
asus_acpi              17308  0 
battery                10756  0 
video                  16260  0 
button                  8720  0 
backlight               6784  1 asus_acpi
ac                      6020  0 
sbs                    15528  0 
i2c_ec                  6016  1 sbs
i2c_core               23424  1 i2c_ec
ipv6                  274080  12 
parport_pc             36644  0 
lp                     12548  0 
parport                37576  3 ppdev,parport_pc,lp
fuse                   46996  1 
af_packet              24072  8 
joydev                 10816  0 
snd_usb_audio          79872  1 
snd_pcm_oss            45056  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                80260  2 snd_usb_audio,snd_pcm_oss
snd_page_alloc         10888  1 snd_pcm
snd_usb_lib            17536  1 snd_usb_audio
snd_hwdep              10500  1 snd_usb_audio
snd_seq_dummy           4740  0 
snd_seq_oss            33408  0 
snd_seq_midi            9600  0 
snd_rawmidi            25856  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia                 39596  0 
snd_timer              24196  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54788  12 snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bcm43xx               126952  0 
soundcore               9440  1 snd
ieee80211softmac       31360  1 bcm43xx
cdc_acm                16032  0 
xpad                    9988  0 
ieee80211              35272  2 bcm43xx,ieee80211softmac
ieee80211_crypt         7040  1 ieee80211
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
tifm_7xx1               8832  0 
tifm_core              11268  1 tifm_7xx1
psmouse                38792  0 
serio_raw               7940  0 
sky2                   43912  0 
pcmcia_core            41624  3 pcmcia,yenta_socket,rsrc_nonstatic
iTCO_wdt               12072  0 
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25372  1 
agpgart                35788  3 drm,intel_agp
shpchp                 34324  0 
pci_hotplug            33608  1 shpchp
evdev                  11008  6 
tsdev                   8768  0 
ext3                  134152  2 
jbd                    63528  1 ext3
mbcache                 9604  1 ext3
sg                     35996  0 
sr_mod                 17188  0 
cdrom                  37664  1 sr_mod
sd_mod                 23556  4 
ata_generic             9092  0 
usbhid                 26720  0 
hid                    27392  1 usbhid
ata_piix               15620  3 
libata                125848  2 ata_generic,ata_piix
scsi_mod              143116  4 sg,sr_mod,sd_mod,libata
ehci_hcd               34316  0 
generic                 5124  0 [permanent]
uhci_hcd               25488  0 
usbcore               135048  8 snd_usb_audio,snd_usb_lib,cdc_acm,xpad,usbhid,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31560  1 thermal
fan                     5636  0 
fbcon                  43296  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
nighto@persocon:~/FretsOnFire$ 
nighto@persocon:~/FretsOnFire$ 
nighto@persocon:~/FretsOnFire$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 6666:0667 Prototype product Vendor ID Smart Joy PSX, PS-PC Smart JoyPad
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
Bus 001 Device 001: ID 0000:0000  

```

---

