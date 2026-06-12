---
title: "Acer Aspire One - Wifi not working (madwifi/ath5k("
date: 2009-07-17
forum: Networking &amp; Wireless
---

### Post by bmhunt on 2009-07-17
Hi there,

My wireless isn't working on my Acer Aspire One. I've tried both ath5k and madwifi on my Ubuntu Netbook Remix - Jaunty.

_**Ath5k**_

In the ath5k case, I can sometimes connect. The NetworkManager Applet stopped "managing the device" at some point, for no apparent reason (and with no indication of where to look for a fix). At one point the ath5k module did permit a connection to the WAP/WAP2 (and/or WAP2 only) interface, but after about 20 minutes it asked for my wireless password (the same password it had just used to connect) but would not connect. When I changed the name of the network name on the router, it permitted me to connect again for a few moments.

Thus there are two problems with the ath5k module right now - NetworkManager Applet doesn't work, and I cannot consistently remain connected to the wireless network.

Here's some data from my ath5k attempt:

```

$ lspci
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


$ lsmod
Module                  Size  Used by
i915                   65668  3 
drm                    96296  4 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18368  0 
arc4                    9856  2 
ecb                    10752  2 
ath5k                 126468  0 
lbm_cw_mac80211       227492  1 ath5k
lbm_cw_cfg80211        73760  2 ath5k,lbm_cw_mac80211
led_class              12036  1 ath5k
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         434100  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
psmouse                61972  0 
serio_raw              13316  0 
pcspkr                 10496  0 
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               63240  0 
compat_ioctl32          9344  1 uvcvideo
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
video                  25360  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
output                 11008  1 video
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp
r8169                  40836  0 
mii                    13312  1 r8169
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit


$ uname -a
Linux b-17 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux


$ dpkg -l | grep linux | grep ii
ii  libselinux1                                2.0.65-5build1                            SELinux shared libraries
ii  libv4l-0                                   0.5.8-1                                   Collection of video4linux support libraries
ii  linux-backports-modules-2.6.28-13-generic  2.6.28-13.14                              Ubuntu supplied Linux modules for version 2.6.28 on x86/x86_64
ii  linux-backports-modules-jaunty             2.6.28.13.17                              Generic Linux backported drivers.
ii  linux-backports-modules-jaunty-generic     2.6.28.13.17                              Backported drivers for generic kernel image
ii  linux-firmware                             1.11                                      Firmware for Linux kernel drivers
ii  linux-generic                              2.6.28.13.17                              Complete Generic Linux kernel
ii  linux-headers-2.6.28-13                    2.6.28-13.45                              Header files related to Linux kernel version 2.6.28
ii  linux-headers-2.6.28-13-generic            2.6.28-13.45                              Linux kernel headers for version 2.6.28 on x86/x86_64
ii  linux-headers-generic                      2.6.28.13.17                              Generic Linux kernel headers
ii  linux-image-2.6.28-11-generic              2.6.28-11.42                              Linux kernel image for version 2.6.28 on x86/x86_64
ii  linux-image-2.6.28-13-generic              2.6.28-13.45                              Linux kernel image for version 2.6.28 on x86/x86_64
ii  linux-image-generic                        2.6.28.13.17                              Generic Linux kernel image
ii  linux-libc-dev                             2.6.28-13.45                              Linux Kernel Headers for development
ii  linux-restricted-modules-2.6.28-13-generic 2.6.28-13.17                              Non-free Linux kernel modules for version 2.6.28 on x86/x86_64
ii  linux-restricted-modules-common            2.6.28-13.17                              Non-free Linux 2.6.28 modules helper script
ii  linux-restricted-modules-generic           2.6.28.13.17                              Restricted Linux modules for generic kernels
ii  linux-sound-base                           1.0.18.dfsg-1ubuntu8                      base package for ALSA and OSS sound systems
ii  syslinux                                   2:3.63+dfsg-2ubuntu3                      Bootloader for Linux/i386 using MS-DOS floppies
ii  util-linux                                 2.14.2-1ubuntu4                           Miscellaneous system utilities



$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1e:68:d5:05:ad  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:251 Base address:0xc000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1e:68:d5:05:ad  
          inet addr:169.254.6.227  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:251 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2960 (2.9 KB)  TX bytes:2960 (2.9 KB)

pan0      Link encap:Ethernet  HWaddr f2:10:be:b6:0e:c5  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:23:4d:02:fd:c4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:23:4d:02:fd:c4  
          inet addr:169.254.8.140  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-23-4D-02-FD-C4-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



$ cat /var/log/syslog | grep ath | tail -n 25

Jul 17 17:09:38 b-17 kernel: [  345.063047] ath5k 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 17 17:09:38 b-17 kernel: [  345.063093] ath5k 0000:03:00.0: setting latency timer to 64
Jul 17 17:09:38 b-17 kernel: [  345.063659] ath5k 0000:03:00.0: registered as 'phy0'
Jul 17 17:09:38 b-17 kernel: [  345.176578] Registered led device: ath5k-phy0::rx
Jul 17 17:09:38 b-17 kernel: [  345.176634] Registered led device: ath5k-phy0::tx
Jul 17 17:09:38 b-17 kernel: [  345.176643] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
Jul 17 17:09:38 b-17 NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ath5k') 
Jul 17 17:58:25 b-17 kernel: [    3.024793] device-mapper: multipath: version 1.0.5 loaded
Jul 17 17:58:25 b-17 kernel: [    3.024799] device-mapper: multipath round-robin: version 1.0.0 loaded
Jul 17 17:58:25 b-17 kernel: [   12.939703] ath5k 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 17 17:58:25 b-17 kernel: [   12.939748] ath5k 0000:03:00.0: setting latency timer to 64
Jul 17 17:58:25 b-17 kernel: [   12.939970] ath5k 0000:03:00.0: registered as 'phy0'
Jul 17 17:58:25 b-17 kernel: [   13.035796] Registered led device: ath5k-phy0::rx
Jul 17 17:58:25 b-17 kernel: [   13.035832] Registered led device: ath5k-phy0::tx
Jul 17 17:58:25 b-17 kernel: [   13.035838] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
Jul 17 17:58:26 b-17 bluetoothd[2796]: Registered interface org.bluez.Service on path /org/bluez/2796/any
Jul 17 17:58:27 b-17 NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ath5k') 
Jul 17 17:58:31 b-17 gdmgreeter[3158]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks", 
Jul 17 17:58:32 b-17 gdmgreeter[3158]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks", 
Jul 17 19:59:52 b-17 kernel: [ 3374.719512] ath5k 0000:03:00.0: PCI INT A disabled
Jul 17 19:59:52 b-17 kernel: [ 3375.684478] ath5k 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
Jul 17 19:59:52 b-17 kernel: [ 3375.684524] ath5k 0000:03:00.0: restoring config space at offset 0x4 (was 0x4, writing 0x55200004)
Jul 17 19:59:52 b-17 kernel: [ 3375.684535] ath5k 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x20)
Jul 17 19:59:52 b-17 kernel: [ 3375.684551] ath5k 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
Jul 17 19:59:52 b-17 kernel: [ 3375.700211] ath5k 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18

```[U][B]
Madwifi[/B][/U]

