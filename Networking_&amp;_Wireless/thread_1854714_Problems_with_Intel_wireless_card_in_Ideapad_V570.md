---
title: "Problems with Intel wireless card in Ideapad V570"
date: 2011-10-04
forum: Networking &amp; Wireless
---

### Post by Calluella on 2011-10-04
Hello,

Longtime Ubuntu user here who's spent a good few years figuring out how to keep my system running via google and other people's forum posts, finally stumped.

I recently purchased a Lenovo Ideapad V570; in the main, I love it, but I installed Lucid almost as soon as I got it home and haven't been able to get the system to acknowledge its wireless card since.  It basically acts as though the toggle switch on the side of the laptop that enables/disables the wireless card is turned off.  (It isn't.)

The card is an Intel Centrino Wireless-N + WiMAX 6150.  Apparently the iwlwifi drivers I need to make it run are notoriously problematic, but I haven't worked out exactly what I need to be running or installing to make them work.

lspci gets you:
```
00:00.0 Host bridge: Intel Corporation Device 0104 (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b5)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Device 1c49 (rev 05)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
02:00.0 Network controller: Intel Corporation Device 0886 (rev 67)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

```

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr f0:de:f1:5c:9f:9f  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f2de:f1ff:fe5c:9f9f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10591 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7936 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9364164 (9.3 MB)  TX bytes:1227521 (1.2 MB)
          Interrupt:28 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

```

I'm not altogether sure which of these, if any, is supposed to be my wireless module; I suspect this may be the problem.

```
lsmod
[INDENT]Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203408  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  35102  71 
tileblit                1999  1 fbcon
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
font                    7557  1 fbcon
video                  17375  0 
soundcore               6620  1 snd
bitblit                 4707  1 fbcon
uvcvideo               57406  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
softcursor              1189  1 bitblit
videodev               34425  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
psmouse                63677  0 
vga16fb                11385  1 
output                  1871  1 video
vgastate                8961  1 vga16fb
serio_raw               3978  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
r8169                  34140  0 
mii                     4381  1 r8169
ahci                   32360  2 
[/INDENT]
```


Network configuration
```

sudo lshw -C network
[INDENT]  *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 67
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d0500000-d0501fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: f0:de:f1:5c:9f:9f
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.68 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:28 ioport:2000(size=256) memory:d0404000-d0404fff(prefetchable) memory:d0400000-d0403fff(prefetchable)
[/INDENT]
```

Scanning for networks only gets me:
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

Ubuntu release is 10.04.3 LTS, kernel is 2.6.32-34-generic i686


Hopefully there's enough here; I'm afraid I've been staring through forum posts for so long that I don't know up from down on this one any more.  I'd really like to find a way to get my wireless card working.  Thanks!

---

### Post by eracho on 2011-10-14
I have the same problem on a samsung np-n100 netbook.

I hope someone post a solution

---

### Post by nema.arpit on 2012-01-15
Hey, my friend had the same problem in his lenovo v570. I updated the kernel to 3.0.0.14-generic ([http://www.ubuntuupdates.org/ppas/37](http://www.ubuntuupdates.org/ppas/37) , install linux-image-* and linux-headers-*), and upon reboot into the new kernel, the card was detected.
After that, there is one more thing to do : remove the acer_wmi module :
[http://ubuntuforums.org/showthread.php?t=1856155&highlight=wireless+driver+lenovo+v570](http://ubuntuforums.org/showthread.php?t=1856155&highlight=wireless+driver+lenovo+v570)

---

