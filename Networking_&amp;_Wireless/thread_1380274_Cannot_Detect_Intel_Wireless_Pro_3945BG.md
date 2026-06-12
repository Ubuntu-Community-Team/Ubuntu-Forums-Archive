---
title: "Cannot Detect Intel Wireless Pro 3945BG"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by nomad05 on 2010-01-13
Ok, so as a gift to a friend I picked up a Hasee MJ125 Netbook while I was in China last week. It's a crappy Chinese brand, but it seems to do the job.
 
It didn't come with a wireless adapter so I manually installed an Intel Pro 3945BG card. Despite not being familiar with linux operating systems in general, I picked Ubuntu Netbook Remix for the OS for my friend's preferences.

The problem is that Ubuntu cannot recognize the card or even detect that is there. It's firmly plugged in correctly, but beyond that I'm stumped. I've spent considerable time researching the 3945BG's history with linux, and I've noted several unofficial driver projects (ipw3945) which have later been morphed into other broader projects (iwlwifi).

Not knowing much about command lines, my overall apparent conclusion is that the most recent build of Ubuntu that I have (9.10) has drivers integrated. I've tried using 3rd party network programs (Wicd) to remedy the problem but still cannot be detected.

I'm at a loss. Ubuntu and Linux in general isn't a world I'm intimately familar with. If anyone has any advice or suggestions on where to proceed from here, I'd greatly appreciate it.

Thanks,
Chris

Detailed information:

1.Computer Brand 
Hashee MJ125 Netbook

2. Wireless Brand/Model

Intel Wireless Pro 3945BG (self install)
```
lspci -nn | grep 'Intel'
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
```

3. Check Interface

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:0d:be:a7:10  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:dff:febe:a710/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2633 errors:3 dropped:4 overruns:3 frame:0
          TX packets:2401 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3125018 (3.1 MB)  TX bytes:343309 (343.3 KB)
          Interrupt:17 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```4. Check Modules

```
 $ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10240  0 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
iptable_filter          3100  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                56500  0 
serio_raw               5280  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
usb_storage            52576  0 
i915                  221320  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
8139too                22620  0 
8139cp                 19260  0 
mii                     5212  2 8139too,8139cp
video                  19380  1 i915
output                  2780  1 video
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp

```6. Network Configuration

```
$ sudo lshw -C network
[sudo] password for nomad: 
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth0
       version: 10
       serial: 00:03:0d:be:a7:10
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.107 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:17 ioport:ec00(size=256) memory:febffc00-febffcff

```7. Scan for Networks

```
 iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```8. Ubuntu Version

```
$ lsb_release -d
Description:    Ubuntu 9.10

```9. Kernel/architecture

```
$ uname -mr
2.6.31-17-generic i686

```10. Restart Network

```
sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...     
```

---

### Post by chili555 on 2010-01-13
If neither *lspci* nor *lshw* see any sign of the network adapter, there is not much we can do. Even a card with no driver will show up, albeit 'UNCLAIMED,' that is, unclaimed by any driver.

I suggest you recheck your card installation. Make sure everything is nice and snug and properly seated. Next, I suggest searching all over the laptop for any kind of hardware switch that has been nudged to 'Off.'

Finally, I suggest researching whether there is a setting in the BIOS to enable/disable the wireless card.

I doubt that Hasee has any kind of whitelist for wireless cards, but it's worth Googling.

The Intel 3945ABG is very well supported out of the box in Ubuntu.

---

### Post by Leppie on 2010-01-13
it looks like the kernel module isn't loaded:
```
sudo modprobe iwl3945
```

---

