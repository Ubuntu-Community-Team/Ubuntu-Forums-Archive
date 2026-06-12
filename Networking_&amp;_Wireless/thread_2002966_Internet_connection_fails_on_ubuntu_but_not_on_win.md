---
title: "Internet connection fails on ubuntu but not on windows"
date: 2012-06-13
forum: Networking &amp; Wireless
---

### Post by mariuszp on 2012-06-13
I am connected to the internet via wireless wifi. There are not problems with that on Windows 7, but it does not work properly on ubuntu.

When I go on any website (with Chrome or Firefox), it initially works, but later the internet connection starts becoming slower and slower, until eventually it gets to the point where no website can be opened, but the network manager reports that there is full signal strength. Also, resetting the connection makes it go back to fast, but then it slows down again and the whole scenario repeats.

In case you need it, here's the output from "sudo ethtool eth0":

```


Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Half
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
	Link detected: no

```

I found on some forum that setting duplex to full and turning off "auto-negotiation" might help, but it doesn't work for me.

Does anyone know what could cause this problem?

---

### Post by wildmanne39 on 2012-06-13
Hi, please try:
```
echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf . /dev/null
```
Thanks

---

### Post by mariuszp on 2012-06-13
> **wildmanne39 said:**
> Hi, please try:
```
echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf . /dev/null
```
Thanks

Am I literally supposed to type "nameserver 8.8.8.8" or am I meant to find out what the nameserver is and its IP address? If so, how do I do this?

---

### Post by wildmanne39 on 2012-06-13
Hi, just copy and paste the command into the terminal.
Thanks

---

### Post by mariuszp on 2012-06-13
> **wildmanne39 said:**
> Hi, just copy and paste the command into the terminal.
Thanks

I did. The output was:

```

tee: .: Jest katalogiem [is a directory]
nameserver 8.8.8.8

```

what now?

BTW: it created the /etc/resolv.conf file with "nameserver 8.8.8.8" in it.

---

### Post by wildmanne39 on 2012-06-13
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod

```
here by clicking on new reply and click # and paste the information between the brackets.

set your wireless settings to match the screenshots.
Thank you

---

### Post by mariuszp on 2012-06-13
Here's the output from the commands before changing the settings:

```


mariusz@mariusz-laptop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
Linux mariusz-laptop 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 x86_64 GNU/Linux
mariusz@mariusz-laptop:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Toshiba America Info Systems Device [1179:fd30]
	Kernel driver in use: r8169
--
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8184]
	Kernel driver in use: rtl819xSE
mariusz@mariusz-laptop:~$ lsusb
Bus 002 Device 003: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:58f2 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
mariusz@mariusz-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  ESSID:"O2wirelessF63A57"  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:26:44:F6:3A:57   
          Bit Rate=39 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management period:0us  mode:All packets received
          Link Quality=76/100  Signal level=-59 dBm  Noise level=-108 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

mariusz@mariusz-laptop:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
mariusz@mariusz-laptop:~$ lsmod
Module                  Size  Used by
iwlagn                202721  0 
iwlcore               146875  1 iwlagn
mac80211              267099  2 iwlagn,iwlcore
michael_mic             2188  4 
arc4                    1497  2 
cryptd                  8140  0 
aes_x86_64              7936  1 
aes_generic            27631  1 aes_x86_64
binfmt_misc             7984  1 
vboxnetadp              5267  0 
vboxnetflt             14966  0 
vboxdrv              1792856  2 vboxnetadp,vboxnetflt
kvm_intel              49279  0 
kvm                   299345  1 kvm_intel
parport_pc             30086  0 
ppdev                   6804  0 
joydev                 11395  0 
snd_hda_codec_nvhdmi    14221  4 
snd_hda_codec_realtek   302155  1 
snd_hda_intel          25542  2 
snd_hda_codec          99195  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
usbhid                 42030  0 
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
nvidia              10221046  40 
snd_seq                57512  3 snd_seq_midi,snd_seq_midi_event
hid                    84710  1 usbhid
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
r8192se_pci           512896  0 
video                  22176  0 
uvcvideo               62379  0 
output                  2527  1 video
jmb38x_ms               8667  0 
videodev               49359  1 uvcvideo
snd                    64181  14 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              170485  4 iwlagn,iwlcore,mac80211,r8192se_pci
intel_agp              32334  0 
usb_storage            50436  0 
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12614  1 videodev
psmouse                62080  0 
serio_raw               4910  0 
memstick               10185  1 jmb38x_ms
lp                     10201  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
parport                37032  3 parport_pc,ppdev,lp
r8169                  42254  0 
ahci                   22210  2 
mii                     5261  1 r8169
libahci                26148  1 ahci
sdhci_pci               8083  0 
sdhci                  18400  1 sdhci_pci
led_class               3393  1 sdhci

