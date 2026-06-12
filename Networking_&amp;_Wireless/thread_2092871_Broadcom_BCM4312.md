---
title: "Broadcom BCM4312"
date: 2012-12-09
forum: Networking &amp; Wireless
---

### Post by chriswebs23 on 2012-12-09
Have just installed Ubuntu 12.10 on my old HP Compaq 6720s...

Hoping it would run quicker and simpler than Vista.

At the moment i am regretting the move to ubuntu because i cant connect to my home or work wireless internet connection.

Its just not as simple as vista. I have no experience with ubuntu i just want my work laptop to connect to the internet!

Any help would be great... considering switching back to vista...

---

### Post by chili555 on 2012-12-09
Once you solve the wireless piece, I think Ubuntu will indeed be simpler and faster than Vista. Let's see what kind of wireless card you have. Is it a PCI card built-in? Please open a terminal and run this command and post the result:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

If your wireless device is USB, please post:```
lsusb
```Thanks.

---

### Post by chriswebs23 on 2012-12-09
chris@chris-HP-Compaq-6720s:~$ lspci -nn  grep 0280
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file
chris@chris-HP-Compaq-6720s:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile GME965/GLE960 Memory Controller Hub [8086:2a10] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller [8086:2a12] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller [8086:2a13] (rev 0c)
00:19.0 Ethernet controller [0200]: Intel Corporation 82562GT 10/100 Network Connection [8086:10c4] (rev 03)
00:1a.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03)
00:1d.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] [8086:2829] (rev 03)
10:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
chris@chris-HP-Compaq-6720s:~$ grep 0280

---

### Post by EmmEight on 2012-12-09
Welcome to Ubuntu!

I know this sounds silly, but how comfortable are you with the user interface?
Have you discovered where the network manager icon is? On the top right of the screen? Have you clicked and right-clicked on it?

Please god, don't go back to vista. ):P

---

### Post by westie457 on 2012-12-09
Hi and welcome to the forum.

Plug an ethernet cable in, it is necessary at this stage.

Open a terminal, type in and run these two commands please.```
sudo apt-get install b43fwcutter

sudo apt-get install firmware-b43-lpphy-installer
```

When this has finished wait a few seconds and click the Network Manager icon at the top of the screen. It looks like piece of pie.

Any available networks will appear there, choose yours and enter details as necessary. You should be up and running.

If nothing in network manager run ```
sudo modprobe b43
```and try Network Manager again.

If there is no joy after trying all the above post the output of ```
lsmod
```

Thank you.

---

### Post by chriswebs23 on 2012-12-09
not very used to the interface at all!! i loved XP, and have windows 7 on my home Desktop... I am trying to give this old junk laptop a new life, have always been windows so this is all new to me...

I have a wired connection no problem... have done the whole 192.168.1.1 stuff to get details about my home network and entered those into the Network Connection -> Wireless panel... and/ it just will not work, how do i know if my internal wireless card is recognized/installed...

All i want this laptop for is using and editing my Excel work doc's and web use at work to sync with my android and Pc.

Oh and to keep me entertained while flying for 12 hours...

---

### Post by chili555 on 2012-12-09
> chris@chris-HP-Compaq-6720s:~$ lspci -nn grep 0280You forgot the pipe symbol I referred to above; however, we have what we need:> Broadcom Corporation BCM4312 802.11b/g LP-PHY [[COLOR="Red"]14e4:4315[/COLOR]]Please try:```
sudo apt-get install linux-headers-generic bcmwl-kernel-source
sudo modprobe wl
```Is it working now?

---

### Post by chriswebs23 on 2012-12-09
thanks for helping guys!

chris@chris-HP-Compaq-6720s:~$ sudo apt-get install b43fwcutter
[sudo] password for chris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package b43fwcutter
chris@chris-HP-Compaq-6720s:~$ sudo apt-get install firmware-b43-lpphy-installerReading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  b43-fwcutter
The following NEW packages will be installed
  b43-fwcutter firmware-b43-lpphy-installer
0 upgraded, 2 newly installed, 0 to remove and 179 not upgraded.
Need to get 22.4 kB of archives.
After this operation, 110 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal/main b43-fwcutter i386 1:015-14 [18.9 kB]
Get:2 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal/multiverse firmware-b43-lpphy-installer all 1:015-14 [3,434 B]
Fetched 22.4 kB in 0s (91.9 kB/s)                  
Selecting previously unselected package b43-fwcutter.
(Reading database ... 152329 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a015-14_i386.deb) ...
Selecting previously unselected package firmware-b43-lpphy-installer.
Unpacking firmware-b43-lpphy-installer (from .../firmware-b43-lpphy-installer_1%3a015-14_all.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:015-14) ...
Setting up firmware-b43-lpphy-installer (1:015-14) ...
No chroot environment found. Starting normal installation
--2012-12-09 16:06:27--  [http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2)
Resolving downloads.openwrt.org (downloads.openwrt.org)... 78.24.191.177
Connecting to downloads.openwrt.org (downloads.openwrt.org)|78.24.191.177|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5986780 (5.7M) [application/octet-stream]
Saving to: `broadcom-wl-4.178.10.4.tar.bz2'

100%[======================================>] 5,986,780    211K/s   in 27s     

2012-12-09 16:06:55 (213 KB/s) - `broadcom-wl-4.178.10.4.tar.bz2' saved [5986780/5986780]

