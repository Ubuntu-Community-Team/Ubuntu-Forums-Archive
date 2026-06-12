---
title: "Sager NP9280 intel N6300 WiFi Ubuntu 9.10 no WiFi"
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by dieselglock on 2010-03-06
Hello,
New to these forums and new to Ubuntu. I posted yesterday in the general forums before I realized there was a specific section for Wifi.

Installed ubuntu 9.10 dual boot with win7 yesterday. Everything working but Wifi. Wifi works fine with Win7. No Wifi in Ubuntu. Very confused. I have info from the wifi trouble ticket post.

There does not seem to be a driver for this card anywhere.


lawrence@lawrence-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation X58 I/O Hub to ESI Port (rev 13)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 13)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 13)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 13)
00:13.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub I/OxAPIC Interrupt Controller (rev 13)
00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 13)
00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 13)
00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 13)
00:16.0 System peripheral: Intel Corporation 5520/5500/X58 Chipset QuickData Technology Device (rev 13)
00:16.1 System peripheral: Intel Corporation 5520/5500/X58 Chipset QuickData Technology Device (rev 13)
00:16.2 System peripheral: Intel Corporation 5520/5500/X58 Chipset QuickData Technology Device (rev 13)
00:16.3 System peripheral: Intel Corporation 5520/5500/X58 Chipset QuickData Technology Device (rev 13)
00:16.4 System peripheral: Intel Corporation 5520/5500/X58 Chipset QuickData Technology Device (rev 13)
00:16.5 System peripheral: Intel Corporation 5520/5500/X58 Chipset QuickData Technology Device (rev 13)
00:16.6 System peripheral: Intel Corporation 5520/5500/X58 Chipset QuickData Technology Device (rev 13)
00:16.7 System peripheral: Intel Corporation 5520/5500/X58 Chipset QuickData Technology Device (rev 13)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 3
00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 4
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.3 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
03:00.0 VGA compatible controller: nVidia Corporation Device 060f (rev a2)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
07:00.0 Network controller: Intel Corporation WiFi Link 6000 Series (rev 35)
08:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
08:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
08:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
08:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
lawrence@lawrence-laptop:~$ 

------------------------------------------------------------------------------------------------------
 lawrence@lawrence-laptop:~$ lsusb
Bus 006 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 5986:0440 Acer, Inc 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
lawrence@lawrence-laptop:~$ 

---------------------------------------------------------------------------------------------------------
lawrence@lawrence-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lawrence@lawrence-laptop:~$ 
----------------------------------------------------------------------------------------------------------
lawrence@lawrence-laptop:~$ lsmod
Module                  Size  Used by
isofs                  36424  1 
udf                    88136  0 
crc_itu_t               2336  1 udf
binfmt_misc            10220  1 
ppdev                   8232  0 
snd_hda_codec_si3054     5856  1 
snd_hda_codec_realtek   277860  1 
snd_hda_intel          31880  2 
snd_hda_codec          87584  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
arc4                    2144  2 
snd_mixer_oss          18976  1 snd_pcm_oss
ecb                     3296  2 
snd_pcm                93160  4 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
iwlagn                124832  0 
snd_seq_oss            33440  0 
iwlcore               133248  1 iwlagn
snd_seq_midi            8192  0 
iptable_filter          3872  0 
snd_rawmidi            27360  1 snd_seq_midi
joydev                 13088  0 
ip_tables              21200  1 iptable_filter
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
mac80211              210104  2 iwlagn,iwlcore
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               65260  0 
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                57124  0 
sdhci_pci               8928  0 
jmb38x_ms              11300  0 
sdhci                  20484  1 sdhci_pci
snd                    77096  17 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
memstick               12528  1 jmb38x_ms
lp                     11908  0 
nvidia              10316904  38 
x_tables               25832  1 ip_tables
videodev               43360  1 uvcvideo
v4l1_compat            16804  2 uvcvideo,videodev
v4l2_compat_ioctl32    13344  1 videodev
serio_raw               6596  0 
parport                40528  2 ppdev,lp
cfg80211              109144  3 iwlagn,iwlcore,mac80211
led_class               5256  2 iwlcore,sdhci
usbhid                 43968  0 
ohci1394               33780  0 
ieee1394              100896  1 ohci1394
r8169                  38884  0 
mii                     6368  1 r8169
video                  23612  0 
output                  3680  1 video
lawrence@lawrence-laptop:~$ 
--------------------------------------------------------------------------------------------------------