Madwifi just doesn't create a wlan0, wifi0, wmaster0 or any other networking device to connect to the wireless network. I presume the problem may be inferred from the following message:

```
Jul 17 20:34:44 b-17 kernel: [  763.492597] wifi%d: unable to attach hardware: 'Hardware didn't respond as expected' (HAL status 3)
```And here's some data from my madwifi attempt:

```


$ lspci | grep Ath
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

$ lsmod
Module                  Size  Used by
i915                   65668  3 
drm                    96296  4 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18368  0 
ath_pci                99224  0 
wlan                  210288  1 ath_pci
ath_hal               198864  1 ath_pci
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         434100  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
psmouse                61972  0 
serio_raw              13316  0 
snd_rawmidi            29696  1 snd_seq_midi
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
pcspkr                 10496  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
uvcvideo               63240  0 
compat_ioctl32          9344  1 uvcvideo
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
video                  25360  0 
output                 11008  1 video
r8169                  40836  0 
mii                    13312  1 r8169
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit


$ uname -a 
Linux b-17 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux


bmh@b-17:~$ dmesg | egrep "ath_(hal|pci)"
[   12.839813] ath_hal: module license 'Proprietary' taints kernel.
[   12.843501] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   12.891136] ath_pci: 0.9.4
[   12.891257] ath_pci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.891314] ath_pci 0000:03:00.0: setting latency timer to 64
[   12.939942] ath_pci 0000:03:00.0: PCI INT A disabled



$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1e:68:d5:05:ad  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:251 Base address:0xc000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1e:68:d5:05:ad  
          inet addr:169.254.6.227  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:251 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1856 (1.8 KB)  TX bytes:1856 (1.8 KB)

pan0      Link encap:Ethernet  HWaddr a6:02:5e:2a:70:73  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


$ sudo modprobe -r ath_pci
$ sudo modprobe ath_pci
$ tail /var/log/syslog
Jul 17 20:34:39 b-17 kernel: [  758.325088] wlan: driver unloaded
Jul 17 20:34:39 b-17 kernel: [  758.341138] ath_hal: driver unloaded
Jul 17 20:34:44 b-17 kernel: [  763.399713] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
Jul 17 20:34:44 b-17 kernel: [  763.470135] wlan: 0.9.4
Jul 17 20:34:44 b-17 kernel: [  763.486847] ath_pci: 0.9.4
Jul 17 20:34:44 b-17 kernel: [  763.486944] ath_pci 0000:03:00.0: enabling device (0000 -> 0002)
Jul 17 20:34:44 b-17 kernel: [  763.486966] ath_pci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 17 20:34:44 b-17 kernel: [  763.486999] ath_pci 0000:03:00.0: setting latency timer to 64
Jul 17 20:34:44 b-17 kernel: [  763.492597] wifi%d: unable to attach hardware: 'Hardware didn't respond as expected' (HAL status 3)
Jul 17 20:34:44 b-17 kernel: [  763.492650] ath_pci 0000:03:00.0: PCI INT A disabled

```I've spent a great deal of time on this, without any appreciable progress. Any suggestions would be very much appreciated.

