---
title: "Atheros  Wireless Conundrum inside an Enigma"
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by genestar on 2009-07-01
I am a recent convert and I'm trying to get my wireless running.Where do I even begin? Here is the ticket in the correct format.


1) acer aspire 5720z
2) Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
3)genestar@genestar-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:6d:9a:65  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe6d:9a65/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:174111 errors:0 dropped:0 overruns:0 frame:0
          TX packets:227200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:91369266 (87.1 MB)  TX bytes:190988275 (182.1 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1406 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1406 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:71364 (69.6 KB)  TX bytes:71364 (69.6 KB)

genestar@genestar-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

4)Module                  Size  Used by
ipv6                  267780  10 
af_packet              23812  2 
i915                   32512  2 
drm                    82580  3 i915
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
acpi_cpufreq           10796  1 
cpufreq_ondemand        9740  1 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8712  0 
cpufreq_userspace       5284  0 
sbs                    15112  0 
dock                   11280  0 
container               5632  0 
sbshc                   7680  1 sbs
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
acer_acpi              18112  0 
led_class               6020  1 acer_acpi
psmouse                40336  0 
serio_raw               7940  0 
evdev                  13056  8 
pcspkr                  4224  0 
uvcvideo               58116  0 
snd_hda_intel         344728  3 
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
sdhci                  19076  0 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
mmc_core               51460  1 sdhci
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
ricoh_mmc               4352  0 
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
battery                14212  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
wmi_acer                9644  1 acer_acpi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ac                      6916  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
video                  19856  0 
output                  4736  1 video
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
soundcore               8800  1 snd
button                  9232  0 
intel_agp              25492  1 
agpgart                34760  3 drm,intel_agp
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
ext3                  136712  2 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sd_mod                 30720  4 
ata_piix               19588  0 
pata_acpi               8320  0 
ahci                   28420  3 
ata_generic             8324  0 
ohci1394               33584  0 
libata                159344  4 ata_piix,pata_acpi,ahci,ata_generic
scsi_mod              151436  5 sbp2,sr_mod,sg,sd_mod,libata
ieee1394               93752  2 sbp2,ohci1394
tg3                   116228  0 
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  4 uvcvideo,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 
5)[   18.567999] eth0: Tigon3 [partno(BCM95787m) rev b002 PHY(5787)] (PCI Express) 10/100/1000Base-T Ethernet 00:1b:38:6d:9a:65
[   18.568007] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[   18.568010] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   44.740516] eth0: no IPv6 routers present
6)PCI (sysfs)  
7)lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

8)Ubuntu 8.04
9)2.6.24-16-generic i686
10) * Reconfiguring network interfaces...                                   [ OK ]

---

### Post by t0mppa on 2009-07-01
Well, you posted pretty much everything but the output of **lshw -c network**, which would tell us whether your wireless interface is disabled or just not getting associated with any drivers. Although since no drivers appear to be loaded, that'd lead towards it being disabled.

Also, just to make sure, check that you haven't accidently disabled the wireless through a kill switch (laptops often have buttons for this), as that happens fairly often around here and causes behavior like this.

---

### Post by MaindotC on 2009-07-01
Try the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).

---

