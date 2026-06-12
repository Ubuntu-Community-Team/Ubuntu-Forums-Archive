---
title: "AR242x wireless with hardy"
date: 2009-08-04
forum: Networking &amp; Wireless
---

### Post by Nephtys on 2009-08-04
Hi, I have a wee bit of a problem. I'm using hardy heron on an emachines e620 laptop and I can't get my wireless card to work. I have already tried madwifi, ath5k and ndiswrapper to no avail, although ath5k did make the card work but it could not find a signal.

I'd be grateful if anybody had an idea on how to solve this because I'm really clueless about now. Here's the output of lshw -C network.

```
 *-network
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ndiswrapper latency=0 module=ndiswrapper
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:c8:40:54
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.178.26 latency=0 module=r8169 multicast=yes
```

---

### Post by superprash2003 on 2009-08-04
have you looked under system->admin->hardware drivers?

---

### Post by superprash2003 on 2009-08-04
also post output of
1)iwconfig
2)sudo iwlist scanning

---

### Post by practic on 2009-08-04
I fixed my Atheros wireless woes on my netbooks by removing the Atheros Wireless cards and replacing them with Intel 3945 ABG cards. They're about $10 on eBay and will plug right into the laptop/netbook (well, you have to take the unit apart a bit to get at the card, but that's still way less time than fighting with drivers).

---

### Post by Nephtys on 2009-08-04
> have you looked under system->admin->hardware drivers? 
Yes, I have.Apparently the driver to my wireless card was not in use so I ticked the checkbox, after which I was told to reboot. I did but it didn't work; it said 'not in use' again.

```
nephtys@nephtys-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

and

```
nephtys@nephtys-laptop:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

---

### Post by Nephtys on 2009-08-05
I've disabled ndiswrapper and I have removed the native ath modules from the blacklist. After rebooting Hardware Drivers shows the following:

Atheros Hardware Access Layer Enabled | (checkbox ticked) | In use
Support for Atheros 802.11 wireless LAN cards | Enabled (checkbox ticked) | In use

lshw -C doesnt show that a driver is attached to the card though:

```
WARNING: you should run this program as super-user.
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:c8:40:54
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.178.26 latency=0 module=r8169 multicast=yes
```

```
nephtys@nephtys-laptop:~$ lsmod
Module                  Size  Used by
ath_pci               101024  0
wlan                  207728  1 ath_pci
ath_hal               192592  1 ath_pci
ipv6                  268036  8
af_packet              23812  2
rfcomm                 41744  2
l2cap                  25728  13 rfcomm
bluetooth              61028  4 rfcomm,l2cap
radeon                124192  0
drm                    82452  1 radeon
ppdev                  10372  0
powernow_k8            16704  0
cpufreq_userspace       5284  0
cpufreq_ondemand        9740  1
cpufreq_stats           7104  0
freq_table              5536  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0
cpufreq_conservative     8712  0
container               5632  0
dock                   11280  0
sbs                    15112  0
sbshc                   7680  1 sbs
iptable_filter          3840  0
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
aes_i586               33536  0
dm_crypt               15364  0
dm_mod                 62660  1 dm_crypt
parport_pc             36260  0
lp                     12324  0
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0
uvcvideo               58116  0
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
serio_raw               7940  0
psmouse                40336  0
video                  19856  0
output                  4736  1 video
battery                14212  0
ac                      6916  0
evdev                  13056  7
snd_hda_intel         346136  1
snd_pcm_oss            42144  0
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
pcspkr                  4224  0
snd_seq_dummy           4868  0
wmi_acer                9644  0
button                  9232  0
snd_seq_oss            35584  0
snd_seq_midi            9376  0
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
k8temp                  6656  0
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ati_agp                 9996  0
agpgart                34760  2 drm,ati_agp
i2c_piix4               9612  0
snd                    56996  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_core               24832  1 i2c_piix4
shpchp                 34452  0
pci_hotplug            30880  1 shpchp
soundcore               8800  1 snd
ext3                  136968  1
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
pata_acpi               8320  0
pata_atiixp             8960  0
ata_generic             8324  0
sg                     36880  0
sr_mod                 17956  0
cdrom                  37408  1 sr_mod
sd_mod                 30720  3
atiixp                  5648  0 [permanent]
ide_core              113996  1 atiixp
ahci                   28548  2
ehci_hcd               37900  0
ohci_hcd               26640  0
r8169                  34820  0
libata                159728  4 pata_acpi,pata_atiixp,ata_generic,ahci
scsi_mod              151692  4 sg,sr_mod,sd_mod,libata
usbcore               146412  4 uvcvideo,ehci_hcd,ohci_hcd
thermal                16796  0
processor              36616  3 powernow_k8,thermal
fan                     5636  0
fbcon                  42912  0
tileblit                3584  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  1
```

---

### Post by Nephtys on 2009-08-11
Taking the liberty of a bump. I'd really appreciate all the help I can get.

---