```

And here's the output after the change in settings:

```


mariusz@mariusz-laptop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
Linux mariusz-laptop 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 x86_64 GNU/Linux
mariusz@mariusz-laptop:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Toshiba America Info Systems Device [1179:fd30]
	Kernel driver in use: r8169
--
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8184]
	Kernel driver in use: rtl819xSE
mariusz@mariusz-laptop:~$ lsusb
Bus 002 Device 003: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:58f2 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
mariusz@mariusz-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  ESSID:"O2wirelessF63A57"  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:26:44:F6:3A:57   
          Bit Rate=26 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management period:0us  mode:All packets received
          Link Quality=79/100  Signal level=-59 dBm  Noise level=-109 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

mariusz@mariusz-laptop:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
mariusz@mariusz-laptop:~$ lsmod
Module                  Size  Used by
iwlagn                202721  0 
iwlcore               146875  1 iwlagn
mac80211              267099  2 iwlagn,iwlcore
michael_mic             2188  8 
arc4                    1497  4 
cryptd                  8140  0 
aes_x86_64              7936  1 
aes_generic            27631  1 aes_x86_64
binfmt_misc             7984  1 
vboxnetadp              5267  0 
vboxnetflt             14966  0 
vboxdrv              1792856  2 vboxnetadp,vboxnetflt
kvm_intel              49279  0 
kvm                   299345  1 kvm_intel
parport_pc             30086  0 
ppdev                   6804  0 
joydev                 11395  0 
snd_hda_codec_nvhdmi    14221  4 
snd_hda_codec_realtek   302155  1 
snd_hda_intel          25542  2 
snd_hda_codec          99195  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
usbhid                 42030  0 
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
nvidia              10221046  40 
snd_seq                57512  3 snd_seq_midi,snd_seq_midi_event
hid                    84710  1 usbhid
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
r8192se_pci           512896  0 
video                  22176  0 
uvcvideo               62379  0 
output                  2527  1 video
jmb38x_ms               8667  0 
videodev               49359  1 uvcvideo
snd                    64181  14 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              170485  4 iwlagn,iwlcore,mac80211,r8192se_pci
intel_agp              32334  0 
usb_storage            50436  0 
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12614  1 videodev
psmouse                62080  0 
serio_raw               4910  0 
memstick               10185  1 jmb38x_ms
lp                     10201  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
parport                37032  3 parport_pc,ppdev,lp
r8169                  42254  0 
ahci                   22210  2 
mii                     5261  1 r8169
libahci                26148  1 ahci
sdhci_pci               8083  0 
sdhci                  18400  1 sdhci_pci
led_class               3393  1 sdhci

