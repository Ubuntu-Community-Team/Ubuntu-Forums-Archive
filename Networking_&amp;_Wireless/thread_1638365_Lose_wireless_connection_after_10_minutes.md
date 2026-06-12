---
title: "Lose wireless connection after 10 minutes"
date: 2010-12-05
forum: Networking &amp; Wireless
---

### Post by markcoronado on 2010-12-05
I have a Acer Aspire 7535-5020 laptop with a Atheros AR5B91 wireless adapter & lose my connection after about 10 minutes.
The only way to reconnect is by rebooting.
I read in another thread that installing the linux-backports-modules-karmic would solve the problem.

However when I try to install it I get the message, Error Dependency is not satisfiable:Linux-backports-Modules-2.6.31-22 generic.

Any idea as to what I'm doing wrong?

I'm new to Linux.

---

### Post by northd_tech on 2010-12-05
Hi Mark,

Are you sure that you have the header files for your kernel installed?  You will need to do this for all of the Linux kernels that you want to use with your wireless (and each time an update finds a new kernel, unless the new kernel has "built-in" wireless support for your WiFi interface).

Run these 2 terminal commands and post any error messages that you get (warnings aren't so scary, and there are usually lots of those).
```
sudo apt-get update
sudo apt-get install linux-headers-$(uname -r)

```

Then try installing the backports again and see if your error message has disappeared.

Also, could you post the results of the following terminal commands (maybe in a different post because there will be a lot to copy/paste):

```
lspci
lsusb
sudo lshw -C network
lsmod
ifconfig
iwconfig

uname -a
lsb_release -d
```

It is also possible that those backports aren't the correct versions for your version of Ubuntu (but those last 2 commands should tell us that).

---

### Post by markcoronado on 2010-12-06
[QUOTE=northd_tech;10203915]Hi Mark,

Are you sure that you have the header files for your kernel installed?  You will need to do this for all of the Linux kernels that you want to use with your wireless (and each time an update finds a new kernel, unless the new kernel has "built-in" wireless support for your WiFi interface).

Run these 2 terminal commands and post any error messages that you get (warnings aren't so scary, and there are usually lots of those).
```
sudo apt-get update
sudo apt-get install linux-headers-$(uname -r)

```Then try installing the backports again and see if your error message has disappeared.

Thanks for the help northd tech

mark@mark-laptop:~$ sudo apt-get update
[sudo] password for mark: 
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done            
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
mark@mark-laptop:~$ 


mark@mark-laptop:~$ sudo apt-get install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.31-14-generic is already the newest version.
linux-headers-2.6.31-14-generic set to manually installed.
The following packages were automatically installed and are no longer required:
  libtwolame0 liba52-0.7.4 libsidplay1 libmpeg2-4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mark@mark-laptop:~$ 


Error message still there after trying to install.
Error: Dependency is not satisfiable: linux-backports-modules-2.6.31-22-generic

---

### Post by markcoronado on 2010-12-06
mark@mark-laptop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Acer Incorporated [ALI] Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev ff)
mark@mark-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 064e:a103 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
mark@mark-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
 product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: 00:26:2d:57:c0:84
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=sb v2.19 ip=192.168.1.103 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:f0300000-f030ffff
  *-generic
       description: Wireless interface
       product: Illegal Vendor ID
       vendor: Illegal Vendor ID
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: ff
       serial: 0c:60:76:1b:b5:a5
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master vga_palette cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=255 maxlatency=255 mingnt=255 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0400000-f040ffff
mark@mark-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc            10220  1 
ppdev                   8232  0 
snd_hda_codec_atihdmi     4320  1 
snd_hda_codec_realtek   277860  1 
snd_hda_intel          31880  2 
snd_hda_codec          87584  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
arc4                    2144  2 
ecb                     3296  2 
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
ath9k                 278176  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
mac80211              210104  1 ath9k
uvcvideo               65260  0 
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
psmouse                57124  0 
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lp                     11908  0 
ath                    10304  1 ath9k
snd                    77096  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               43360  1 uvcvideo
amd64_edac_mod         26688  0 
iptable_filter          3872  0 
serio_raw               6596  0 
ip_tables              21200  1 iptable_filter
acer_wmi               18504  0 
soundcore               9088  1 snd
joydev                 13088  0 
parport                40528  2 ppdev,lp
i2c_piix4              11728  0 
v4l1_compat            16804  2 uvcvideo,videodev
v4l2_compat_ioctl32    13344  1 videodev
edac_core              48876  1 amd64_edac_mod
shpchp                 37756  0 
x_tables               25832  1 ip_tables
led_class               5256  2 ath9k,acer_wmi
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
cfg80211              109144  3 ath9k,mac80211,ath
hid_logitech           10112  0 
ff_memless              6504  1 hid_logitech
usbhid                 43968  1 hid_logitech
video                  23612  0 
radeon                684512  1 
output                  3680  1 video
ttm                    43056  1 radeon
tg3                   123748  0 
drm                   193856  3 radeon,ttm
i2c_algo_bit            7076  1 radeon
mark@mark-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:2d:57:c0:84  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:2dff:fe57:c084/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2762 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2348 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3041641 (3.0 MB)  TX bytes:340004 (340.0 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 0c:60:76:1b:b5:a5  
          inet6 addr: fe80::e60:76ff:fe1b:b5a5/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1777 (1.7 KB)  TX bytes:6039 (6.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 0C-60-76-1B-B5-A5-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

mark@mark-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"ACTIONTEC"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mark@mark-laptop:~$ 
mark@mark-laptop:~$ uname -a
Linux mark-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux
mark@mark-laptop:~$ lsb_release -d

---

### Post by markcoronado on 2010-12-09
I got it working by installing the 10.04 LTS update.

I have been able to stay connected for over 4 hours now.
Hope it stays that way.

---

