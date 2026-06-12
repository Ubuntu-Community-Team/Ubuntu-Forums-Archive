---
title: "Ubuntu Netbook Remix on Dell Mini 10 (NO WIRELESS CONNECTION)"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by msackley on 2010-01-01
Hey all, so I got a Dell Inspiron Mini 10 for Xmas and it orginally came with Windows 7 Starter which sucked, so I decided to installed Ubuntu Netbook Remix tonight and everything seemed to go just fine. I installed it with little issues using the flash drive method.

Now I cannot get a wireless connection to work for the life of me. I'm a total linux noob. I have never used it before in my life. I have been reading and it seems like this is a very common issue but most of this stuff is all kind of confusing I really wish it would be a little more simple. I'm able to get the internet to work when I directly connect it through a wired connection but it will not recognize any wireless connections/networks when I know there are some.

The network that I am trying to connect to is my home router which has no password on it at the moment so for the security issues it shouldn't be difficult to connect to but linux isn't even picking it up in the network manager thing.

If anyone could help me with simple steps and maybe dumb it down as when things get really technical i start to get lost as Ive noticed after reading some other things. 

Any help would be greatly appreciated as I really want to use linux and really enjoy it but this one small issue is going to be a major one if I dont get it fixed. 

Thanks!

---

### Post by msackley on 2010-01-01
Here is an update with the specific information from the terminal below:

1) Machine Brand and Model: Dell Inspiron Mini 10 (originally had windows 7 starter)

2) Wireless Brand, Model and Wireless Chipset:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
matt@msackley:~$ 

```


3) Interface
> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:e8:ed:c6:6d  
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:e8ff:feed:c66d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1755 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2613298 (2.6 MB)  TX bytes:242711 (242.7 KB)
          Interrupt:27 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


>  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

4) Modules:
> lsmod
Module                  Size  Used by
usbhid                 38208  0 
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10272  0 
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
snd_hda_codec_realtek   203328  1 
psmouse                56180  0 
serio_raw               5280  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
dell_wmi                2564  0 
snd_seq_dummy           2656  0 
compal_laptop           3728  0 
snd_seq_oss            28576  0 
b43                   122136  0 
snd_seq_midi            6432  0 
mac80211              181236  1 b43
dcdbas                  7292  0 
usb_storage            52544  0 
snd_rawmidi            22208  1 snd_seq_midi
cfg80211               93052  2 b43,mac80211
led_class               4096  1 b43
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iptable_filter          3100  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
ssb                    35300  1 b43
r8169                  32064  0 
mii                     5212  1 r8169
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video


5) Network Configuration
> password for matt: 
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:24:e8:ed:c6:6d
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.109 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:2000(size=256) memory:f0510000-f0510fff(prefetchable) memory:f0500000-f050ffff(prefetchable) memory:f0520000-f053ffff(prefetchable)


7) Scan for networks
> iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


8) Ubuntu Version
> lsb_release -d
Description:    Ubuntu 9.10


9) Kernel/architecture
> uname -mr
2.6.31-14-generic i686


Restarting the network
> sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                       Ignoring unknown interface eth0=eth0.

---

### Post by focwiz on 2010-01-01
> **msackley said:**
> Hey all, so I got a Dell Inspiron Mini 10 for Xmas and it orginally came with Windows 7 Starter which sucked, so I decided to installed Ubuntu Netbook Remix tonight and everything seemed to go just fine. I installed it with little issues using the flash drive method.

Now I cannot get a wireless connection to work for the life of me. I'm a total linux noob. I have never used it before in my life. I have been reading and it seems like this is a very common issue but most of this stuff is all kind of confusing I really wish it would be a little more simple. I'm able to get the internet to work when I directly connect it through a wired connection but it will not recognize any wireless connections/networks when I know there are some.

The network that I am trying to connect to is my home router which has no password on it at the moment so for the security issues it shouldn't be difficult to connect to but linux isn't even picking it up in the network manager thing.

If anyone could help me with simple steps and maybe dumb it down as when things get really technical i start to get lost as Ive noticed after reading some other things. 

Any help would be greatly appreciated as I really want to use linux and really enjoy it but this one small issue is going to be a major one if I dont get it fixed. 

Thanks!

Ahhh...Broadcom Chipset....see this post..
[http://ubuntuforums.org/showthread.php?t=1368699]("http://ubuntuforums.org/showthread.php?t=1368699")

---

### Post by msackley on 2010-01-01
Just wanted to say THANKS! Its working like a charm now im posting from my now Dell Mini 10 with UNR on it rather than that lame Windows 7 Starter! 

Thanks for the help!

---

### Post by focwiz on 2010-01-01
> **msackley said:**
> Just wanted to say THANKS! Its working like a charm now im posting from my now Dell Mini 10 with UNR on it rather than that lame Windows 7 Starter! 

Thanks for the help!

You are welcome...the geniuses on this site are great aren't they...they have helped me a lot.  Please mark this post "Solved"

---

