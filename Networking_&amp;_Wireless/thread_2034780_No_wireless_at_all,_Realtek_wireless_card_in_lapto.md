---
title: "No wireless at all, Realtek wireless card in laptop."
date: 2012-07-29
forum: Networking &amp; Wireless
---

### Post by Marius280t on 2012-07-29
So basically i have no wireless connectivity at all. cant see the router, cant scan, and the wireless doesnt even look like its on. The computer is an ASUS U31j with a Realtek RTL8191SEvA. Ubuntu 12.04. This isnt my first Ubuntu machine, i had a Toshiba with 11xx, that also had wireless problems, so does my desktop with its wireless card. but firstly i would like to get my laptop fixed.


When i try installing the drivers for this card using windows wireless driver (ndiswrapper) i get the following error.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release. FATAL: Module ndiswrapper not found.  Is the ndiswrapper module installed?

Below is some output from terminal. Please ask me for anything else you would like to see.

---

### Post by Marius280t on 2012-07-29
[COLOR=DarkGreen]
[COLOR=Black]marius@ubuntu:~$ sudo iwconfig
[sudo] password for marius: 
lo        no wireless extensions.

eth0      no wireless extensions.[/COLOR] [COLOR=Black]

marius@ubuntu:~$ rfkill list all[/COLOR] [COLOR=Black]
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
marius@ubuntu:~$ lspci00:[/COLOR][/COLOR][COLOR=DarkGreen][COLOR=Black]
[/COLOR][/COLOR][COLOR=DarkGreen][COLOR=Black]0[/COLOR][COLOR=Black]

03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev 10)[/COLOR] [COLOR=Black]
    Subsystem: AzureWave Device 1107
    Physical Slot: 1
    Flags: bus master, fast devsel, latency 0, IRQ 10
    I/O ports at b000 [size=256]
    Memory at d4c00000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: rtl8192se

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)[/COLOR] [COLOR=Black]
    Subsystem: ASUSTeK Computer Inc. U6V/U31J laptop
    Physical Slot: 5
    Flags: bus master, fast devsel, latency 0, IRQ 45
    I/O ports at a000 [size=256]
    Memory at d3804000 (64-bit, prefetchable) [size=4K]
    Memory at d3800000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

[/COLOR][COLOR=Black]

marius@ubuntu:~$ lspci -nn[/COLOR] [COLOR=Black]
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 1
00:01.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express x16 Root Port [8086:0045] (rev 1
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 1
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 06)
00:1d.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 06)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 06)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5  Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 06)
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108 [GeForce GT 415M] [10de:0dee] (rev a1)
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller [10ec:8171] (rev 10)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev  06)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath  Architecture Generic Non-core Registers [8086:2c62] (rev 05)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 05)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 05)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 05)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 05)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 05)
marius@ubuntu:~$ lsmod | grep 819
marius@ubuntu:~$ sudo iwlist wlan0 scan
[sudo] password for marius: 
wlan0     Interface doesn't support scanning.

marius@ubuntu:~$ rfkill list all[/COLOR] [/COLOR][COLOR=Black]
[/COLOR]

---

