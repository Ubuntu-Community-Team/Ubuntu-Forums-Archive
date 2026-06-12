---
title: "No Wireless under Ubuntu 8.10"
date: 2009-01-30
forum: Networking &amp; Wireless
---

### Post by ronparent on 2009-01-30
PC laptop is used booted in Win Vista with wlan funtional.  I've installed Ubuntu 8.10 on a usb flashdrive. The wlan is switched on but the blue wlan led never lights when booted with Ububtu. I'm stumped. Is there a resolution here for use of this box with Ubuntu (other than plugging into eth0?

Here is the requested output.
hp model dv6449us
************************************************************************
ron5@ron5-usbdrv:~$ lspci

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
......................
ron5@ron5-usbdrv:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 13fe:1f00 Kingston Technology Company Inc. DataTraveler 2.0 4GB Flash Drive
Bus 001 Device 002: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
................................

ron5@ron5-usbdrv:~$ lspci -nn | grep Broadcom
03:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)

ron5@ron5-usbdrv:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:85:9a:d4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

ron5@ron5-usbdrv:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

ron5@ron5-usbdrv:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
**************************************************************
ron5@ron5-usbdrv:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    57376  1 vfat
binfmt_misc            16904  1 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
rfcomm                 44432  0 
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 sco,rfcomm,bnep,l2cap
ppdev                  15620  0 
powernow_k8            22148  1 
cpufreq_ondemand       14988  1 
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
freq_table             12672  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
sbs                    19464  0 
container              11520  0 
sbshc                  13440  1 sbs
pci_slot               12680  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
snd_hda_intel         384176  2 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
pcspkr                 10624  0 
evdev                  17696  11 
psmouse                45200  0 
snd_seq_oss            38528  0 
serio_raw              13444  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               63624  0 
snd                    63268  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
compat_ioctl32          9344  1 uvcvideo
soundcore              15328  1 snd
sdhci_pci              15360  0 
videodev               41344  1 uvcvideo
sdhci                  23940  1 sdhci_pci
v4l1_compat            22404  2 uvcvideo,videodev
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ricoh_mmc              11904  0 
mmc_core               58268  1 sdhci
k8temp                 12416  0 
isp1760                26400  0 
i2c_nforce2            14468  0 
nvidia               4717332  32 
agpgart                42184  1 nvidia
i2c_core               31892  2 i2c_nforce2,nvidia
wl                   1080212  0 
ieee80211_crypt        13572  1 wl
video                  25232  0 
output                 11008  1 video
wmi                    14504  0 
battery                18436  0 
ac                     12292  0 
button                 14224  0 
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  4 
crc_t10dif              9984  1 sd_mod
pata_acpi              12160  0 
ata_generic            12932  0 
sg                     39732  0 
usb_storage            82752  3 
libusual               30356  1 usb_storage
ohci1394               37936  0 
sata_nv                30600  0 
pata_amd               18692  0 
ieee1394               96324  2 sbp2,ohci1394
forcedeth              61328  0 
ohci_hcd               32016  0 
ehci_hcd               43788  0 
libata                178208  4 pata_acpi,ata_generic,sata_nv,pata_amd
scsi_mod              155212  6 sbp2,sr_mod,sd_mod,sg,usb_storage,libata
usbcore               149360  7 uvcvideo,isp1760,usb_storage,libusual,ohci_hcd,ehci_hcd
dock                   16656  1 libata
ssb                    40580  0 
thermal                23708  0 
processor              42156  4 powernow_k8,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 
dm_raid4_5             73996  0 
dm_region_hash         19456  1 dm_raid4_5
dm_mem_cache           12800  1 dm_raid4_5
dm_message             11008  1 dm_raid4_5
dm_mirror              27008  0 
dm_log                 17924  3 dm_raid4_5,dm_region_hash,dm_mirror
dm_mod                 63432  3 dm_raid4_5,dm_mirror,dm_log

Excuse volume of this post - but I saw nothing applicable
**********************************************************************
$ dmesg
Lots of data - but I saw nothing here either (front end of output may have been truncated).

*******************************************************************

ron5@ron5-usbdrv:~$ sudo lshw -C network
[sudo] password for ron5: 
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 8a:6c:f4:76:bd:82
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
**************************************************************************
ron5@ron5-usbdrv:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.
**************************************************************************

ron5@ron5-usbdrv:~$ lsb_release -d
Description:	Ubuntu 8.10

ron5@ron5-usbdrv:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...  

*******************************************************************************

---

### Post by ronparent on 2009-01-31
Problem solved! I am sending this from the laptop hooked to the wlan now.

Thanks to Jamie Jackson and the "HowTo: Broadcom BCM43xx in 5 minutes with ndiswrapper/WPA for fresh installs" post. I did have to run the follow-up debug routines to get it running - eventually the WiFi hookups showed up in the panel.:D

---

