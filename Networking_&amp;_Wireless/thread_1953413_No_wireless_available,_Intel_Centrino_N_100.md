---
title: "No wireless available, Intel Centrino N 100"
date: 2012-04-06
forum: Networking &amp; Wireless
---

### Post by Tanvile on 2012-04-06
Samsung n100 notebook
IntelCentrino N 100  // (08ae)

```
barboruzeles@barboruzeles-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation Device 08ae
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
barboruzeles@barboruzeles-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 2232:1006  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```______________________________

```
barboruzeles@barboruzeles-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr e8:11:32:7c:ed:9f  
          inet addr:192.168.1.71  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ea11:32ff:fe7c:ed9f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:299850 errors:0 dropped:0 overruns:0 frame:0
          TX packets:163026 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:444951321 (444.9 MB)  TX bytes:12194983 (12.1 MB)
          Interrupt:28 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11454 (11.4 KB)  TX bytes:11454 (11.4 KB)

barboruzeles@barboruzeles-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```_________________________

```
barboruzeles@barboruzeles-laptop:~$ lsmod
Module                  Size  Used by
iwlagn                106911  0 
iwlcore               106149  1 iwlagn
mac80211              205434  2 iwlagn,iwlcore
led_class               2864  1 iwlcore
cfg80211              126528  3 iwlagn,iwlcore,mac80211
easy_slow_down_manager     4081  0 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203472  1 
snd_hda_intel          22069  2 
snd_hda_codec          74297  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
snd_seq_midi            4557  0 
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_rawmidi            19056  1 snd_seq_midi
vga16fb                11385  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
vgastate                8961  1 vga16fb
snd_seq                47263  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
joydev                  8740  0 
i915                  289683  3 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         29329  1 i915
drm                   163779  4 i915,drm_kms_helper
snd                    54244  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            5028  1 i915
uvcvideo               57438  0 
psmouse                63677  0 
samsung_backlight       2917  0 
lp                      7028  0 
video                  17375  1 i915
soundcore               6620  1 snd
intel_agp              24375  2 i915
videodev               34457  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
serio_raw               3978  0 
output                  1871  1 video
agpgart                31724  2 drm,intel_agp
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
parport                32635  2 ppdev,lp
ahci                   32680  2 
r8169                  34140  0 
mii                     4381  1 r8169

```__________________________

```
barboruzeles@barboruzeles-laptop:~$ dmesg | grep iwl
[ 2781.984312] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[ 2781.984328] iwlagn: Copyright(c) 2003-2009 Intel Corporation

```_____________________________

```
barboruzeles@barboruzeles-laptop:~$ sudo lshw -C network
[sudo] password for barboruzeles: 
  *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0100000-f0101fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 05
       serial: e8:11:32:7c:ed:9f
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.71 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:28 ioport:2000(size=256) memory:f050c000-f050cfff(prefetchable) memory:f0508000-f050bfff(prefetchable)

```________________________
```
barboruzeles@barboruzeles-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


```___________________________

```
barboruzeles@barboruzeles-laptop:~$ lsb_release -d
Description:    Ubuntu 10.04.4 LTS
barboruzeles@barboruzeles-laptop:~$ uname -mr
2.6.32-40-generic i686

```___________________________

```
barboruzeles@barboruzeles-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 1656
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/e8:11:32:7c:ed:9f
Sending on   LPF/eth0/e8:11:32:7c:ed:9f
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/e8:11:32:7c:ed:9f
Sending on   LPF/eth0/e8:11:32:7c:ed:9f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.1.71 from 192.168.1.254
DHCPREQUEST of 192.168.1.71 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.71 from 192.168.1.254
bound to 192.168.1.71 -- renewal in 1772 seconds.
                                                                         [ OK ]

```I didn't mess it up! (hands up) It didn't connect from the start, i.e., after being installed. I think this has something to do with kernel, isn't it? Or so [they have written]("http://intellinuxwireless.org/").
I'm so at loss that I have downloaded ubuntu 11 and now am running to buy a bigger flash (don't laugh, thank you) to burn a live usb. 

Yet, I would like to know is it - installing ubuntu 11 - the only way? Copying all my docs and pics and stuff in Lucid to a new distro................ 

Meego 1.2 works like magic on this notebook, yet ubuntu somehow does not... MOreover, MEego uses iwlwifi (driver? module? which is it?), whereas modprobe iwlwifi in Lucid finds nothing.

Help? :) Any... help? T.T

---

### Post by 2F4U on 2012-04-06
It seems as if you asked the same question couple of month ago:

[http://ubuntuforums.org/showthread.php?t=1880270&page=2](http://ubuntuforums.org/showthread.php?t=1880270&page=2)

You got some suggestions but didn't follow up. What happened?

---

### Post by Tanvile on 2012-04-06
Well, I did repeat the sequences for n-teen times, but it didn't work and I gave up - used Meego instead :(

Yet, I got frustrated with Meego.

I'll enter the given code again and print out response in previous thread. Should I include the first post of this thread as well?

:)

---

### Post by Tanvile on 2012-04-06
> **Tanvile said:**
> Well, I did repeat the sequences for n-teen times, but it didn't work and I gave up - used Meego instead :(

Yet, I got frustrated with Meego.

I'll enter the given code again and print out response in previous thread. Should I include the first post of this thread as well?

:)
Thread is solved. To those of you who come across this thread, please refer to [this thread]("http://ubuntuforums.org/showthread.php?p=11822990#post11822990").

---