### Post by chili555 on 2012-07-29
> 03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev 10)
Subsystem: AzureWave Device 1107
Physical Slot: 1
Flags: bus master, fast devsel, latency 0, IRQ 10
I/O ports at b000 [size=256]
Memory at d4c00000 (32-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel modules: [COLOR="Red"]rtl8192se[/COLOR]It looks like you have a driver installed already. Let's check:```
lsmod | grep rtl
dmesg | grep -i rtl
```Thanks.

---

### Post by Marius280t on 2012-07-30
```
marius@ubuntu:~$ lsmod | grep rtl
marius@ubuntu:~$ dmesg | grep -i rtl
[    1.965186] r8169 0000:04:00.0: eth0: RTL8168e/8111e at 0xffffc90000668000, bc:ae:c5:65:c6:11, XID 0c200000 IRQ 45
marius@ubuntu:~$ 
```

---

### Post by NikTh on 2012-07-30
Hi ,
and sorry for intervention , chili555 is one of the best wireless problems treatment :) 
please give the output of 
```
lsmod 
dpkg --get-selections | grep -i ndis
sudo lshw -C network
```maybe results help. 

Thanks

---

### Post by Marius280t on 2012-07-30
> **NikTh said:**
> Hi ,
and sorry for intervention , chili555 is one of the best wireless problems treatment :) 
please give the output of 
```
lsmod 
dpkg --get-selections | grep -i ndis
sudo lshw -C network
```maybe results help. 

Thanks

```
marius@ubuntu:~$ lsmod 
Module                  Size  Used by
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61512  1 vfat
usb_storage            49198  0 
uas                    18180  0 
rfcomm                 46621  0 
bnep                   18139  2 
parport_pc             32866  0 
ppdev                  17113  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
b43                   365653  0 
mac80211              514621  1 b43
cfg80211              209821  2 b43,mac80211
bcma                   30720  1 b43
ssb                    61596  1 b43
joydev                 17693  0 
pcmcia                 49310  2 b43,ssb
pcmcia_core            22614  1 pcmcia
snd_hda_codec_realtek   223962  1 
ath_pci               202589  0 
btusb                  18295  1 
wlan                  252939  1 ath_pci
bluetooth             185573  13 rfcomm,bnep,btusb
ath_hal               430739  1 ath_pci
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
nouveau               774641  0 
ttm                    76949  1 nouveau
mxm_wmi                12979  1 nouveau
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    19256  1 mxm_wmi
asus_laptop            24493  0 
sparse_keymap          13890  1 asus_laptop
input_polldev          13896  1 asus_laptop
psmouse                87692  0 
soundcore              15091  1 snd
mac_hid                13253  0 
i915                  472897  8 
drm_kms_helper         46978  2 nouveau,i915
drm                   242038  6 nouveau,ttm,i915,drm_kms_helper
intel_ips              18089  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
i2c_algo_bit           13423  2 nouveau,i915
v4l2_compat_ioctl32    17128  1 videodev
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
serio_raw              13211  0 
video                  19596  2 nouveau,i915
mei                    41616  0 
r8169                  62099  0 
marius@ubuntu:~$ dpkg --get-selections | grep -i ndis
ndisgtk                        install
ndiswrapper-common                install
ndiswrapper-utils-1.9                install
marius@ubuntu:~$ sudo lshw -C network
[sudo] password for marius: 
  *-network UNCLAIMED     
       description: Network controller
       product: RTL8191SEvA Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:b000(size=256) memory:d4c00000-d4c03fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 06
       serial: bc:ae:c5:65:c6:11
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.1.7 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:45 ioport:a000(size=256) memory:d3804000-d3804fff memory:d3800000-d3803fff


```Yes, ive seen how many people he has helped through wireless issues, its great to have support like that for an open source product.

I might take some time to reply to each post. Im GMT+12.

---

### Post by chili555 on 2012-07-30
Holy wireless drivers, Batman!! You have a whole pile of drivers there!> b43                   365653  0 
mac80211              514621  1 b43
cfg80211              209821  2 b43,mac80211
bcma                   30720  1 b43
ssb                    61596  1 b43
pcmcia                 49310  2 b43,ssb
pcmcia_core            22614  1 pcmcia
snd_hda_codec_realtek   223962  1 
ath_pci               202589  0 
wlan                  252939  1 ath_pci
ath_hal               430739  1 ath_pciYikes!

Do you have a PCMCIA wireless device? A USB wireless device? May we see:```
cat /etc/modules
cat /etc/modprobe.d/blacklist
lsusb
lspcmcia
```Thanks...I think.

---

### Post by BkkBonanza on 2012-07-30
Please see this thread,

[http://ubuntuforums.org/showthread.php?t=1834478](http://ubuntuforums.org/showthread.php?t=1834478)

Same wifi dongle, not ndiswrapper, and he gets correct driver to work.

---

### Post by Marius280t on 2012-07-30
> **chili555 said:**
> Holy wireless drivers, Batman!! You have a whole pile of drivers there!Yikes!

Do you have a PCMCIA wireless device? A USB wireless device? May we see:```
cat /etc/modules
cat /etc/modprobe.d/blacklist                     [[More]("http://ubuntuforums.org/newreply.php?do=newreply&p=12140821#")]
lsusb
lspcmcia
```Thanks...I think.

No i dont have a wireless dongle.
Not sure how all those got there. 

```
marius@ubuntu:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ath_pci
b43
marius@ubuntu:~$ cat /etc/modprobe.d/blacklist

#Remove To Install MadWIFI Drivers
blacklist ath9k
blacklist ath5k
marius@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04f2:b1b9 Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 0b05:1788 ASUSTek Computer, Inc. 
marius@ubuntu:~$ lspcmcia

```

---

### Post by Marius280t on 2012-07-30
> **BkkBonanza said:**
> Please see this thread,

[http://ubuntuforums.org/showthread.php?t=1834478](http://ubuntuforums.org/showthread.php?t=1834478)

Same wifi dongle, not ndiswrapper, and he gets correct driver to work.

I tried that, it didnt work. Im thinking of doing a fresh install of Ubuntu and trying again.

---

### Post by chili555 on 2012-07-31
Please do:```
sudo rm /etc/modprobe.d/blacklist
sudo gedit /etc/modules
```When the text editor opens, remove the highlighted parts:> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

[COLOR="Red"]ath_pci
b43[/COLOR]Proofread, save and close gedit. Reboot and show us:```
lsmod | grep rtl
dmesg | grep rtl
cat /etc/modprobe.d/blacklist.conf | tail -n5
```We can fix this!

---

### Post by Marius280t on 2012-07-31
```

marius@ubuntu:~$ lsmod | grep rtl
marius@ubuntu:~$ dmesg | grep rtl
marius@ubuntu:~$ cat /etc/modprobe.d/blacklist.conf | tail -n5
# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```

---

### Post by chili555 on 2012-07-31
So far, so good. Let's see if we get an error or other warning when we load rtl8192se:```
sudo modprobe rtl8192se
rfkill list all
```Thanks.

---

### Post by Marius280t on 2012-07-31
> **chili555 said:**
> So far, so good. Let's see if we get an error or other warning when we load rtl8192se:```
sudo modprobe rtl8192se
rfkill list all
```Thanks.

```
marius@ubuntu:~$ sudo modprobe rtl8192se
marius@ubuntu:~$ rfkill list all
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

OMG you fixed it! What a legend. The wireless just started working. Im taking my laptop to class and if i can get it working on the University Internet ill sign this off as Solved when i get home. Thank you so much for your help, its really appreciated. :D

---

### Post by chili555 on 2012-07-31
Let's try to make sure it stays fixed:```
sudo su
echo rtl8192se >> /etc/modules
exit
```If all goes well, please use thread tools at the top to mark Solved.

---