Creating new firmware directory...
broadcom-wl-4.178.10.4/
broadcom-wl-4.178.10.4/config/
broadcom-wl-4.178.10.4/config/wlconfig_nomimo
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_apsta_1chipG
broadcom-wl-4.178.10.4/config/wlconfig_lx_wl_sdstd
broadcom-wl-4.178.10.4/config/wlconfig_lx_shared
broadcom-wl-4.178.10.4/config/diffupdate.sh
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_ap_1chipG
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_ap
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_ap_sdstd
broadcom-wl-4.178.10.4/config/wl.mk
broadcom-wl-4.178.10.4/config/wltunable_lx_router.h
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_sta
broadcom-wl-4.178.10.4/config/wl_default
broadcom-wl-4.178.10.4/config/wltunable_lx_router_1chipG.h
broadcom-wl-4.178.10.4/config/wl_hnd
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_sta_1chipG
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_apsta
broadcom-wl-4.178.10.4/config/wlconfig_apdef
broadcom-wl-4.178.10.4/README
broadcom-wl-4.178.10.4/linux/
broadcom-wl-4.178.10.4/linux/wl_sta.o
broadcom-wl-4.178.10.4/linux/wl.o
broadcom-wl-4.178.10.4/linux/wl_ap.o
broadcom-wl-4.178.10.4/linux/wl_apsta.o
This file is recognised as:
  filename   :  wl_apsta.o
  version    :  478.104
  MD5        :  bb8537e3204a1ea5903fe3e66b5e2763
Extracting b43/ucode5.fw
Extracting b43/pcm5.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/ucode9.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/ucode11.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/n0initvals11.fw
Extracting b43/ucode13.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/lp0initvals13.fw
Extracting b43/ucode14.fw
Extracting b43/lp0initvals14.fw
Extracting b43/lp0bsinitvals14.fw
Extracting b43/ucode15.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/lp0initvals15.fw
Extracting b43/ucode16.fw
Extracting b43/n0bsinitvals16.fw
Extracting b43/sslpn0initvals16.fw
Extracting b43/n0initvals16.fw
Extracting b43/lp0initvals16.fw
Extracting b43/sslpn0bsinitvals16.fw
Extracting b43/lp0bsinitvals16.fw
chris@chris-HP-Compaq-6720s:~$ sudo modprobe b43
chris@chris-HP-Compaq-6720s:~$ lsmod
Module                  Size  Used by
btusb                  17950  0 
nls_iso8859_1          12617  0 
joydev                 17161  0 
coretemp               13168  0 
snd_hda_codec_analog    75059  1 
hp_wmi                 13616  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_intel          32515  2 
snd_hda_codec         111547  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
microcode              18209  0 
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                84843  0 
b43                   347284  0 
mac80211              461161  1 b43
cfg80211              175375  2 b43,mac80211
snd                    61991  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13031  0 
lpc_ich                16925  0 
soundcore              14599  1 snd
bcma                   34483  1 b43
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
rfcomm                 37276  12 
i915                  457161  3 
parport_pc             31968  0 
bnep                   17707  2 
ppdev                  12817  0 
bluetooth             183228  22 btusb,rfcomm,bnep
drm_kms_helper         45271  1 i915
drm                   230463  4 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
wmi                    18590  1 hp_wmi
video                  18847  1 i915
mac_hid                13037  0 
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
usb_storage            39350  0 
ssb                    50087  1 b43
e1000e                174645  0 
chris@chris-HP-Compaq-6720s:~$ sudo modprobe b43
chris@chris-HP-Compaq-6720s:~$ sudo apt-get install b43fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package b43fwcutter
chris@chris-HP-Compaq-6720s:~$ lsmod
Module                  Size  Used by
btusb                  17950  0 
nls_iso8859_1          12617  0 
joydev                 17161  0 
coretemp               13168  0 
snd_hda_codec_analog    75059  1 
hp_wmi                 13616  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_intel          32515  2 
snd_hda_codec         111547  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
microcode              18209  0 
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                84843  0 
b43                   347284  0 
mac80211              461161  1 b43
cfg80211              175375  2 b43,mac80211
snd                    61991  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13031  0 
lpc_ich                16925  0 
soundcore              14599  1 snd
bcma                   34483  1 b43
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
rfcomm                 37276  12 
i915                  457161  3 
parport_pc             31968  0 
bnep                   17707  2 
ppdev                  12817  0 
bluetooth             183228  22 btusb,rfcomm,bnep
drm_kms_helper         45271  1 i915
drm                   230463  4 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
wmi                    18590  1 hp_wmi
video                  18847  1 i915
mac_hid                13037  0 
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
usb_storage            39350  0 
ssb                    50087  1 b43
e1000e                174645  0