```

---

### Post by wildmanne39 on 2012-06-13
Hi, there are a couple of things I see.

1. You are using an unsupported version of ubuntu I recommend you upgrade.

2. You have two wireless device drivers, so they are conflicting.

3. This is strange > Power Management period:0us 
Thanks

---

### Post by mariuszp on 2012-06-14
What are the names of the 2 drivers, which one should I uninstall and how? Also, I cannot upgrade because of the internet connection crashing..

EDIT: I tried removing the top module (r8169) but it turns out that its the Ethernet driver, whereas the other one is the WIFI driver, so they don't conflict. I'm using wifi.

---

### Post by wildmanne39 on 2012-06-14
Hi, let's give this a shot we will remove the conflicting driver first.
```
echo "blacklist iwlagn" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then we turn power management off:
```
gksudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default powermanagement behavior) and enter the following: 
```
#!/bin/sh

/sbin/iwconfig wlan0 power off
```

above exit0, then save gedit, close, disconnect wired connection and reboot.
Thanks

---

### Post by mariuszp on 2012-06-14
i don't have the file "wireless". do i still create it?

EDIT: i just created that file and also ran the command you suggested, and after rebooting my system i still have the same problem. also, i don't have any wired connection.

---

### Post by wildmanne39 on 2012-06-14
Hi, please post the output of:
```
iwconfig
dmesg | egrep 'rtl|firm|radio|switch|wlan0'
lsmod | grep -e rtl -e iwl
```
the contents of:
```
gksudo gedit /etc/pm/power.d/wireless
```
nothing we did should have made your wired connection stop working did you plug it back in after you rebooted?
Thanks

---

### Post by mariuszp on 2012-06-15
i meant i do not have a wired connection at all. It didn't stop working, i just don't use it. I only use the wifi.

---

### Post by mariuszp on 2012-06-15
Output from the commands:

```


mariusz@mariusz-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  ESSID:"O2wirelessF63A57"  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:26:44:F6:3A:57   
          Bit Rate=300 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management period:0us  mode:All packets received
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

