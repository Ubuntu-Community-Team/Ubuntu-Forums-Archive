---
title: "Wireless not working-Dell Inspiron 1545"
date: 2010-02-22
forum: Networking &amp; Wireless
---

### Post by Lobo89 on 2010-02-22
Please help, I don't know much about linux.

I'm running Ubuntu 9.10, Dell Inspiron 1545. 

I have the NDISwrapper installed, and the driver shows up in "Hardware Drivers" as activated (Broadcom STA wireless driver) it also shows up in "Windows Wireless Drivers" (bcmwl6) but it still won't allow me to connect wirelessly.

If you let me know what commands I need to run to give you all the info, I'd be happy to do it.

Thanks.

---

### Post by northd_tech on 2010-02-22
It would help if you can post the results of these terminal commands:

```
lspci 

lsmod

lsusb

cat /etc/modules

cat /etc/modules.conf

sudo lshw -C network

ifconfig

iwconfig

nm-tool
```

---

### Post by wojox on 2010-02-22
Have you tried installing:

```
sudo apt-get update && sudo apt-get install bcmwl-kernel-source
```

---

### Post by Megaptera on 2010-02-22
This is what I did on my Dell Inspiron 1545. It's what wojox suggested but with screenshots and using Synaptic instead if that helps?. Iknow it says Dell 'Mini' but ignore that!

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

Hope this helps?
Richard

---

### Post by Lobo89 on 2010-02-23
> **northd_tech said:**
> It would help if you can post the results of these terminal commands:

```
lspci 

lsmod

lsusb

cat /etc/modules

cat /etc/modules.conf

sudo lshw -C network

ifconfig

iwconfig

nm-tool
```

