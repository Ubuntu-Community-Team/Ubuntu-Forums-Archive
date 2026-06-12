---
title: "Wifi drops out but says connected on Intel 5100 in 12.04.1 LTS"
date: 2013-01-15
forum: Networking &amp; Wireless
---

### Post by Skullsworth on 2013-01-15
I am running 12.04.1 LTS off of a bootable USB drive with 4GB persistent file system.  On a fresh install the wireless will work as soon as I enter the password.  After some time (sometimes a while 45+ minutes and sometimes just a few minutes) the connection will no longer work.  The connection info will show no difference between it working and not.
After a reboot, the connection info will say that it is connected, but the connection is in fact not working.

I've found a similar issue in these forums that recommend the following series of commands:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```This series of commands will consistently get my connection working once per boot (if this got the connection working again, but then it drops out another time, re-entering the commands does not seem to consistently work a second time and I need to reboot).

1 Dell studio 1555 laptop
2 Intel Corp Wifi Link 5100
3 ifconfig :  ```
Link encap:Ethernet  HWaddr 00:22:fb:a6:fb:94  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:fbff:fea6:fb94/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:54 errors:0 dropped:0 overruns:0 frame:0
          TX packets:259 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5114 (5.1 KB)  TX bytes:31459 (31.4 KB)
```iwconfig:  ```
wlan1     IEEE 802.11abg  ESSID:"HOME-BB62"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1D:D1:35:BB:60   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```4 lsmod:  ```
Module                  Size  Used by
dm_crypt               22528  0 
arc4                   12473  2 
snd_hda_codec_hdmi     31775  1 
iwlwifi               291907  0 
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  5 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
mac80211              436455  1 iwlwifi
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
r852                   17901  0 
cfg80211              178679  2 iwlwifi,mac80211
sm_common              16737  1 r852
snd_seq_midi_event     14475  1 snd_seq_midi
nand                   49667  2 r852,sm_common
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
nand_ids                8547  1 nand
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mtd                    35584  2 sm_common,nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
snd                    62064  20 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nand_ecc               13070  1 nand
uvcvideo               67203  0 
r592                   17808  0 
soundcore              14635  1 snd
btusb                  17912  2 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
memstick               15857  1 r592
videodev               86588  1 uvcvideo
psmouse                72919  0 
joydev                 17393  0 
parport_pc             32114  0 
dell_wmi               12601  0 
dell_laptop            17767  0 
mac_hid                13077  0 
ppdev                  12849  0 
serio_raw              13027  0 
sparse_keymap          13658  1 dell_wmi
bnep                   17830  2 
dcdbas                 14098  1 dell_laptop
rfcomm                 38139  12 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
bluetooth             158438  23 btusb,bnep,rfcomm
dm_multipath           22710  0 
ext2                   67987  1 
squashfs               36095  1 
overlayfs              27511  1 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
usbhid                 41906  0 
hid                    77367  1 usbhid
radeon                737789  3 
firewire_ohci          40172  0 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
ttm                    65344  1 radeon
tg3                   141369  0 
drm_kms_helper         45466  1 radeon
drm                   197692  5 radeon,ttm,drm_kms_helper
usb_storage            39646  1 
wmi                    18744  1 dell_wmi
video                  19068  0 
i2c_algo_bit           13199  1 radeon

```5 dmesg | grep wlan1: ```
[   67.486042] udevd[2575]: renamed network interface wlan0 to wlan1
[   67.667008] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   67.667261] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   77.547260] wlan1: authenticate with 00:1d:d1:35:bb:60 (try 1)
[   77.549910] wlan1: authenticated
[   77.554667] wlan1: associate with 00:1d:d1:35:bb:60 (try 1)
[   77.561236] wlan1: RX AssocResp from 00:1d:d1:35:bb:60 (capab=0xc11 status=0 aid=1)
[   77.561240] wlan1: associated
[   77.566193] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   88.240021] wlan1: no IPv6 routers present
```6 sudo lshw -C network:  ```
 *-network               
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan1
       version: 00
       serial: 00:22:fb:a6:fb:94
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-29-generic-pae firmware=8.83.5.1 build 33692 ip=10.0.0.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:49 memory:f8000000-f8001fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:26:b9:01:e1:08
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 firmware=sb v2.17 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:50 memory:fc100000-fc10ffff

```7 iwlist scan: ```
 lo        Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 00:1D:D1:35:BB:60
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"HOME-BB62"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000494c902145
                    Extra: Last beacon: 50604ms ago
                    IE: Unknown: 0009484F4D452D42423632
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A0C0016FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1606000100000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000025127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD7D0050F204104A0001101044000102103B000103104700102880288028801880A880001DD135BB6010210005415252495310230006544738363247102400065254323836301042000831323334353637381054000800060050F204000110110012415252495320544738363220526F75746572100800020084103C000101

eth0      Interface doesn't support scanning.
```8 lsb_release -d:  ```
Description:    Ubuntu 12.04.1 LTS
```9 uname -mr: ```
 3.2.0-29-generic-pae i686 
```10 sudo /etc/init.d/networking restart: ```
  * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 

```Any help or explanation of what I am doing (wrong) or any decent explanation of anything really is greatly appreciated.