mariusz@mariusz-laptop:~$ dmesg | egrep 'rtl|firm|radio|switch|wlan0'
[   23.108710] rtllib_crypt: registered algorithm 'NULL'
[   23.108713] rtllib_crypt: registered algorithm 'TKIP'
[   23.108716] rtllib_crypt: registered algorithm 'CCMP'
[   23.108718] rtllib_crypt: registered algorithm 'WEP'
[   23.108776] rtl819xSE 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   23.108783] rtl819xSE 0000:07:00.0: setting latency timer to 64
[   23.212390] rtl8192: wireless switch is on
[   27.443328] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   27.443335] ===>rtllib_start_scan()
[   27.443401] =====>rtl8192_set_chan()====ch:11
[   27.452215] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.503788] =====>rtl8192_set_chan()====ch:1
[   27.621950] =====>rtl8192_set_chan()====ch:2
[   27.741911] =====>rtl8192_set_chan()====ch:3
[   27.861894] =====>rtl8192_set_chan()====ch:4
[   27.981299] =====>rtl8192_set_chan()====ch:5
[   28.091282] =====>rtl8192_set_chan()====ch:6
[   28.201289] =====>rtl8192_set_chan()====ch:7
[   28.311289] =====>rtl8192_set_chan()====ch:8
[   28.421295] =====>rtl8192_set_chan()====ch:9
[   28.531340] =====>rtl8192_set_chan()====ch:10
[   28.641339] =====>rtl8192_set_chan()====ch:11
[   28.751346] =====>rtl8192_set_chan()====ch:12
[   28.861339] =====>rtl8192_set_chan()====ch:13
[   41.994282] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   41.994366] =====>rtl8192_set_chan()====ch:1
[   42.110045] =====>rtl8192_set_chan()====ch:2
[   42.240030] =====>rtl8192_set_chan()====ch:3
[   42.360183] =====>rtl8192_set_chan()====ch:4
[   42.470660] =====>rtl8192_set_chan()====ch:5
[   42.600658] =====>rtl8192_set_chan()====ch:6
[   42.720023] =====>rtl8192_set_chan()====ch:7
[   42.840648] =====>rtl8192_set_chan()====ch:8
[   42.950171] =====>rtl8192_set_chan()====ch:9
[   43.070111] =====>rtl8192_set_chan()====ch:10
[   43.190089] =====>rtl8192_set_chan()====ch:11
[   43.310042] =====>rtl8192_set_chan()====ch:12
[   43.430035] =====>rtl8192_set_chan()====ch:13
[   43.551015] ===>rtllib_start_scan()
[   43.551031] =====>rtl8192_set_chan()====ch:12
[   43.561148] ===>rtllib_associate_procedure_wq(), chan:11
[   43.561154] =====>rtl8192_set_chan()====ch:11
[   43.571355] ===>rtllib_associate_procedure_wq(), chan:11
[   43.571360] =====>rtl8192_set_chan()====ch:11
[   43.584769] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   43.590592] =====>rtl8192_set_chan()====ch:11
[   43.600707] ===>rtl8192se_link_change():ieee->iw_mode is 2
[   43.600715] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[   43.602395] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   48.227429] ===>rtl8192se_link_change():ieee->iw_mode is 2
[   48.280166] =====>rtl8192_set_chan()====ch:1
[   48.390063] =====>rtl8192_set_chan()====ch:2
[   48.500059] =====>rtl8192_set_chan()====ch:3
[   48.610088] =====>rtl8192_set_chan()====ch:4
[   48.720058] =====>rtl8192_set_chan()====ch:5
[   48.830060] =====>rtl8192_set_chan()====ch:6
[   48.940062] =====>rtl8192_set_chan()====ch:7
[   49.050039] =====>rtl8192_set_chan()====ch:8
[   49.160047] =====>rtl8192_set_chan()====ch:9
[   49.270069] =====>rtl8192_set_chan()====ch:10
[   49.380032] =====>rtl8192_set_chan()====ch:11
[   49.491297] =====>rtl8192_set_chan()====ch:12
[   49.600100] =====>rtl8192_set_chan()====ch:13
[   49.710057] =====>rtl8192_set_chan()====ch:11
[   49.718340] ===>rtl8192se_link_change():ieee->iw_mode is 2
[   49.718344] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[   88.227783] ===>rtl8192se_link_change():ieee->iw_mode is 2
[   88.280189] =====>rtl8192_set_chan()====ch:1
[   88.400057] =====>rtl8192_set_chan()====ch:2
[   88.520075] =====>rtl8192_set_chan()====ch:3
[   88.640068] =====>rtl8192_set_chan()====ch:4
[   88.760187] =====>rtl8192_set_chan()====ch:5
[   88.880062] =====>rtl8192_set_chan()====ch:6
[   89.000059] =====>rtl8192_set_chan()====ch:7
[   89.120078] =====>rtl8192_set_chan()====ch:8
[   89.245691] =====>rtl8192_set_chan()====ch:9
[   89.360061] =====>rtl8192_set_chan()====ch:10
[   89.480060] =====>rtl8192_set_chan()====ch:11
[   89.600064] =====>rtl8192_set_chan()====ch:12
[   89.720063] =====>rtl8192_set_chan()====ch:13
[   89.840057] =====>rtl8192_set_chan()====ch:11
[   89.850280] ===>rtl8192se_link_change():ieee->iw_mode is 2
[   89.850285] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  148.229566] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  148.280138] =====>rtl8192_set_chan()====ch:1
[  148.400781] =====>rtl8192_set_chan()====ch:2
[  148.520083] =====>rtl8192_set_chan()====ch:3
[  148.630699] =====>rtl8192_set_chan()====ch:4
[  148.750078] =====>rtl8192_set_chan()====ch:5
[  148.860655] =====>rtl8192_set_chan()====ch:6
[  148.980051] =====>rtl8192_set_chan()====ch:7
[  149.090697] =====>rtl8192_set_chan()====ch:8
[  149.210073] =====>rtl8192_set_chan()====ch:9
[  149.320661] =====>rtl8192_set_chan()====ch:10
[  149.440691] =====>rtl8192_set_chan()====ch:11
[  149.560690] =====>rtl8192_set_chan()====ch:12
[  149.680061] =====>rtl8192_set_chan()====ch:13
[  149.790076] =====>rtl8192_set_chan()====ch:11
[  149.800268] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  149.800277] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  228.230478] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  228.290117] =====>rtl8192_set_chan()====ch:1
[  228.400055] =====>rtl8192_set_chan()====ch:2
[  228.510099] =====>rtl8192_set_chan()====ch:3
[  228.620045] =====>rtl8192_set_chan()====ch:4
[  228.730681] =====>rtl8192_set_chan()====ch:5
[  228.850042] =====>rtl8192_set_chan()====ch:6
[  228.960054] =====>rtl8192_set_chan()====ch:7
[  229.070048] =====>rtl8192_set_chan()====ch:8
[  229.180073] =====>rtl8192_set_chan()====ch:9
[  229.300045] =====>rtl8192_set_chan()====ch:10
[  229.410042] =====>rtl8192_set_chan()====ch:11
[  229.530532] =====>rtl8192_set_chan()====ch:12
[  229.640046] =====>rtl8192_set_chan()====ch:13
[  229.750064] =====>rtl8192_set_chan()====ch:11
[  229.760258] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  229.760266] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  325.450338] ===>rtl819x_watchdog_wqcallback(): AP is power off,chan:11, connect another one
[  325.450733] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  325.551130] =====>rtl8192_set_chan()====ch:1
[  325.670066] =====>rtl8192_set_chan()====ch:2
[  325.780704] =====>rtl8192_set_chan()====ch:3
[  325.900057] =====>rtl8192_set_chan()====ch:4
[  326.020273] =====>rtl8192_set_chan()====ch:5
[  326.140064] =====>rtl8192_set_chan()====ch:6
[  326.260083] =====>rtl8192_set_chan()====ch:7
[  326.370103] =====>rtl8192_set_chan()====ch:8
[  326.490046] =====>rtl8192_set_chan()====ch:9
[  326.610036] =====>rtl8192_set_chan()====ch:10
[  326.730047] =====>rtl8192_set_chan()====ch:11
[  326.850061] =====>rtl8192_set_chan()====ch:12
[  326.970114] =====>rtl8192_set_chan()====ch:13
[  327.091518] ===>rtllib_associate_procedure_wq(), chan:11
[  327.091531] =====>rtl8192_set_chan()====ch:11
[  327.101765] ===>rtllib_associate_procedure_wq(), chan:11
[  327.101777] =====>rtl8192_set_chan()====ch:11
[  327.111976] ===>rtllib_associate_procedure_wq(), chan:11
[  327.111980] =====>rtl8192_set_chan()====ch:11
[  327.127088] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  327.133110] =====>rtl8192_set_chan()====ch:11
[  327.143239] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  327.143246] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  333.450473] ===>rtl819x_watchdog_wqcallback(): AP is power off,chan:11, connect another one
[  333.450489] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  333.551079] =====>rtl8192_set_chan()====ch:1
[  333.661366] =====>rtl8192_set_chan()====ch:2
[  333.770107] =====>rtl8192_set_chan()====ch:3
[  333.880048] =====>rtl8192_set_chan()====ch:4
[  333.991330] =====>rtl8192_set_chan()====ch:5
[  334.100046] =====>rtl8192_set_chan()====ch:6
[  334.210066] =====>rtl8192_set_chan()====ch:7
[  334.320068] =====>rtl8192_set_chan()====ch:8
[  334.431355] =====>rtl8192_set_chan()====ch:9
[  334.540071] =====>rtl8192_set_chan()====ch:10
[  334.650073] =====>rtl8192_set_chan()====ch:11
[  334.760069] =====>rtl8192_set_chan()====ch:12
[  334.880062] =====>rtl8192_set_chan()====ch:13
[  335.001634] ===>rtllib_associate_procedure_wq(), chan:11
[  335.001647] =====>rtl8192_set_chan()====ch:11
[  335.011966] ===>rtllib_associate_procedure_wq(), chan:11
[  335.011975] =====>rtl8192_set_chan()====ch:11
[  335.022154] ===>rtllib_associate_procedure_wq(), chan:11
[  335.022162] =====>rtl8192_set_chan()====ch:11
[  335.036266] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  335.043648] =====>rtl8192_set_chan()====ch:11
[  335.053777] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  335.053784] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  339.451756] ===>rtl819x_watchdog_wqcallback(): AP is power off,chan:11, connect another one
[  339.451777] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  339.552461] =====>rtl8192_set_chan()====ch:1
[  339.670689] =====>rtl8192_set_chan()====ch:2
[  339.790714] =====>rtl8192_set_chan()====ch:3
[  339.910677] =====>rtl8192_set_chan()====ch:4
[  340.030696] =====>rtl8192_set_chan()====ch:5
[  340.150067] =====>rtl8192_set_chan()====ch:6
[  340.260688] =====>rtl8192_set_chan()====ch:7
[  340.380078] =====>rtl8192_set_chan()====ch:8
[  340.490788] =====>rtl8192_set_chan()====ch:9
[  340.610687] =====>rtl8192_set_chan()====ch:10
[  340.730045] =====>rtl8192_set_chan()====ch:11
[  340.840740] =====>rtl8192_set_chan()====ch:12
[  340.967453] =====>rtl8192_set_chan()====ch:13
[  341.081539] ===>rtllib_associate_procedure_wq(), chan:11
[  341.081553] =====>rtl8192_set_chan()====ch:11
[  341.091790] ===>rtllib_associate_procedure_wq(), chan:11
[  341.091861] =====>rtl8192_set_chan()====ch:11
[  341.102334] ===>rtllib_associate_procedure_wq(), chan:11
[  341.102347] =====>rtl8192_set_chan()====ch:11
[  341.114354] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  341.121497] =====>rtl8192_set_chan()====ch:11
[  341.129699] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  341.129709] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  355.984302] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  356.063575] =====>rtl8192_set_chan()====ch:1
[  356.180074] =====>rtl8192_set_chan()====ch:2
[  356.290527] =====>rtl8192_set_chan()====ch:3
[  356.410066] =====>rtl8192_set_chan()====ch:4
[  356.531225] =====>rtl8192_set_chan()====ch:5
[  356.650080] =====>rtl8192_set_chan()====ch:6
[  356.775662] =====>rtl8192_set_chan()====ch:7
[  356.890347] =====>rtl8192_set_chan()====ch:8
[  357.010057] =====>rtl8192_set_chan()====ch:9
[  357.130073] =====>rtl8192_set_chan()====ch:10
[  357.250040] =====>rtl8192_set_chan()====ch:11
[  357.370065] =====>rtl8192_set_chan()====ch:12
[  357.490069] =====>rtl8192_set_chan()====ch:13
[  357.611420] ===>rtllib_start_scan()
[  357.611449] =====>rtl8192_set_chan()====ch:12
[  357.621825] ===>rtllib_associate_procedure_wq(), chan:11
[  357.621838] =====>rtl8192_set_chan()====ch:11
[  357.635183] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  357.638886] =====>rtl8192_set_chan()====ch:11
[  357.649016] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  357.649021] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  361.493666] rtllib: TsStartAddBaProcess()==>BA timer is already added
mariusz@mariusz-laptop:~$ lsmod | grep -e rtl -e iwl
mariusz@mariusz-laptop:~$ 