aaron@aaron-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
aaron@aaron-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10240  0 
snd_hda_codec_idt      59844  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
iptable_filter          3100  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
v4l1_compat            14496  2 uvcvideo,videodev
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ndiswrapper           185532  0 
dell_wmi                2564  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
dell_laptop             8128  0 
dcdbas                  7292  1 dell_laptop
psmouse                56500  0 
serio_raw               5280  0 
snd                    59204  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  221320  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
usb_storage            52576  0 
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
sky2                   46528  0 
video                  19380  1 i915
output                  2780  1 video
aaron@aaron-laptop:~$ lsusb
Bus 001 Device 003: ID 0c45:63ee Microdia 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
aaron@aaron-laptop:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
aaron@aaron-laptop:~$ cat /etc/modules.conf
cat: /etc/modules.conf: No such file or directory
aaron@aaron-laptop:~$ sudo lshw -C network
[sudo] password for aaron: 
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:50:52:3f
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=192.168.1.4 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:f68fc000-f68fffff ioport:de00(size=256)
aaron@aaron-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:64:50:52:3f  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:64ff:fe50:523f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:888 errors:0 dropped:0 overruns:0 frame:0
          TX packets:785 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:981381 (981.3 KB)  TX bytes:99824 (99.8 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

aaron@aaron-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

aaron@aaron-laptop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        00:25:64:50:52:3F

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

---

### Post by Lobo89 on 2010-02-23
> **wojox said:**
> Have you tried installing:

```
sudo apt-get update && sudo apt-get install bcmwl-kernel-source
```


aaron@aaron-laptop:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release [44.1kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release    
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release [44.1kB]         
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages [67.4kB]        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages [174kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages [14B] 
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources [21.0kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources [14B]      
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages [32.4kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources [6,767B]    
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages [1,666B] 
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources [577B]    
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages [14B]   
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources [52.8kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources [14B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages [103kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources [26.3kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages [6,930B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources [3,820B]
Fetched 586kB in 2s (265kB/s)                         
Reading package lists... Done
aaron@aaron-laptop:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by erucalea on 2010-06-27
Hello,

I have the same problem but it seems I couldnt find the bcmwl-kernel-source package.
Any suggestion?

esteban@esteban-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
esteban@esteban-laptop:~$ lsmod
Module                  Size  Used by
i915                   67844  2 
drm                    96424  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         436148  5 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               63368  0 
snd                    62756  18 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
compat_ioctl32          9344  1 uvcvideo
soundcore              15200  1 snd
joydev                 18368  0 
video                  25872  0 
psmouse                61972  0 
intel_agp              34108  1 
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
output                 11008  1 video
serio_raw              13444  0 
pcspkr                 10496  0 
usbhid                 42336  0 
dcdbas                 15264  0 
agpgart                42696  3 drm,intel_agp
ieee80211_crypt_tkip    16896  0 
wl                   1281364  0 
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl
usb_storage            99648  0 
sky2                   54916  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
esteban@esteban-laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 1bcf:0007 Sunplus Innovation Technology Inc. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:63ee Microdia 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

## thanks

---

### Post by mikewhatever on 2010-06-27
erucalea, according to the output you posted, the module for your wireless is loaded and everything should be working muy bueno.

---

### Post by erucalea on 2010-06-27
Yeah, but I am not detecting any wireless signal, and I try to install the package and this is the output

esteban@esteban-laptop:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bcmwl-kernel-source

:S

---

### Post by mikewhatever on 2010-06-27
You probably get the 'Couldn't find package' message because you aren't connected to the internet. If that's not the case, run **sudo apt-get update** and then try again. The following command will show if bcmwl-kernel-source is installed or not:
```
dpkg -l | grep bcmwl-kernel-source
```

To troubleshoot the wireless problem, post the outputs of the following:
ifconfig
sudo lshw -C network

---

### Post by erucalea on 2010-06-27
Still nothing, I dont even detect wireless conections, 

esteban@esteban-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:ae:3e:19:6b  
          inet addr:10.92.101.254  Bcast:10.92.111.255  Mask:255.255.240.0
          inet6 addr: fe80::223:aeff:fe3e:196b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2660 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2846 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1939578 (1.9 MB)  TX bytes:548852 (548.8 KB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:22:5f:b2:0f:f0  
          inet6 addr: fe80::222:5fff:feb2:ff0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3280 (3.2 KB)  TX bytes:3280 (3.2 KB)

esteban@esteban-laptop:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:22:5f:b2:0f:f0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:3e:19:6b
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=10.92.101.254 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 1a:1d:ec:f7:b8:e5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
esteban@esteban-laptop:~$

---

### Post by mikewhatever on 2010-06-27
```
sudo apt-get update
sudo apt-get install --reinstall bmcwl-kernel-source
```

and post the outputs of the above.

The module is definitely loaded:
```
configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes
```
Make sure the wireless is turned on.

---

### Post by erucalea on 2010-06-28
esteban@esteban-laptop:~$ sudo apt-get update
[sudo] password for esteban: 
Get:1 [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg [189B]
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US              
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg [189B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg [197B]                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                               
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages                     
Get:4 [http://download.virtualbox.org](http://download.virtualbox.org) jaunty Release.gpg [197B] 
Ign [http://download.virtualbox.org](http://download.virtualbox.org) jaunty/non-free Translation-en_US
Get:5 [http://download.virtualbox.org](http://download.virtualbox.org) jaunty Release [3446B]    
Err [http://download.virtualbox.org](http://download.virtualbox.org) jaunty Release                              
  
Get:6 [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) jaunty Release.gpg [189B]                   
Ign [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Get:7 [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) jaunty-updates Release.gpg [189B]
Ign [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) jaunty Release
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) jaunty-updates Release
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) jaunty/main Packages
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) jaunty/universe Packages
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) jaunty-updates/multiverse Packages
Fetched 1151B in 1s (606B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139

W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/jaunty/Release](http://download.virtualbox.org/virtualbox/debian/dists/jaunty/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
esteban@esteban-laptop:~$ sudo apt-get install --reinstall bmcwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bmcwl-kernel-source
esteban@esteban-laptop:~$ configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes
bash: configuration:: command not found
esteban@esteban-laptop:~$

---

### Post by mikewhatever on 2010-06-28
Right, apparently, Jaunty has a different package, b43-fwcutter. It's been my mistake all along.
Anyways, everything looks ok as far as the driver goes. Is there a button to turn the wireless on/off? The following command might help too:
```
sudo ifconfig eth1 up
```

---

### Post by erucalea on 2010-06-28
OK, it worked!!! thanks a lot!!!!

---

### Post by erucalea on 2010-06-28
I am sorry to keep bothering, but can you explain me what did I just did??

thanks, I am new in Linux and the forums, so I am still kinda lost

---

### Post by mikewhatever on 2010-06-28
> **erucalea said:**
> I am sorry to keep bothering, but can you explain me what did I just did??

thanks, I am new in Linux and the forums, so I am still kinda lost

This is a help and support forum, and you are not bothering at all. :p
This command,
```
sudo ifconfig eth1 up
```
simply brings up the wireless interface, 'eth1' in your case.
The question is, why wasn't it up in the first place.
AS mentioned earlier, some notebooks have a button to turn the wireless on/off. Could it be that yours was off?

---

