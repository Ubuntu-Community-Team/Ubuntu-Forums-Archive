---
title: "Broadcom Corporation Device 4727 rev02/Ubuntu 10.04 LTS/Acer Aspire One D257-1497"
date: 2013-03-12
forum: Networking &amp; Wireless
---

### Post by socialconquest on 2013-03-12
Hey folks,

I've been plowing through the forums and trying to get this fixed for hours now. I'm Ubuntu newb style with a fresh install, testing it out on this netbook to potentially expand into my collection of comps for dev. Anyways, I have a wired connection to the internetweb but I can't seem to get the wireless to see anything out there. I installed the driver through the hardware drivers system to no avail. I also went through the hard way and got the direct install through ndiswrapper (bcmwl6.inf) from (WLAN_Broadcom_5.100.235.19_W7x86). No bones. Here are the stats, plz help!:

lspci: 
[TABLE="class: outer_border, width: 500"]
[TR]
[TD]00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
02:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
03:00.0 Class ff00: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)

[/TD]
[/TR]
[/TABLE]

lsusb
[TABLE="class: outer_border, width: 500"]
[TR]
[TD]chris@chris-tinycomp:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b209 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[/TD]
[/TR]
[/TABLE]

lspci
[TABLE="class: outer_border, width: 500"]
[TR]
[TD]chris@chris-tinycomp:~$ lspci -nn | grep 'Broadcom Corporation'
02:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)
[/TD]
[/TR]
[/TABLE]

ifconfig
[TABLE="class: outer_border, width: 500"]
[TR]
[TD]chris@chris-tinycomp:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr e8:9a:8f:ea:fe:3a  
          inet addr:192.168.2.16  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::ea9a:8fff:feea:fe3a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:99038 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82629 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:134008243 (134.0 MB)  TX bytes:6607452 (6.6 MB)
          Interrupt:27 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr e4:d5:3d:9f:01:0a  
          inet6 addr: fe80::e6d5:3dff:fe9f:10a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

[/TD]
[/TR]
[/TABLE]

iwconfig
[TABLE="class: outer_border, width: 500"]
[TR]
[TD]chris@chris-tinycomp:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

[/TD]
[/TR]
[/TABLE]

lsmod
[TABLE="class: outer_border, width: 500"]
[TR]
[TD]chris@chris-tinycomp:~$ lsmod
Module                  Size  Used by
lib80211_crypt_tkip     8676  0 
wl                   1964968  0 
lib80211                6151  2 lib80211_crypt_tkip,wl
binfmt_misc             7992  1 
ppdev                   6375  0 
snd_hda_codec_realtek   279104  1 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
snd_hda_intel          25805  2 
snd_hda_codec          85791  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23681  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  327365  3 
drm_kms_helper         30742  1 i915
snd                    71283  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               62915  0 
led_class               3764  0 
drm                   200480  4 i915,drm_kms_helper
videodev               40614  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
i2c_algo_bit            6024  1 i915
video                  20623  1 i915
lp                      9336  0 
soundcore               8052  1 snd
psmouse                65040  0 
serio_raw               4918  0 
intel_agp              29319  2 i915
ndiswrapper           244832  0 
output                  2503  1 video
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
parport                37160  2 ppdev,lp
ahci                   38350  2 
r8169                  39714  0 
mii                     5237  1 r8169

[/TD]
[/TR]
[/TABLE]

sudo lshw -c network
[TABLE="class: outer_border, width: 500"]
[TR]
[TD]chris@chris-tinycomp:~$ sudo lshw -c network
[sudo] password for chris: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: e8:9a:8f:ea:fe:3a
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.2.16 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:3000(size=256) memory:50004000-50004fff(prefetchable) memory:50000000-50003fff(prefetchable)
  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: e4:d5:3d:9f:01:0a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl1 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:54000000-54003fff

[/TD]
[/TR]
[/TABLE]

iwlist scan
[TABLE="class: outer_border, width: 500"]
[TR]
[TD]chris@chris-tinycomp:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

[/TD]
[/TR]
[/TABLE]

uname -mr
[TABLE="class: outer_border, width: 500"]
[TR]
[TD]chris@chris-tinycomp:~$ uname -mr
2.6.32-45-generic x86_64

[/TD]
[/TR]
[/TABLE]

And now you know more about my system than I do. Any help would be greatly appreciated.

---

### Post by Hadaka on 2013-03-12
Hi please do..

*Note do all commands even if there is an error
untill all commands are entered..

```
sudo modprobe -rfv ndiswrapper 
sudo apt-get remove --purge ndisgtk ndiswrapper*
sudo rm /etc/modprobe.d/ndis*
sudo rm -r /etc/ndiswrapper/*
``` 
then do..
```
sudo apt-get install linux-headers-generic
 sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```
report results please.
thanks.

---