```

The /etc/pm/power.d/wireless file:

```

#!/bin/sh

/sbin/iwconfig wlan0 power off

```

---

### Post by wildmanne39 on 2012-06-15
Hi, please try:
```
sudo ifconfig wlan0 down
sudo rmmod -f r8192se_pci
sudo modprobe r8192se_pci hwwep=0
sudo ifconfig wlan0 up

```
do not reboot after running the commands if it works we will need to make it permanent.

Your link quality is 10 which is to low to connect it may go up when you run this command, but make sure for testing that you are close to your wireless router.

Also you have an ESSID and a NICKNAME did you set it up that way?
Thanks

---

### Post by mariuszp on 2012-06-15
Running those commands changed nothing. Also, when i ran the modprobe, 2 times in a row the system completely crashed and i had to disconnect the power.

The ESSID was set up and it is correct, by i did not set up any "NICKNAME".

---

### Post by wildmanne39 on 2012-06-15
Hi, please post the output from:
```
dmesg | egrep 'r81|firm|radio|switch|wlan0'
nm-tool
```
```
lsmod | grep -e r81 -e iwl
```
```
ndiswrapper -l
cat /var/lib/NetworkManager/NetworkManager.state
cat /etc/resolv.conf
```
Thanks

---

### Post by mariuszp on 2012-06-16
Output:

```