My next step would be, subject to input from this form, to get the latest madwifi directly, and compile the module independent of linux-restricted-modules-2.6.28-13-generic.

Cheers

---

### Post by bmhunt on 2009-07-17
Incidentally, I've tried the new madwifi driver (i.e. madwifi-hal-0.10.5.6-current.tar.gz). When the machine boots, NetworkManager indicates that it's doing something (those circles rotating icon), but it doesn't connect to the wireless network and NetworkManager keeps asking for my wireless password (which I diligently provide).

I'm at a loss, and would duly appreciate help. It's all the more confusing and frustrating because of the reports suggesting that the wifi works on the Aspire One with both ath5k and madwifi.

/var/log/syslog reports:

```
Jul 17 21:51:07 b-17 NetworkManager: <info>  ath0: link timed out. 
Jul 17 21:51:53 b-17 NetworkManager: <info>  Activation (ath0/wireless): association took too long. 
Jul 17 21:51:53 b-17 NetworkManager: <info>  (ath0): device state change: 5 -> 6 
Jul 17 21:51:53 b-17 NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Jul 17 21:51:53 b-17 NetworkManager: <info>  Activation (ath0/wireless): asking for new secrets 
Jul 17 21:51:53 b-17 NetworkManager: <info>  (ath0): supplicant connection state:  associating -> disconnected 
Jul 17 21:51:57 b-17 NetworkManager: <info>  (ath0): supplicant connection state:  disconnected -> scanning 
Jul 17 21:52:03 b-17 NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Jul 17 21:52:03 b-17 NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Jul 17 21:52:03 b-17 NetworkManager: <info>  (ath0): device state change: 6 -> 4 
Jul 17 21:52:03 b-17 NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Jul 17 21:52:03 b-17 NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Jul 17 21:52:03 b-17 NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Jul 17 21:52:03 b-17 NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Jul 17 21:52:03 b-17 NetworkManager: <info>  (ath0): device state change: 4 -> 5 
Jul 17 21:52:03 b-17 NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Jul 17 21:52:03 b-17 NetworkManager: <info>  Activation (ath0/wireless): connection 'H' has security, and secrets exist.  No new secrets needed. 
Jul 17 21:52:03 b-17 NetworkManager: <info>  Config: added 'ssid' value 'H' 
Jul 17 21:52:03 b-17 NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Jul 17 21:52:03 b-17 NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Jul 17 21:52:03 b-17 NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Jul 17 21:52:03 b-17 NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jul 17 21:52:03 b-17 NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jul 17 21:52:03 b-17 NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Jul 17 21:52:03 b-17 NetworkManager: <info>  Config: set interface ap_scan to 2 
Jul 17 21:52:03 b-17 NetworkManager: <info>  (ath0): supplicant connection state:  scanning -> disconnected 
Jul 17 21:52:03 b-17 NetworkManager: <info>  (ath0): supplicant connection state:  disconnected -> scanning 
Jul 17 21:52:03 b-17 NetworkManager: <info>  (ath0): supplicant connection state:  scanning -> associating 
Jul 17 21:52:05 b-17 kernel: [  121.821055] CE: hpet increasing min_delta_ns to 15000 nsec
Jul 17 21:52:18 b-17 NetworkManager: <info>  ath0: link timed out. 
bmh@b-17:/var/log$ tail -n 30 syslog
Jul 17 21:52:03 b-17 NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Jul 17 21:52:03 b-17 NetworkManager: <info>  Config: set interface ap_scan to 2 
Jul 17 21:52:03 b-17 NetworkManager: <info>  (ath0): supplicant connection state:  scanning -> disconnected 
Jul 17 21:52:03 b-17 NetworkManager: <info>  (ath0): supplicant connection state:  disconnected -> scanning 
Jul 17 21:52:03 b-17 NetworkManager: <info>  (ath0): supplicant connection state:  scanning -> associating 
Jul 17 21:52:05 b-17 kernel: [  121.821055] CE: hpet increasing min_delta_ns to 15000 nsec
Jul 17 21:52:18 b-17 NetworkManager: <info>  ath0: link timed out. 
Jul 17 21:53:03 b-17 NetworkManager: <info>  Activation (ath0/wireless): association took too long. 
Jul 17 21:53:03 b-17 NetworkManager: <info>  (ath0): device state change: 5 -> 6 
Jul 17 21:53:03 b-17 NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Jul 17 21:53:03 b-17 NetworkManager: <info>  Activation (ath0/wireless): asking for new secrets 
Jul 17 21:53:03 b-17 NetworkManager: <info>  (ath0): supplicant connection state:  associating -> disconnected 
Jul 17 21:53:06 b-17 NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: applet-device-wifi.c.1539 (get_secrets_dialog_response_cb): canceled. 
Jul 17 21:53:06 b-17 NetworkManager: <info>  (ath0): device state change: 6 -> 9 
Jul 17 21:53:06 b-17 NetworkManager: <info>  Activation (ath0) failed for access point (H) 
Jul 17 21:53:06 b-17 NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Jul 17 21:53:06 b-17 NetworkManager: <info>  Marking connection 'H' invalid. 
Jul 17 21:53:06 b-17 NetworkManager: <info>  Activation (ath0) failed. 
Jul 17 21:53:06 b-17 NetworkManager: <info>  (ath0): device state change: 9 -> 3 
Jul 17 21:53:06 b-17 NetworkManager: <info>  (ath0): deactivating device (reason: 0). 

```/var/log/wpa_supplicant reports:

```
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with SSID 'H'
Authentication with 00:00:00:00:00:00 timed out.
Trying to associate with SSID 'H'
CTRL-EVENT-SCAN-RESULTS 
No network configuration found for the current AP
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with SSID 'H'
Authentication with 00:00:00:00:00:00 timed out.
Trying to associate with SSID 'H'
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with SSID 'H'

```Please advise if there is any further information that may be of assistance.

Best regards,
Brian

---

### Post by enz1m3 on 2009-07-19
Are you using the latest netbook remix? This is very weird because I've made a few installations of it and it works out-of-the-box...

Have you tried reinstalling unr or is it nonviable now?

When you say the wifi didn't work after installing unr, what happened? It didn't detect any network or the wlan device at all?

---

### Post by bmhunt on 2009-07-19
Thanks for the reply.

There seemed to have been two problems:

1. The kernel/wireless driver didn't work (i.e. ath5k and the ath_pci that comes with backports-jaunty). Solution: Install the latest Madwifi from the madwifi website. I.e.:

```
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz
sudo apt-get install build-essential linux-headers-$(uname -r)
tar -xzf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6*/
make
sudo make install
sudo modprobe ath_pci

```

2. Even when the network driver did work, the connection wasn't working reliably (i.e. NetworkManager kept asking for passwords). Solution: Install [WICD]("http://wicd.sourceforge.net/").