### Post by chili555 on 2013-03-12
The first thing I'd suggest is to remove ndiswrapper. It is a conflict with wl:```
sudo apt-get remove --purge ndiswrapper*
sudo modprobe -r ndiswrapper
```Next, I'd reboot with the ethernet detached and see if it scans now:```
sudo iwlist eth1 scan
```If not, I'd look for errors:```
dmesg | grep -e wl -e eth1
```

---

### Post by socialconquest on 2013-03-12
Rock and roll, thanks for the quick reply. It doesn't look like it worked. Here are the results:
[TABLE="class: outer_border, width: 500"]
[TR]
[TD]chris@chris-tinycomp:~$ sudo iwlist eth1 scan
[sudo] password for chris: 
eth1      Failed to read scan data : Invalid argument

chris@chris-tinycomp:~$ dmesg | grep -e wl -e eth1
[   14.760127] wl: module license 'MIXED/Proprietary' taints kernel.
[   14.782914] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.782935] wl 0000:02:00.0: setting latency timer to 64
[   14.992006] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.60.48.36 
[   26.043829] eth1: no IPv6 routers present
chris@chris-tinycomp:~$ 

[/TD]
[/TR]
[/TABLE]

---

### Post by chili555 on 2013-03-12
Nothing alarming here, except it doesn't actually start and run! Let's dig deeper:```
rfkill list all
cat /var/log/syslog | grep eth1 | tail -n20
```

---

### Post by socialconquest on 2013-03-12
That first bit of code all accepted, effectively removing ndiswrapper and ndisgtk. Headers command came back already updated and kernel source succesfully reinstalled. The last command gave no return. Here is the log (second time around, I repeated to be sure):
[TABLE="class: outer_border, width: 500"]
[TR]
[TD]chris@chris-tinycomp:~$ sudo modprobe -rfv ndiswrapper
chris@chris-tinycomp:~$ sudo apt-get remove --purge ndisgtk ndiswrapper*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ndisgtk is not installed, so not removed
Note, selecting ndiswrapper-modules-1.9 for regex 'ndiswrapper*'
Note, selecting ndiswrapper-utils for regex 'ndiswrapper*'
Note, selecting ndiswrapper-common for regex 'ndiswrapper*'
Note, selecting ndiswrapper-source for regex 'ndiswrapper*'
Note, selecting ndiswrapper-utils-1.9 for regex 'ndiswrapper*'
E: Couldn't find package ndiswrapper*
chris@chris-tinycomp:~$ sudo rm /etc/modprobe.d/ndis*
rm: cannot remove `/etc/modprobe.d/ndis*': No such file or directory
chris@chris-tinycomp:~$ sudo rm -r /etc/ndiswrapper/*
rm: cannot remove `/etc/ndiswrapper/*': No such file or directory
chris@chris-tinycomp:~$ sudo apt-get install linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
chris@chris-tinycomp:~$ ^C
chris@chris-tinycomp:~$ clear

chris@chris-tinycomp:~$ sudo apt-get install linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
chris@chris-tinycomp:~$ sudo apt-get install --reinstall bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/896kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 160585 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.60.48.36+bdcom-0ubuntu3 (using .../bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
Building only for 2.6.32-45-generic
Building for architecture x86_64
Building initial module for 2.6.32-45-generic
Done.

wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.32-45-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-45-generic
chris@chris-tinycomp:~$ sudo modprobe wl
chris@chris-tinycomp:~$ 

[/TD]
[/TR]
[/TABLE]

---

### Post by socialconquest on 2013-03-12
Here is the response on that one:
[TABLE="class: outer_border, width: 500"]
[TR]
[TD]chris@chris-tinycomp:~$ rfkill list all
chris@chris-tinycomp:~$ cat /var/log/syslog | grep eth1 | tail -n20
Mar 12 14:24:12 chris-tinycomp avahi-daemon[749]: Registering new address record for fe80::e6d5:3dff:fe9f:10a on eth1.*.
Mar 12 14:24:12 chris-tinycomp NetworkManager: <info>  (eth1): supplicant interface state:  starting -> ready
Mar 12 14:24:12 chris-tinycomp NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 42)
Mar 12 14:24:21 chris-tinycomp kernel: [ 5548.103792] eth1: no IPv6 routers present
Mar 12 15:39:17 chris-tinycomp kernel: [   14.992006] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.60.48.36 
Mar 12 15:39:17 chris-tinycomp NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/eth1, iface: eth1)
Mar 12 15:39:17 chris-tinycomp NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Mar 12 15:39:17 chris-tinycomp NetworkManager: <info>  (eth1): driver supports SSID scans (scan_capa 0x01).
Mar 12 15:39:17 chris-tinycomp NetworkManager: <info>  (eth1): new 802.11 WiFi device (driver: 'wl')
Mar 12 15:39:17 chris-tinycomp NetworkManager: <info>  (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
Mar 12 15:39:17 chris-tinycomp NetworkManager: <info>  (eth1): now managed
Mar 12 15:39:17 chris-tinycomp NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
Mar 12 15:39:17 chris-tinycomp NetworkManager: <info>  (eth1): bringing up device.
Mar 12 15:39:17 chris-tinycomp NetworkManager: <info>  (eth1): preparing device.
Mar 12 15:39:17 chris-tinycomp NetworkManager: <info>  (eth1): deactivating device (reason: 2).
Mar 12 15:39:17 chris-tinycomp NetworkManager: <info>  (eth1): supplicant manager state:  down -> idle
Mar 12 15:39:17 chris-tinycomp NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 0)
Mar 12 15:39:17 chris-tinycomp NetworkManager: <info>  (eth1): supplicant interface state:  starting -> ready
Mar 12 15:39:18 chris-tinycomp avahi-daemon[744]: Registering new address record for fe80::e6d5:3dff:fe9f:10a on eth1.*.
Mar 12 15:39:27 chris-tinycomp kernel: [   26.043829] eth1: no IPv6 routers present

[/TD]
[/TR]
[/TABLE]

---

### Post by chili555 on 2013-03-12
Please do:```
sudo modprobe -r wl && sudo modprobe wl
sudo iwlist eth1 scan
```Is there a functioning wireless button or switch on your Acer? In 10.04, the module *acer-wmi* is often troublesome, however, I don't see it loaded and I'm puzzled by:> chris@chris-tinycomp:~$ rfkill list all
[email]chris@chris-tinycomp:~$...that[/email] is to say, I have nothing to report; no good news, no bad news, no nothing.

---

