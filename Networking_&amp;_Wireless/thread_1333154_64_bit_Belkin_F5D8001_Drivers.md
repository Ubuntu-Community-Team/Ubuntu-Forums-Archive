---
title: "64 bit Belkin F5D8001 Drivers"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by gordonreid1992 on 2009-11-21
I'm running a Belkin N1 Wireless Card, I've installed the windows drivers but I've seen a "bad magic" message. Belkin supply one driver which works on 32 bit and 64 bit so I'm not sure how I'll be able to get past the "bag magic" bit. Also, there is no wlan0 or any wireless connection available on my system.

To access the internet on Ubuntu I have an ethernet cable running from my desktop to a wireless laptop and the laptop is sharing it's wireless connection with Ubuntu.

Any ideas? Sorry about the long post.

1 ) Machine Brand and Model (PC/Laptop):
```
Compaq SR5139UK Desktop PC
```

2 ) Wireless Brand, Model and Wireless Chipset:
```
lspci -nn brings up a lot of stuff, the one which i am interested in is this one, my Belkin N1 Wireless Card
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88W8361 [TopDog] 802.11n Wireless (rev 03)

$ lspci -nn | grep 'Wireless Brand' doesn't show up anything

```

3 ) check interface:
```
ifconfig brings up eth0, lo, vmnet1, vmnet8 but no wlan0.

iwconfig brings up:
lo        no wireless extensions.

eth0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

iwconfig wlan0 brings up:
wlan0     No such device

```

4 ) Check for modules:
```

lsmod brings up:
lsmod
Module                  Size  Used by
cryptd                  8008  0 
aes_x86_64              8992  4 
aes_generic            28480  1 aes_x86_64
twofish                 6560  4 
twofish_common         15200  1 twofish
serpent                19104  4 
xts                     3776  6 
gf128mul                9632  1 xts
dm_crypt               14888  6 
binfmt_misc            10220  1 
vmnet                  49404  13 
ppdev                   8232  0 
parport_pc             37352  0 
vmblock                15240  1 
vsock                  46464  0 
vmci                   61704  1 vsock
vmmon                  84620  0 
iptable_filter          3872  0 
ip_tables              21200  1 iptable_filter
psmouse                57124  0 
serio_raw               6596  0 
joydev                 13088  0 
lp                     11908  0 
parport                40528  3 ppdev,parport_pc,lp
snd_hda_codec_realtek   277860  1 
snd_hda_intel          31880  2 
snd_hda_codec          87584  2 snd_hda_codec_realtek,snd_hda_intel
snd_usb_audio         102976  1 
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_usb_lib            19648  1 snd_usb_audio
snd_pcm                93160  4 snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss
snd_hwdep               9352  2 snd_hda_codec,snd_usb_audio
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               65260  0 
videodev               43360  1 uvcvideo
v4l1_compat            16804  2 uvcvideo,videodev
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
v4l2_compat_ioctl32    13344  1 videodev
snd                    77096  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
x_tables               25832  1 ip_tables
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
ndiswrapper           245248  0 
nvidia              10316904  36 
usbhid                 43968  0 
usb_storage            65952  1 
e1000e                138672  0 
ohci1394               33780  0 
ieee1394              100896  1 ohci1394
intel_agp              32816  0 


lsmod | grep "wlan_module_name" brings up nothing

```

5 ) Kernal Boot Messages:
```
dmesg | grep "wlan_module_name" brings up nothing

```

6 ) Network Configuration
```
lshw -C network
  *-network               
       description: Ethernet interface
       product: 82566DC-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1b:fc:d1:03:f4
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=0.9-2 ip=192.168.0.52 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:25 memory:f9ec0000-f9edffff memory:f9efe000-f9efefff ioport:c000(size=32)
 [B] *-network UNCLAIMED
       description: Ethernet controller
       product: 88W8361 [TopDog] 802.11n Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: memory:f9fe0000-f9feffff memory:f9fd0000-f9fdffff[/B]

```

7 ) Scan for networks
```
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

vmnet1    Interface doesn't support scanning.

vmnet8    Interface doesn't support scanning.

```

8 ) Ubuntu version
```
lsb_release -d
Description:	Ubuntu 9.10

```

9) Kernel Architecture
```
uname -mr
2.6.31-14-generic x86_64

```

10 ) Restarting the network
```
/etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]

```

---