lawrence@lawrence-laptop:~$ sudo lshw -c network
[sudo] password for lawrence: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 02
       serial: 00:90:f5:9c:59:9b
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:58 ioport:4000(size=256) memory:f0500000-f0500fff memory:f0200000-f020ffff(prefetchable) memory:f0220000-f023ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       product: WiFi Link 6000 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 35
       serial: 00:24:d7:0e:5b:a8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:59 memory:f0400000-f0401fff
lawrence@lawrence-laptop:~$ 

------------------------------------------------------------------------------------------------------

lawrence@lawrence-laptop:~$ iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').
lawrence@lawrence-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

lawrence@lawrence-laptop:~$ 

---------------------------------------------------------------------------------------------------------------------------------

Sorry if some of this info is unnecessary I am not sure what relative and what is not.


Len

---

### Post by chili555 on 2010-03-06
Please post:```
rfkill list
```Thanks.> There does not seem to be a driver for this card anywhere.> *-network DISABLED
description: Wireless interface
product: WiFi Link 6000 Series
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:07:00.0
logical name: wmaster0
version: 35
serial: 00:24:d7:0e:5b:a8
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes [COLOR="Red"]driver=iwlagn[/COLOR]

---

### Post by dieselglock on 2010-03-06
Thanks for taking the time.

lawrence@lawrence-laptop:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
lawrence@lawrence-laptop:~$ 

Len

---