---

### Post by chriswebs23 on 2012-12-09
pipe symbol?!? lol ok trying that now

---

### Post by chriswebs23 on 2012-12-09
chris@chris-HP-Compaq-6720s:~$ sudo apt-get install linux-headers-generic bcmwl-kernel-source
[sudo] password for chris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms fakeroot linux-headers-3.5.0-19 linux-headers-3.5.0-19-generic
Suggested packages:
  dpkg-dev debhelper
The following NEW packages will be installed
  bcmwl-kernel-source dkms fakeroot linux-headers-3.5.0-19
  linux-headers-3.5.0-19-generic
The following packages will be upgraded:
  linux-headers-generic
1 upgraded, 5 newly installed, 0 to remove and 178 not upgraded.
Need to get 14.3 MB of archives.
After this operation, 73.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal/main dkms all 2.2.0.3-1.1ubuntu1 [72.8 kB]
Get:2 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal-updates/main linux-headers-3.5.0-19 all 3.5.0-19.30 [12.1 MB]
Get:3 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal-updates/main linux-headers-3.5.0-19-generic i386 3.5.0-19.30 [945 kB]
Get:4 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal/restricted bcmwl-kernel-source i386 5.100.82.112+bdcom-0ubuntu3 [1,150 kB]
Get:5 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal/main fakeroot i386 1.18.4-2 [88.0 kB]
Get:6 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal-updates/main linux-headers-generic i386 3.5.0.19.22 [2,440 B]
Fetched 14.3 MB in 41s (347 kB/s)                                              
Selecting previously unselected package dkms.
(Reading database ... 152341 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.2.0.3-1.1ubuntu1_all.deb) ...
Selecting previously unselected package linux-headers-3.5.0-19.
Unpacking linux-headers-3.5.0-19 (from .../linux-headers-3.5.0-19_3.5.0-19.30_all.deb) ...
Selecting previously unselected package linux-headers-3.5.0-19-generic.
Unpacking linux-headers-3.5.0-19-generic (from .../linux-headers-3.5.0-19-generic_3.5.0-19.30_i386.deb) ...
Selecting previously unselected package bcmwl-kernel-source.
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_i386.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.18.4-2_i386.deb) ...
Preparing to replace linux-headers-generic 3.5.0.17.19 (using .../linux-headers-generic_3.5.0.19.22_i386.deb) ...
Unpacking replacement linux-headers-generic ...
Processing triggers for man-db ...
Setting up dkms (2.2.0.3-1.1ubuntu1) ...
Setting up linux-headers-3.5.0-19 (3.5.0-19.30) ...
Setting up linux-headers-3.5.0-19-generic (3.5.0-19.30) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.5.0-19-generic /boot/vmlinuz-3.5.0-19-generic
Setting up bcmwl-kernel-source (5.100.82.112+bdcom-0ubuntu3) ...
Loading new bcmwl-5.100.82.112+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.5.0-17-generic
Building for architecture i686
Building initial module for 3.5.0-17-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.5.0-17-generic/updates/dkms/

depmod.......

DKMS: install completed.
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
update-initramfs: deferring update (trigger activated)
Setting up fakeroot (1.18.4-2) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
Setting up linux-headers-generic (3.5.0.19.22) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-17-generic
chris@chris-HP-Compaq-6720s:~$ sudo modprobe wl

---

### Post by chriswebs23 on 2012-12-09
chilli555 you are my hero!

why cant it just do that from install? is it just the vast number of wireless cards?

many thanks! now to have a fiddle! cough cough

---

### Post by chriswebs23 on 2012-12-09
screen is dark... any way to brighten it up! keyboard fn keys dont work!

---

### Post by chili555 on 2012-12-09
So  is your wireless working now? One of these solutions will work for you, but not both. We may need to fine-tune a bit.

---

### Post by chriswebs23 on 2012-12-09
yes it works great, your method worked perfectly...

thanks very much

---

### Post by mörgæs on 2012-12-09
Good, please mark the thread 'solved'.

---

### Post by celsoblk on 2013-04-16
Thanks for me too. This post very help me.

---