mariusz@mariusz-laptop:~$ dmesg | egrep 'r81|firm|radio|switch|wlan0'
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u262144
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u262144 alloc=1*2097152
[    1.158540] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.158590] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.158678] r8169 0000:02:00.0: setting latency timer to 64
[    1.158689] r8169 0000:02:00.0: (unregistered net_device): unknown MAC, using family default
[    1.158777] r8169 0000:02:00.0: irq 46 for MSI/MSI-X
[    1.159472] r8169 0000:02:00.0: eth0: RTL8101e at 0xffffc9000067c000, 88:ae:1d:48:cf:2c, XID 0c200000 IRQ 46
[   22.759553] rtl8192: wireless switch is on
[   25.949532] r8169 0000:02:00.0: eth0: link down
[   26.121484] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.760330] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
mariusz@mariusz-laptop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        88:AE:1D:48:CF:2C

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0  [Auto O2wirelessF63A57] ---------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl819xSE
  State:             connected
  Default:           yes
  HW Address:        00:26:4D:D9:3C:E7

  Capabilities:
    Speed:           135 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    BTHomeHub2-CZ7F: Infra, 00:24:17:F5:96:4B, Freq 2442 MHz, Rate 2 Mb/s, Strength 47 WPA WPA2
    BTFON:           Infra, 02:24:17:EF:0C:2D, Freq 2442 MHz, Rate 2 Mb/s, Strength 47
    BTHomeHub2-3FQ8: Infra, 00:24:17:EF:0C:2B, Freq 2442 MHz, Rate 2 Mb/s, Strength 47 WPA WPA2
    BTHub3-2XQZ:     Infra, 10:C6:1F:AC:12:53, Freq 2412 MHz, Rate 16 Mb/s, Strength 50 WPA WPA2
    Orange2275fe:    Infra, E0:46:9A:05:C8:00, Freq 2462 MHz, Rate 22 Mb/s, Strength 47 WPA WPA2
    BTFON:           Infra, 02:24:17:F5:96:4D, Freq 2442 MHz, Rate 2 Mb/s, Strength 47
    *O2wirelessF63A57: Infra, 00:26:44:F6:3A:57, Freq 2462 MHz, Rate 2 Mb/s, Strength 79 WPA WPA2
    BTOpenzone-H:    Infra, 92:C6:1F:AC:12:54, Freq 2412 MHz, Rate 16 Mb/s, Strength 59
    BTFON:           Infra, 92:C6:1F:AC:12:55, Freq 2412 MHz, Rate 16 Mb/s, Strength 47
    BTFON:           Infra, 12:FE:F4:49:EF:18, Freq 2412 MHz, Rate 16 Mb/s, Strength 53
    BTOpenzone-H:    Infra, 02:FE:F4:49:EF:18, Freq 2412 MHz, Rate 16 Mb/s, Strength 66
    BTOpenzone-H:    Infra, 02:24:17:EF:0C:2C, Freq 2442 MHz, Rate 2 Mb/s, Strength 47
    BTHub3-8C6M:     Infra, 00:FE:F4:49:EF:18, Freq 2412 MHz, Rate 16 Mb/s, Strength 47 WPA WPA2
    SKY1A3A2:        Infra, 4C:17:EB:51:A3:A3, Freq 2437 MHz, Rate 16 Mb/s, Strength 47 WPA WPA2
    HistR:           Infra, 00:50:7F:71:2A:C0, Freq 2437 MHz, Rate 44 Mb/s, Strength 56 WPA
    TALKTALK-7CDB2C: Infra, 00:26:5A:7C:DB:2C, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    flynn135:        Infra, 00:22:B0:E9:86:9B, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    virginbroadband1:Infra, 1C:BD:B9:82:3C:F2, Freq 2437 MHz, Rate 54 Mb/s, Strength 59 WPA
    SKY08122:        Infra, 00:1F:33:7C:6B:84, Freq 2437 MHz, Rate 54 Mb/s, Strength 81 WPA
    SKY86917:        Infra, F0:7D:68:6E:5E:D7, Freq 2462 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.64
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             8.8.8.8
    DNS:             8.8.4.4