### Post by chili555 on 2010-03-07
We are wondering why, if not by the wireless switch, your wireless card is disabled. Network Manager, which is installed by default, will use the wired interface in preference to wireless, if it's available but I notice *link=no* in your *lshw*. Let's look a little deeper. The kernel keeps boot and other messages in a file called *dmesg*. Let's read it and look for messages only with iwlagn or wlan0 in them. In a terminal, please do:```
dmesg | grep -e iwlagn -e wlan0
```Post the result and we hope we will find a clue.

---

### Post by dieselglock on 2010-03-07
lawrence@lawrence-laptop:~$ dmesg | grep -e iwlagn -e wlan0
[   10.931924] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   10.931926] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   10.932950] iwlagn 0000:07:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   10.932964] iwlagn 0000:07:00.0: setting latency timer to 64
[   10.933034] iwlagn 0000:07:00.0: Detected Intel Wireless WiFi Link 6000 Series 3x3 AGN REV=0x74
[   10.985118] iwlagn 0000:07:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   10.985277] iwlagn 0000:07:00.0: irq 59 for MSI/MSI-X
[   15.667506] iwlagn 0000:07:00.0: firmware: requesting iwlwifi-6000-3.ucode
[   15.716559] iwlagn 0000:07:00.0: iwlwifi-6000-3.ucode firmware file req failed: -2
[   15.716676] iwlagn 0000:07:00.0: firmware: requesting iwlwifi-6000-2.ucode
[   15.719334] iwlagn 0000:07:00.0: iwlwifi-6000-2.ucode firmware file req failed: -2
[   15.719451] iwlagn 0000:07:00.0: firmware: requesting iwlwifi-6000-1.ucode
[   15.721554] iwlagn 0000:07:00.0: iwlwifi-6000-1.ucode firmware file req failed: -2
[   15.721746] iwlagn 0000:07:00.0: Could not read microcode: -2
[   17.200960] iwlagn 0000:07:00.0: firmware: requesting iwlwifi-6000-3.ucode
[   17.203443] iwlagn 0000:07:00.0: iwlwifi-6000-3.ucode firmware file req failed: -2
[   17.203446] iwlagn 0000:07:00.0: firmware: requesting iwlwifi-6000-2.ucode
[   17.205669] iwlagn 0000:07:00.0: iwlwifi-6000-2.ucode firmware file req failed: -2
[   17.205672] iwlagn 0000:07:00.0: firmware: requesting iwlwifi-6000-1.ucode
[   17.207398] iwlagn 0000:07:00.0: iwlwifi-6000-1.ucode firmware file req failed: -2
[   17.207401] iwlagn 0000:07:00.0: Could not read microcode: -2
lawrence@lawrence-laptop:~$ 

Here you go

Len

---

### Post by dieselglock on 2010-03-07
Just wanted to make sure you know I am not using the said laptop on any kind wired connection. I have not tried a wired connection yet.

Len

---

### Post by dieselglock on 2010-03-07
Just tried it on ethernet connection and all is well so its just the wireless.

---

### Post by chili555 on 2010-03-07
> iwlwifi-6000-1.ucode firmware file req failed: -2Please do:```
sudo apt-get install linux-backports-modules-karmic-generic
```Among other things, it includes firmware.

---

### Post by dieselglock on 2010-03-07
lawrence@lawrence-laptop:~$ sudo apt-get install linux-backports-modules-karmic-generic
[sudo] password for lawrence: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-backports-modules-2.6.31-19-generic linux-image-2.6.31-19-generic
Suggested packages:
  fdutils linux-doc-2.6.31 linux-source-2.6.31
The following NEW packages will be installed:
  linux-backports-modules-2.6.31-19-generic
  linux-backports-modules-karmic-generic linux-image-2.6.31-19-generic
0 upgraded, 3 newly installed, 0 to remove and 101 not upgraded.
Need to get 30.5MB of archives.
After this operation, 119MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main linux-image-2.6.31-19-generic 2.6.31-19.56 [28.9MB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main linux-backports-modules-2.6.31-19-generic 2.6.31-19.21 [1,616kB]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main linux-backports-modules-karmic-generic 2.6.31.19.32 [3,428B]
Fetched 30.5MB in 5min 20s (95.4kB/s)                                          
W: Duplicate sources.list entry cdrom://Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027.1) karmic/main Packages (/var/lib/apt/lists/Ubuntu%209.10%20%5fKarmic%20Koala%5f%20-%20Release%20amd64%20(20091027.1)_dists_karmic_main_binary-amd64_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027.1) karmic/restricted Packages (/var/lib/apt/lists/Ubuntu%209.10%20%5fKarmic%20Koala%5f%20-%20Release%20amd64%20(20091027.1)_dists_karmic_restricted_binary-amd64_Packages)
Selecting previously deselected package linux-image-2.6.31-19-generic.
(Reading database ... 117975 files and directories currently installed.)
Unpacking linux-image-2.6.31-19-generic (from .../linux-image-2.6.31-19-generic_2.6.31-19.56_amd64.deb) ...
Done.
Selecting previously deselected package linux-backports-modules-2.6.31-19-generic.
Unpacking linux-backports-modules-2.6.31-19-generic (from .../linux-backports-modules-2.6.31-19-generic_2.6.31-19.21_amd64.deb) ...
Selecting previously deselected package linux-backports-modules-karmic-generic.
Unpacking linux-backports-modules-karmic-generic (from .../linux-backports-modules-karmic-generic_2.6.31.19.32_amd64.deb) ...
Setting up linux-image-2.6.31-19-generic (2.6.31-19.56) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-19-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.31-19-generic          
 *  nvidia (185.18.36)...                                                       nvidia (185.18.36): Installing module.
  Kernel headers for 2.6.31-19-generic are not installed.  Cannot install this module.
  Try installing linux-headers-2.6.31-19-generic or equivalent.
                                                                         [fail]
run-parts: executing /etc/kernel/postinst.d/nvidia-common

Setting up linux-backports-modules-2.6.31-19-generic (2.6.31-19.21) ...
update-initramfs: Generating /boot/initrd.img-2.6.31-19-generic

Setting up linux-backports-modules-karmic-generic (2.6.31.19.32) ...
W: Duplicate sources.list entry cdrom://Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027.1) karmic/main Packages (/var/lib/apt/lists/Ubuntu%209.10%20%5fKarmic%20Koala%5f%20-%20Release%20amd64%20(20091027.1)_dists_karmic_main_binary-amd64_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027.1) karmic/restricted Packages (/var/lib/apt/lists/Ubuntu%209.10%20%5fKarmic%20Koala%5f%20-%20Release%20amd64%20(20091027.1)_dists_karmic_restricted_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems
lawrence@lawrence-laptop:~$


Ok so I did the apt get. In the Grub screen I now get the choice of:

2.6.31-19-gen
2.6.31-19 gen rec
2.6.31-14 gen
2.6.31-14 gen rec

I can boot into -14 just fine but when I go to 2.6.31-19 gen the screen flickers and is asking for a login and pass word. This does not happen in -14. I am not sure what the login and password is.

Len

---

### Post by chili555 on 2010-03-07
Please try:```
sudo apt-get install linux-headers-2.6.31-19-generic
sudo apt-get install --reinstall linux-backports-modules-karmic-generic
sudo apt-get update
```Now, does it install without these issues?> * nvidia (185.18.36)... nvidia (185.18.36): Installing module.
Kernel headers for 2.6.31-19-generic are not installed. [COLOR="Red"]Cannot install this module.[/COLOR]
Try installing linux-headers-2.6.31-19-generic or equivalent.
[fail]
run-parts: executing /etc/kernel/postinst.d/nvidia-commonCan you boot into -19? Does the wireless work?

---

### Post by dieselglock on 2010-03-07
sudo apt-get install linux-headers-2.6.31-19-generic
sudo apt-get install --reinstall linux-backports-modules-karmic-generic
sudo apt-get update

Sorry to be so useless but do I run these at the same time or one line at a time.

Len

---

### Post by chili555 on 2010-03-07
No problem at all, Len. We, including and especially me, were all new once.

One at a time, noting any errors E:

---

### Post by dieselglock on 2010-03-07
Ok so I did the first comand and got this:

  	 	 	 	 	 	  lawrence@lawrence-laptop:~$ sudo apt-get install linux-headers-2.6.31-19 generic[sudo] password for lawrence:  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 E: Couldn't find package generic  
 lawrence@lawrence-laptop:~$  
 

 Second command:

  	 	 	 	 	 	  lawrence@lawrence-laptop:~$ sudo apt-get install --reinstall linux-backports-modules-karmic-generic 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 The following packages were automatically installed and are no longer required: 
   linux-backports-modules-2.6.31-19-generic 
 Use 'apt-get autoremove' to remove them. 
 The following extra packages will be installed: 
   linux-backports-modules-2.6.31-20-generic linux-image-2.6.31-20-generic 
 Suggested packages: 
   fdutils linux-doc-2.6.31 linux-source-2.6.31 
 The following NEW packages will be installed: 
   linux-backports-modules-2.6.31-20-generic linux-image-2.6.31-20-generic 
 The following packages will be upgraded: 
   linux-backports-modules-karmic-generic 
 1 upgraded, 2 newly installed, 0 to remove and 252 not upgraded. 
 Need to get 30.5MB of archives. 
 After this operation, 119MB of additional disk space will be used. 
 Do you want to continue [Y/n]? y 
 Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main linux-image-2.6.31-20-generic 2.6.31-20.57 [28.9MB] 
 Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main linux-backports-modules-2.6.31-20-generic 2.6.31-20.22 [1,609kB] 
 Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main linux-backports-modules-karmic-generic 2.6.31.20.33 [3,450B] 
 Fetched 30.5MB in 3min 51s (132kB/s)                                                                       
 Selecting previously deselected package linux-image-2.6.31-20-generic. 
 (Reading database ... 121152 files and directories currently installed.) 
 Unpacking linux-image-2.6.31-20-generic (from .../linux-image-2.6.31-20-generic_2.6.31-20.57_amd64.deb) ... 
 Done. 
 Selecting previously deselected package linux-backports-modules-2.6.31-20-generic. 
 Unpacking linux-backports-modules-2.6.31-20-generic (from .../linux-backports-modules-2.6.31-20-generic_2.6.31-20.22_amd64.deb) ... 
 Preparing to replace linux-backports-modules-karmic-generic 2.6.31.19.32 (using .../linux-backports-modules-karmic-generic_2.6.31.20.33_amd64.deb) ... 
 Unpacking replacement linux-backports-modules-karmic-generic ... 
 Setting up linux-image-2.6.31-20-generic (2.6.31-20.57) ... 
 Running depmod. 
 update-initramfs: Generating /boot/initrd.img-2.6.31-20-generic 
 Running postinst hook script /usr/sbin/update-grub. 
 Generating grub.cfg ... 
 Found linux image: /boot/vmlinuz-2.6.31-20-generic 
 Found initrd image: /boot/initrd.img-2.6.31-20-generic 
 Found linux image: /boot/vmlinuz-2.6.31-19-generic 
 Found initrd image: /boot/initrd.img-2.6.31-19-generic 
 Found linux image: /boot/vmlinuz-2.6.31-14-generic 
 Found initrd image: /boot/initrd.img-2.6.31-14-generic 
 Found memtest86+ image: /boot/memtest86+.bin 
 Found Windows 7 (loader) on /dev/sda1 
 done 
 Examining /etc/kernel/postinst.d. 
 run-parts: executing /etc/kernel/postinst.d/dkms 
  * Running DKMS auto installation service for kernel 2.6.31-20-generic                                      
  *  nvidia (185.18.36)...                                                                                  nvidia (185.18.36): Installing module. 
   Kernel headers for 2.6.31-20-generic are not installed.  Cannot install this module. 
   Try installing linux-headers-2.6.31-20-generic or equivalent. 
                                                                                                     [fail] 
 run-parts: executing /etc/kernel/postinst.d/nvidia-common 
  
 Setting up linux-backports-modules-2.6.31-20-generic (2.6.31-20.22) ... 
 update-initramfs: Generating /boot/initrd.img-2.6.31-20-generic 
  
 Setting up linux-backports-modules-karmic-generic (2.6.31.20.33) ... 
 lawrence@lawrence-laptop:~$ 



At this point its asking if I want to reboot should I reboot or run the 3rd command before rebooting.


Len

---

### Post by chili555 on 2010-03-07
> sudo apt-get install linux-headers-2.6.31-19[COLOR="Red"]-[/COLOR]genericSorry, there's a hyphen in there. Please try all three again before you reboot.

---

### Post by dieselglock on 2010-03-07
[SIZE=6]**Yes**[/SIZE]  :p   Chili555 its working. I am sending this post from my wireless connection. Thank you so much for your help Chili555.

Just one other question I now have 3 versions of ubuntu -20  -19 -14 in my Grub now. 14 and 20 create errors on start up 19 is working as far as I can tell perfect. How do I remove them from the Grub and is there any thing I need to do like removing 14 and 20 from my system.

Thanks again,
 Len

---

### Post by chili555 on 2010-03-07
You can go to Synaptic and remove and reinstall -20 and -20 headers and -20 backports and you should be working fine.

Glad it's working!

---