Seems to be working reliably now (knock on wood!).

---

### Post by Liveman on 2009-07-20
Problems too. Shows that the LED light on the switch doesnt respond even if connected. I use madwifi... it works but dont show on LED.

//Liveman

---

### Post by crossz on 2009-07-24
> **bmhunt said:**
> Thanks for the reply.

There seemed to have been two problems:

1. The kernel/wireless driver didn't work (i.e. ath5k and the ath_pci that comes with backports-jaunty). Solution: Install the latest Madwifi from the madwifi website. I.e.:

```
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz
sudo apt-get install build-essential linux-headers-$(uname -r)
tar -xzf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6*/
make
sudo make install
sudo modprobe ath_pci

```

2. Even when the network driver did work, the connection wasn't working reliably (i.e. NetworkManager kept asking for passwords). Solution: Install [WICD]("http://wicd.sourceforge.net/").

Seems to be working reliably now (knock on wood!).

I have tried both methods you mentioned. But none of them works.
I do think it's driver problem, so no matter wicd or network manager, the wifi card will not work properly.

My situation is same as mentioned above, with the original 9.04 installation 2 months ago, the wifi worked out of box. But recently I updated and upgraded ubuntu from kernel 2.6.28-11 to 2.6.28-13-generic, then the wifi stop working.

But when I reinstalled the Ubuntu 9.04 (kernel 2.6.28-11), the wifi still did not work.

Totally lost! The wifi card should be fine, I tried using other OS, but only Ubuntu-Netbook-remix can not recognize it correctly.

Why? can not recover kernel back?

---

### Post by Nonno Bassotto on 2009-07-28
Same problem of Crossz, although not on a AA1 (but I still have the Atheros card). Upgraded to last kernel (2.6.28.14), lost wireless, and now even the older kernels cannot connect.

---

### Post by fergarciaga on 2009-07-29
I get almost the same problem as crossz, too.
I reinstalled and updated Ubuntu 9.04 (the WiFi card used to work out-of-the-box on my AA1 prior to the reinstallation), also attempted with gNewSense, which is a distro based on Ubuntu. Neither the ath5k nor the madwifi will make the card work (in spite of being listed with lspci and doing sudo modprobe ath5k/ath_pci).
Any clue?
Thanks a lot!

---

### Post by Nonno Bassotto on 2009-07-29
This morning my laptop started working again, with no apparent reason :confused:

---

### Post by nealos on 2009-10-27
FWIW, I was having these same troubles and it was driving me mad (no pun intended).  It turns out, that at some point, I must have tried toggling the wifi switch on the front of my aspire one.  I think it remembers the "off" position since, after many unsuccessful reboots in between fooling around with various configurations, I tried toggling the wifi switch and it came to life!  Moral of the story, make sure your wifi switch is in the "on" state.

Neal

---

