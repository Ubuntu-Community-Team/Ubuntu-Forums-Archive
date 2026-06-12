---
title: "Tenda W322P PCI Adapter Problems..."
date: 2010-09-26
forum: Networking &amp; Wireless
---

### Post by kymagic on 2010-09-26
Hello,

I can't get my Tenda W322P PCI Adapter to work under Ubuntu. By "not work", I mean it doesn't even show up under either iwconfig or ifconfig.

I am 99% sure the chipset for my card is Ralink RT2860.

My PC is custom built; The CPU is an AMD Phenom II 940 3GHz Quad core, and the mobo is an Asus M3N78 Pro.

As for various command outputs, see below.

**lsb_release -d**
```
Description:	Ubuntu 10.04.1 LTS
```

**uname -mr**
```
2.6.32-24-generic x86_64

```

**lspci | grep RaLink**
```
01:0b.0 Network controller: RaLink Device 3062
```

**ifconfig**
```
eth0      Link encap:Ethernet  HWaddr 00:24:8c:3e:6d:53  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:29 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6080 (6.0 KB)  TX bytes:6080 (6.0 KB)


```

**iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.
```

**lsmod** (Couldn't find any reference to 'ralink', 'tenda', 'wlan' etc in here, hence the full output.
```
Module                  Size  Used by
nls_iso8859_1           4633  1 
nls_cp437               6351  1 
vfat                   10866  1 
fat                    55350  1 vfat
cryptd                  8116  0 
aes_x86_64              7912  89 
aes_generic            27607  1 aes_x86_64
joydev                 11072  0 
dm_crypt               13043  0 
snd_hda_codec_nvhdmi     4760  1 
snd_hda_codec_realtek   279040  1 
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_usb_audio          92747  1 
snd_usb_lib            19193  1 snd_usb_audio
snd_hda_intel          25677  2 
snd_hda_codec          85759  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  2 snd_usb_audio,snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87882  4 snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               62467  0 
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
snd                    71106  19 snd_hda_codec_realtek,snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                64576  0 
edac_core              45423  0 
edac_mce_amd            9278  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
serio_raw               4918  0 
i2c_nforce2             6099  0 
asus_atk0110           10033  0 
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 41084  0 
hid                    83440  1 usbhid
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
usb_storage            49833  1 
nouveau               515227  2 
ttm                    60847  1 nouveau
drm_kms_helper         30742  1 nouveau
ohci1394               30260  0 
video                  20623  0 
floppy                 63156  0 
output                  2503  1 video
ieee1394               94771  1 ohci1394
drm                   199204  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit            6024  1 nouveau
forcedeth              55592  0 
ahci                   37870  2 
pata_amd               11962  0 
```

**dmesg**
The sticky on this forum said that this should be included. Again, I couldn't find anyhting in there that appeared meaningful, and I wasn't entirely sure what I should be grepping for in the first place.

It's obviously long, so I threw it on Pastebin.

[http://pastebin.com/dz1mpyaQ](http://pastebin.com/dz1mpyaQ)

**sudo lshw -C network**
```
  *-network UNCLAIMED
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: b
       bus info: pci@0000:01:0b.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=4 mingnt=2
       resources: memory:fdee0000-fdeeffff
  *-network
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:24:8c:3e:6d:53
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:29 memory:fe02b000-fe02bfff ioport:f600(size=8) memory:fe02a000-fe02a0ff memory:fe029000-fe02900f
```

**iwlist scan**
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

---

### Post by kymagic on 2010-09-28
Oh, and I have checked that the Power Management option under Windows doesn't switch the device off when the computer shuts down.

---