Thank you
-c

---

### Post by ahallubuntu on 2013-01-16
It looks like you're not using the latest kernel available - ?  Have you tried updating it to latest in the repository?

I am using a 5100 card in a couple of Dell laptops with Ubuntu 12.04.1 and have had no connections issues at all with them (one install is a 32 bit, one is 64 bit).  In fact, I don't have to disable 802.11n speeds - I get good local transfer rates on my network.   I'm using an 802.11n Asus router with DD-WRT, WPA2 Personal, AES.  What kind of router are you connected to?

---

### Post by Demonarc on 2013-01-16
you may not even have a linux issue. Have you changed your channels at all? are you losing connection on a hard wire? are you on a cisco router?

---

### Post by Skullsworth on 2013-01-16
I dont think it is an issue with any of my hardware as when I boot into windows 7 my wifi connection works flawlessly.

My modem/router is a comcast/xfinity Arris TG862G/GT model

How would I update my kernel?

---

### Post by ahallubuntu on 2013-01-17
In Ubuntu, kernel updates are pushed with regular updates.  If you look at updates listed in Update Manager, you'll probably see a couple related to the kernel.  Or you can just do all updates and that should nail it.

I have seen issues with routers where wireless worked fine with Windows but not with Linux.  One issue used to be WiFi Protected Setup; I always disable that in my routers, anyway, but I have seen cases where WPS messed up Linux connections.  But that was a couple of years ago.

I will say that I have used my Dell laptop with 5100 wireless card on dozens of WiFi hot spots over the years in coffee shops, airports, etc. and have never had a problem I can recall since I started with 10.04 LTS and not since a more recent change to 12.04 LTS.  I get great connection speeds, solid connections, no real issues.

---

### Post by Skullsworth on 2013-01-29
With a wired connection (after it failed when 2/3rds done on my wireless connection) I performed all updates.  Following the post-update reboot, the same problem was present.  I tried the series of commands I mentioned in my first post:
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

but this time, it had bad results.  Upon entering the third command I got a fatal error and my network list emptied:


```
ubuntu@ubuntu:~$ echo "options iwlwifi 11n_disable" | sudo tee /etc/modprobe.d/iwlwifi.conf
options iwlwifi 11n_disable
ubuntu@ubuntu:~$ sudo modprobe -rfv iwlwifi
rmmod /lib/modules/3.2.0-29-generic-pae/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
rmmod /lib/modules/3.2.0-29-generic-pae/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.2.0-29-generic-pae/kernel/net/wireless/cfg80211.ko
ubuntu@ubuntu:~$ sudo modprobe -v iwlwifi
insmod /lib/modules/3.2.0-29-generic-pae/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.2.0-29-generic-pae/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.2.0-29-generic-pae/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko 11n_disable
FATAL: Error inserting iwlwifi (/lib/modules/3.2.0-29-generic-pae/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko): Invalid argument
```

Any ideas?
Anyone?
Any help is greatly appreciated.  I really want to get this sorted out but I dont even know what I'm looking at or where to begin.

Thanks again.

---

### Post by ahallubuntu on 2013-01-29
You have show options listed two different ways - what did you actually put in the modprobe conf file?

This is correct:

```
options iwlwifi 11n_disable=1

```

This below is invalid:

```
options iwlwifi 11n_disable
```

Forget about the tee.  Just open the file and edit it properly.  In a terminal type:

```
gksu gedit /etc/modprobe.d/iwlwifi.conf
```

and set the options correctly.

Also, I see errors in "3.2.0-29" kernel.  That indicates that you didn't reboot after the update or didn't do all the updates?  You should be on 3.2.0-36 .  29 is the old one .

---

### Post by ahallubuntu on 2013-01-29
I want to point out again that I have four laptops (myself + family/friends) using this 5100 card running 12.04 (three Dells, one Acer) and I have not needed this option to disable 802.11n .  I get great wireless N connections all the time.    I use my primary laptop on numerous access points of all types and never wireless problems.

But, it is worth a try if you are having problems.

---

### Post by 452 on 2013-02-17
I have also this problem, Asus M50VC intel 5100 Ubuntu 12.10
17.02.2013

iwconfig show always: Bit Rate=1 Mb/s
even if I&#8217;m standing near router
connections freeze o_O

---

