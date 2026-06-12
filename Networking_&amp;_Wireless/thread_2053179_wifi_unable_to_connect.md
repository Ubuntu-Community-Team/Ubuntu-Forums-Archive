---
title: "wifi unable to connect"
date: 2012-09-04
forum: Networking &amp; Wireless
---

### Post by dyneshqmar on 2012-09-04
Hello there,
I have a dell vostro 1014 Laptop, which runs a ubuntu 12.04. My wireless is enabled, but the LED doesnt glow and its also unable to find the connections nearby. When i was trying to sort out this issue with RTC, someone told me that it is an "rfkill soft-off" issue. Previously, someone told me that there are many interfaces created which is creating a problem for wifi. i am not sure, what that meant. Anyway, thats all i know about the problem. my wireless driver is an AR9285, by Atheros Communication Inc. Help me out guys!!

---

### Post by chili555 on 2012-09-06
Please open a terminal and run and post:```
lspci -nn | grep 0280
rfkill list all
dmesg | grep ath9
```Thanks.

---

### Post by dyneshqmar on 2012-09-10
bravo@Roy-PC:~$ lspci -nn | grep 0280
0c:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
bravo@Roy-PC:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: dell-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
bravo@Roy-PC:~$ dmesg | grep ath9

---

### Post by chili555 on 2012-09-10
> bravo@Roy-PC:~$ dmesg | grep ath9Fascinating.

Let's kick it a bit harder. Please run and post:```
sudo modprobe ath9k
dmesg | grep ath9
iwconfig
```>  someone told me that it is an "rfkill soft-off" issue. Previously, someone told me that there are many interfaces created which is creating a problem for wifi. i am not sure, what that meant.It means a lot of people really don't know much.

Other than the fact that the driver ath9k isn't loading on boot, so far, we see nothing unusual.

---

### Post by dyneshqmar on 2012-09-11
```
bravo@Roy-PC:~$ sudo modprobe ath9k
[sudo] password for bravo: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ath9k.conf.save, it will be ignored in a future release.
bravo@Roy-PC:~$ dmesg | grep ath9
[ 1452.965130] ath9k 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 1452.965145] ath9k 0000:0c:00.0: setting latency timer to 64
[ 1453.074186] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[ 1453.074927] Registered led device: ath9k-phy0
bravo@Roy-PC:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.
```

Thank you!

---

### Post by chili555 on 2012-09-11
Hmmm, somebody has been busy! Let's unravel things. Please let me see:```
cat /etc/modprobe.d/blacklist
cat /etc/modprobe.d/ath9k.conf.save
cat /etc/modprobe.d/ath9k.conf
```Let's fix those problems before we proceed.

---

### Post by dyneshqmar on 2012-09-11
```
bravo@Roy-PC:~$ cat /etc/modprobe.d/blacklist

#Remove To Install MadWIFI Drivers
blacklist ath9k
blacklist ath5k

