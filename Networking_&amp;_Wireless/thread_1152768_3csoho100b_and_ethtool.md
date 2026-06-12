---
title: "3csoho100b and ethtool"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by eikaf on 2009-05-08
Hi guys,
i have 2 desktop one with debian and one with ubuntu 8.04. I installed debian with this network card 3COM SOHO 100b - TX and no problems so far from now.Ethtool is working and so on WOL and all ethtool functions.
Then i moved this nic to a fresh ubuntu installation (plugging it after installation), the nic is reconized by the sistem and i can use it with my internet connection, but when i try to setup wakeonlan ethtool gives me error with "No Data available". I know that ethtool is working for this nic because i used it on debian.
Any suggestion is appreciated.

lsmod
```

Module                  Size  Used by
af_packet              23812  2
ppdev                  10372  0
ipv6                  267908  20
sbs                    15112  0
sbshc                   7680  1 sbs
dock                   11280  0
container               5632  0
video                  19856  0
output                  4736  1 video
battery                14212  0
iptable_filter          3840  0
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0
coretemp                8448  0
tun                    12672  3
parport_pc             36260  0
lp                     12324  0
parport                37832  3 ppdev,parport_pc,lp
snd_hda_intel         346136  3
snd_pcm_oss            42144  0
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
evdev                  13056  3
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0
snd_seq_oss            35584  0
atl1e                  62364  0
agpgart                34760  0
i2c_core               24832  0
snd_seq_midi            9376  0
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                  9232  0
soundcore               8800  1 snd
shpchp                 34452  0
pci_hotplug            30880  1 shpchp
pcspkr                  4224  0
ext3                  136840  4
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0
sr_mod                 17956  0
cdrom                  37408  1 sr_mod
sd_mod                 30720  6
usbhid                 32128  0
hid                    38784  1 usbhid
ahci                   28548  5
floppy                 59588  0
libata                159600  1 ahci
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
tulip                  53536  0
ehci_hcd               37900  0
uhci_hcd               27024  0
usbcore               146412  4 usbhid,ehci_hcd,uhci_hcd
thermal                16796  0
processor              36488  3 thermal
fan                     5636  0
fbcon                  42912  0
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3

```lspci | grep 3Com
```

04:00.0 Ethernet controller: 3Com Corporation 3CSOHO100B-TX 910-A01 [tulip] (rev 31)

```lshw -C network
```

*-network
       description: Ethernet interface
       product: 3CSOHO100B-TX 910-A01 [tulip]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth3
       version: 31
       serial: 00:04:75:b4:16:2d
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.0.148 latency=64 maxlatency=128 mingnt=64 module=tulip multicast=yes


```the only difference is that ubuntu is running kernel 2.6.24, debian 2.6.26

---

### Post by eikaf on 2009-05-08
solved by myself adding 
```

NETDOWN=no

```
at the beginning of /etc/init.d/halt file.Now WOL (wake on lan) is working like a charm, i'll be testing it next week, in case i'll be updating this thread.

---

### Post by eikaf on 2009-05-09
well actually i need help again.After a while doing shutdown, i can't get up it again.

---