mariusz@mariusz-laptop:~$ lsmod | grep -e r81 -e iwl
r8192se_pci           512896  0 
cfg80211              170485  1 r8192se_pci
r8169                  42254  0 
mii                     5261  1 r8169
mariusz@mariusz-laptop:~$ ndiswrapper -l
Program ndiswrapper nie jest obecnie zainstalowany.  Mo&#380;na go zainstalowa&#263; wpisuj&#261;c:
sudo apt-get install ndiswrapper-common
mariusz@mariusz-laptop:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false
mariusz@mariusz-laptop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 8.8.8.8
nameserver 8.8.4.4
mariusz@mariusz-laptop:~$ 

```

It says that ndiswrapper is currently not installed.

---

### Post by wildmanne39 on 2012-06-16
Hi, good I am glad ndiswrapper is not installed I was just checking, please do:
```
gksu gedit /var/lib/NetworkManager/NetworkManager.state
```
change the one that says [COLOR="Red"]false to true[/COLOR] then save gedit, close and reboot.
Is the slow down the same since you blacklisted the 
iwlagn driver with your ethernet disconnected?

Did you have an intel device that you took out if so why? we could probably make it work better then the one you are using.
Thanks

---

### Post by wildmanne39 on 2012-06-16
Hi, I also recommend that you change channels try one or 11 change it in the router settings and change encryption while in the router to just wpa2 if possible it usually works better and change the N speed to just b/g it usually improves stability.
Thanks

---

### Post by mariuszp on 2012-06-16
Changing that value from false to true did not change the speed problem, and the slowdown is still the same after blacklisting that driver. I did not take out or put in any device because i have a laptop so it's not really possible.

---

### Post by mariuszp on 2012-06-16
I would also like to point out:

I realised that if I set up the WiFi on my phone (which is an android, and android is linux), and get it to emulate a router, then i can plug it in via USB and ubuntu sees it as a wired connection and the internet works perfectly!

---

### Post by wildmanne39 on 2012-06-16
Hi, I am afraid I am out out ideas, if you do not want to upgrade you can always use 10.04 it is supported until April 2013 and it is more stable then 10.10.
Thanks

---

### Post by mariuszp on 2012-06-17
Since I can get fast internet via my phone, i guess I could update now. Thanks for help.

---

### Post by wildmanne39 on 2012-06-17
Hi, your welcome!!! just created a livecd or liveusb of ubuntu then backing up your important data and doing a clean install of 12.04 will be much faster and lot less likely to have issues after you are done because there are a lot of differences between 10.10 and 12.04.

Sorry I could not find a better way.

---