#Remove To Install MadWIFI Drivers
blacklist ath9k
blacklist ath5k
bravo@Roy-PC:~$ cat /etc/modprobe.d/ath9k.conf.save
cat: /etc/modprobe.d/ath9k.conf.save: Permission denied
bravo@Roy-PC:~$ cat /etc/modprobe.d/ath9k.conf
cat: /etc/modprobe.d/ath9k.conf: No such file or directory
bravo@Roy-PC:~$
```

---

### Post by dyneshqmar on 2012-09-11
and this MadWIFI thing was also suggested by some one. it didn't work either. I've been tied up with my wired connection on my laptop all day! relieve me brother! thank you!

---

### Post by chili555 on 2012-09-11
> bravo@Roy-PC:~$ cat /etc/modprobe.d/blacklist

#Remove To Install MadWIFI Drivers
blacklist ath9k
blacklist ath5k

#Remove To Install MadWIFI Drivers
blacklist ath9k
blacklist ath5kFascinating. Did you try to install Madwifi? It seems that the driver you need is blacklisted, unless, of course, you've tried some other drivers. > bravo@Roy-PC:~$ cat /etc/modprobe.d/ath9k.conf.save
cat: /etc/modprobe.d/ath9k.conf.save: Permission deniedEven more fascinating! How about:```
sudo cat /etc/modprobe.d/ath9k.conf.save
```

---

### Post by dyneshqmar on 2012-09-11
```
bravo@Roy-PC:~$ sudo cat /etc/modprobe.d/ath9k.conf.save
[sudo] password for bravo: 
options ath9k nohwcrypt=1
bravo@Roy-PC:~$ 
```

---

### Post by chili555 on 2012-09-11
All right, let's do some housekeeping. Please do:```
sudo mv /etc/modprobe.d/ath9k.conf.save /etc/modprobe.d/ath9k.conf
sudo chmod +r /etc/modprobe.d/*
sudo rm /etc/modprobe.d/blacklist
```Now reboot so we have a clean slate and tell me what the wireless is doing. Include:```
sudo iwlist wlan0 scan
```Thanks.

---

### Post by dyneshqmar on 2012-09-11
```
bravo@Roy-PC:~$ sudo iwlist wlan0 scan
[sudo] password for bravo: 
wlan0     Interface doesn't support scanning.
```

hope we have another problem!!

---

### Post by dyneshqmar on 2012-09-11
and moreover, i just noticed this after 3 or 4 days that, the enable wireless option is not there anymore in the network settings!!!

---

### Post by chili555 on 2012-09-11
> **dyneshqmar said:**
> and moreover, i just noticed this after 3 or 4 days that, the enable wireless option is not there anymore in the network settings!!!Please post:```
sudo modprobe ath9k
iwconfig
dmesg | grep ath9
```Thanks.

---

### Post by dyneshqmar on 2012-09-12
```
bravo@Roy-PC:~$ sudo modprobe ath9k
[sudo] password for bravo: 
bravo@Roy-PC:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

bravo@Roy-PC:~$ dmesg | grep ath9
[  216.157124] ath9k 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  216.157139] ath9k 0000:0c:00.0: setting latency timer to 64
[  216.267074] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[  216.268076] Registered led device: ath9k-phy0

```

---

### Post by chili555 on 2012-09-12
We see the timestamp tells us that the driver ath9k didn't load on boot. It probably only loaded it when you just now loaded it. That suggests it's still, in some way, blacklisted. Let's see:```
ls /etc/modprobe.d
cat /etc/modprobe.d/blacklist.conf
cat /etc/modules
```Does it scan?```
sudo modprobe ath9k
sudo iwlist wlan0 scan
```

---

### Post by dyneshqmar on 2012-09-12
```
bravo@Roy-PC:~$ ls /etc/modprobe.d
alsa-base.conf               blacklist-firewire.conf      dkms.conf
ath9k.conf                   blacklist-framebuffer.conf   libpisock9.conf
blacklist-ath_pci.conf       blacklist-modem.conf         ndiswrapper.conf
blacklist-bcm43.conf         blacklist-oss.conf           oss-compat.conf
blacklist-berry_charge.conf  blacklist-rare-network.conf  vmwgfx-fbdev.conf
blacklist.conf               blacklist-watchdog.conf
bravo@Roy-PC:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
bravo@Roy-PC:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
ath_pci
ath_pci
bravo@Roy-PC:~$ sudo modprobe ath9k
[sudo] password for bravo: 
bravo@Roy-PC:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down

```

it still doesnt scan.

---

### Post by chili555 on 2012-09-12
> bravo@Roy-PC:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
[COLOR="Red"]ath_pci
ath_pci[/COLOR]Your /etc/modules asks that the module ath_pci be loaded on boot...twice. However, in 12.04, > $ modinfo ath_pci
ERROR: modinfo: [COLOR="Red"]could not find module ath_pci[/COLOR]Is that something you built as part of the Madwifi suite? You may as well do:```
sudo gedit /etc/modules
```Remove both the ath_pci lines; proofread, save and close gedit.

Let's also take a look at this:```
cat /etc/modprobe.d/blacklist-ath_pci.conf
```And this:```
lsmod
```Thanks.

---

### Post by dyneshqmar on 2012-09-12
```
bravo@Roy-PC:~$ cat /etc/modprobe.d/blacklist-ath_pci.conf
# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath_pci

bravo@Roy-PC:~$ lsmod
Module                  Size  Used by
arc4                   12473  2 
ath9k                 117425  0 
mac80211              436455  1 ath9k
ath9k_common           13781  1 ath9k
ath9k_hw              391554  2 ath9k,ath9k_common
ath                    19387  3 ath9k,ath9k_common,ath9k_hw
cfg80211              178679  3 ath9k,mac80211,ath
rfcomm                 38139  12 
bnep                   17830  2 
joydev                 17393  0 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_hda_codec_conexant    52554  1 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
snd_hda_intel          32765  4 
snd_hda_codec         109562  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
mac_hid                13077  0 
snd_timer              28931  2 snd_pcm,snd_seq
i915                  414939  3 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         45466  1 i915
uvcvideo               67203  0 
ath3k                  12825  0 
psmouse                96619  0 
wmi                    18744  1 dell_wmi
drm                   197692  4 i915,drm_kms_helper
videodev               86588  1 uvcvideo
snd                    62064  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
btusb                  17912  2 
bluetooth             158438  24 rfcomm,bnep,ath3k,btusb
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
serio_raw              13027  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40180  0 
r8169                  56321  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci

```

Thanks.

---

### Post by chili555 on 2012-09-13
> bravo@Roy-PC:~$ cat /etc/modprobe.d/blacklist-ath_pci.conf
# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath_pci
So, the non-existent module we loaded twice is also blacklisted! Please do:```
sudo rm /etc/modprobe.d/blacklist-ath_pci.conf
```Also, please do:```
sudo gedit /etc/modprobe.d/ath9k.conf
```Change the file from this:```
options ath9k nohwcrypt=1
```...to this:```
options ath9k btcoex_enable=1
```Proofread, save and close gedit. Reboot and show us:```
sudo iwlist wlan0 scan
iwconfig
sudo cat /var/log/syslog | grep etwork |tail -n15
```Thanks.

---

### Post by dyneshqmar on 2012-09-13
```
bravo@Roy-PC:~$ sudo iwlist wlan0 scan
[sudo] password for bravo: 
wlan0     Interface doesn't support scanning.

bravo@Roy-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

bravo@Roy-PC:~$ sudo cat /var/log/syslog | grep etwork |tail -n15
Sep 13 19:47:31 Roy-PC NetworkManager[776]: <info>   hostname 'dhcppc1'
Sep 13 19:47:31 Roy-PC NetworkManager[776]: <info>   nameserver '59.179.243.70'
Sep 13 19:47:31 Roy-PC NetworkManager[776]: <info>   nameserver '203.94.243.70'
Sep 13 19:47:31 Roy-PC NetworkManager[776]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Sep 13 19:47:31 Roy-PC NetworkManager[776]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Sep 13 19:47:32 Roy-PC NetworkManager[776]: <info> DNS: starting dnsmasq...
Sep 13 19:47:32 Roy-PC NetworkManager[776]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Sep 13 19:47:34 Roy-PC NetworkManager[776]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Sep 13 19:47:34 Roy-PC NetworkManager[776]: <info> Policy set 'Auto Ethernet' (eth0) as default for IPv4 routing and DNS.
Sep 13 19:47:34 Roy-PC NetworkManager[776]: <info> Activation (eth0) successful, device activated.
Sep 13 19:47:34 Roy-PC NetworkManager[776]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Sep 13 19:47:51 Roy-PC NetworkManager[776]: <info> (eth0): IP6 addrconf timed out or failed.
Sep 13 19:47:51 Roy-PC NetworkManager[776]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Sep 13 19:47:51 Roy-PC NetworkManager[776]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Sep 13 19:47:51 Roy-PC NetworkManager[776]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
bravo@Roy-PC:~$ 

```

thanks

---

### Post by chili555 on 2012-09-13
A perfect example of the wired ethernet connecting. Let's dig deeper. Is the module loaded?```
lsmod | grep ath
```If not, load it, while we wonder why it doesn't load automatically:```
sudo modprobe ath9k
```Now detach the ethernet cable and let us see:```
iwconfig
sudo iwlist wlan0 scan
```

---

### Post by dyneshqmar on 2012-09-13
```
lsmobravo@Roy-PC:~$ lsmod | grep ath
ath3k                  12825  0 
bluetooth             158438  24 rfcomm,bnep,ath3k,btusb
bravo@Roy-PC:~$ sudo modprobe ath9k
[sudo] password for bravo: 
bravo@Roy-PC:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

bravo@Roy-PC:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 80:A1:D7:1F:7F:B0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"MTNL k-290"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000ce2bfd52
                    Extra: Last beacon: 996ms ago
                    IE: Unknown: 000A4D544E4C206B2D323930
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500011B7A12
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706545720010B10
                    IE: Unknown: DD1E00904C336E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401050700000000000000000000000000000000000000
          Cell 02 - Address: 00:1E:40:D3:C6:74
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Sky"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001f69fe189
                    Extra: Last beacon: 1012ms ago
                    IE: Unknown: 0003536B79
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180200F4
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:25:5E:C6:10:B9
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001c2167ee20d
                    Extra: Last beacon: 944ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 04 - Address: 94:D7:23:08:CB:E0
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"MTNL  k 204"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006df57b3161
                    Extra: Last beacon: 724ms ago
                    IE: Unknown: 000B4D544E4C20206B20323034
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706545700010B10
          Cell 05 - Address: 00:19:BE:80:70:C4
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"Mili"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002ddf3cc181
                    Extra: Last beacon: 884ms ago
                    IE: Unknown: 00044D696C69
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
          Cell 06 - Address: 06:19:BE:80:70:C4
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"MHC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002ddf3cc6f2
                    Extra: Last beacon: 884ms ago
                    IE: Unknown: 00034D4843
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
          Cell 07 - Address: 00:1B:2F:5E:55:60
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"home"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000541a95376
                    Extra: Last beacon: 712ms ago
                    IE: Unknown: 0004686F6D65
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: 00:1E:40:83:AD:14
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"ranjit"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000005d0d7c21a
                    Extra: Last beacon: 712ms ago
                    IE: Unknown: 000672616E6A6974
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180202F4
          Cell 09 - Address: 00:1E:40:19:04:80
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"Charvi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000022474cc89
                    Extra: Last beacon: 712ms ago
                    IE: Unknown: 0006436861727669
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020014
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: 00:25:5E:C3:34:B8
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"oberoi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c3389fe4c
                    Extra: Last beacon: 340ms ago
                    IE: Unknown: 00066F6265726F69
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 11 - Address: 00:25:5E:C3:34:B9
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c338a024d
                    Extra: Last beacon: 340ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 12 - Address: 00:25:5E:C3:34:BA
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c33887556
                    Extra: Last beacon: 440ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 13 - Address: 00:25:5E:C3:34:BB
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c33887867
                    Extra: Last beacon: 440ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 14 - Address: 00:1E:40:40:F8:B1
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"Desi boys K-289"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000018638e9fa
                    Extra: Last beacon: 432ms ago
                    IE: Unknown: 000F4465736920626F7973204B2D323839
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180202F4
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: 00:30:1A:33:3F:96
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"SaritaMBST_116"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000013881f3
                    Extra: Last beacon: 256ms ago
                    IE: Unknown: 000E5361726974614D4253545F313136
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010D
                    IE: Unknown: 07064E4C20010D14
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD070050F202000100
                    IE: Unknown: FB0753423332313200
                    IE: Unknown: 050700010000000000
          Cell 16 - Address: 00:40:0C:04:1A:D1
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000138899b
                    Extra: Last beacon: 252ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010D
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C

```

i hope its scanning now.

---

### Post by chili555 on 2012-09-13
It is scanning now. However, this is the strongest network we see:> Quality=[COLOR="Red"]33/70[/COLOR] I suspect that's a factor in not getting a connection. Is your own router or network in there somewhere?

Let's get ath9k to load on boot:```
sudo su
echo ath9k >> /etc/modules
exit
```

---

### Post by dyneshqmar on 2012-09-13
though that is the strongest we can see, the following is my router's,

> Cell 04 - Address: 94:D7:23:08:CB:E0
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    [COLOR=Red]ESSID:"MTNL  k 204"[/COLOR]
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006df57b3161
                    Extra: Last beacon: 724ms ago
                    IE: Unknown: 000B4D544E4C20206B20323034
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706545700010B10now, my wifi LED glows but still its unable to detect networks..should i reboot and try?

---

### Post by dyneshqmar on 2012-09-13
i just rebooted my system, and now the LED doesnt glow, but the "enable wireless" option is available and is tick marked. But still it doesnt detect any networks

---

### Post by dyneshqmar on 2012-09-16
Whatssup??? no reply??? no clue?? should i re-install??

---

### Post by chili555 on 2012-09-16
We wonder why networks are not showing even though the devices scans and sees your network. Have you added any special settings in Network Manager? Is it set to Infrastructure? All settings should be removed. Please see attached.

Sorry for the delay. I undertook a slight change of scenery.

---

### Post by dyneshqmar on 2012-09-17
I donot have any wireless connections presently and more over, i very well remember that its not in infrastructure mode. And now the condition in my PC is that, the LED for wireless glows sometimes. This gives some hope to me. may be im wrong! but still, there should be a way out. I checked etc/networks/ there are 3 interfaces there which i created under the guidance of someone in RTC. May thats an issue..

---

### Post by chili555 on 2012-09-17
>  i very well remember that its not in infrastructure mode.Then please change it.>  I checked etc/networks/ there are 3 interfaces there which i created under the guidance of someone in RTC. May thats an issue.. For Network Manager to work well, only this should appear:```
auto lo
iface lo inet loopback
```Please change it.

---

### Post by dyneshqmar on 2012-09-18
i do not know how to change it, as i dont have any wireless connection now. and this is how, the network folder looks like.

[IMG]http://i50.tinypic.com/oh8fwm.png[/IMG]

what to do now?

---

### Post by chili555 on 2012-09-19
Please do:```
sudo gedit /etc/network/interfaces
```When the file opens, change it as I indicated above. Proofread, save and close gedit. Reboot.

---

### Post by dyneshqmar on 2012-09-19
I just opened, and its like

> auto lo
iface lo inet loopback
iface wlan0 inet static
address 192.168.1.99
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8

should i delete the rest of it and save?

sorry for bugging too much but im a beginner..cant help! :-\

---

### Post by chili555 on 2012-09-19
> should i delete the rest of it and save?Yes. It would never, ever have connected as written. When you are done, you want only: ```
auto lo  
iface lo inet loopback
```

---

### Post by dyneshqmar on 2012-09-20
Its working now. Thank you so much. I would like to learn troubleshooting in ubuntu so that i may be able to help others in this forum like you did to me. Is there any site or book available where i can learn??

Anyway, thanks a to..im connected to the wireless now! :)

---

### Post by chili555 on 2012-09-20
Awesome! I'm very glad it's working. 

I know there are many books about Ubuntu generally but I'm not sure there is a trouble-shooting book. Maybe I should write one!!

I just read posts and learn from others. I Google warning and error messages. I experiment on an old laptop I have. Gradually, over many years, I've learned more and more. 

Please use thread tools at the top to mark Solved.

---

### Post by dyneshqmar on 2012-09-20
Yep..ll do it. Nice knowing u by the way :)

---

### Post by ortermagic on 2012-10-10
Thank you very much chilli555, oddly I had almost the same problem as the OP, you were able to open my eyes too. Good walkthrough.

---

### Post by ALinuxWindowsBalance on 2012-10-10
Maybe you can help me??
[http://ubuntuforums.org/showthread.php?t=2069241&highlight=Driver+Frustration](http://ubuntuforums.org/showthread.php?t=2069241&highlight=Driver+Frustration)

---

