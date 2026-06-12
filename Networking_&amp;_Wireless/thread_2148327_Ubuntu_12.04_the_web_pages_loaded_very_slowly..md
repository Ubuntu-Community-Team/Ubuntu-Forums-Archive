---
title: "Ubuntu 12.04 the web pages loaded very slowly."
date: 2013-05-24
forum: Networking &amp; Wireless
---

### Post by andreic9203 on 2013-05-24
Hello,
Firstly, I want to excuse me for my bad english.


My problem is:
A few days ago, I installed Ubuntu 12.04.
At the beggining, my wireless connection doesn't worked at all.
I digged the internet (on a wired network), and I resolve the problem.
Now, the problem is different, when I want to open a web page, this is slowly loaded, or it don't load.
I tried all the solutions on this forum, on the another forums, but with no successful result.


If anyone can help me, I'll be very grateful.


Thanks.

---

### Post by praseodym on 2013-05-24
Hi,

check if IPv6 is set to "Ignore" in the network-manager applet for your wireless profile

---

### Post by andreic9203 on 2013-05-25
> **praseodym said:**
> Hi,

check if IPv6 is set to "Ignore" in the network-manager applet for your wireless profile

Yes, is on 'Ignore', but is set like this because I set it.
What I need to do, put on Ignore, or on another setting?

---

### Post by praseodym on 2013-05-25
Yes, ignore is good. Try these nameservers:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by andreic9203 on 2013-05-26
> **praseodym said:**
> Yes, ignore is good. Try these nameservers:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart
```


Ok, thank you for the reply.
Seems that is a little better, but not enough. Very strange behaviour... 
If I can help you with some commands results on which you can diagnose the problem, please tell me.

---

### Post by praseodym on 2013-05-26
Lets see:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
route -n
ifconfig -a
```

---

### Post by andreic9203 on 2013-05-27
> **praseodym said:**
> Lets see:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
route -n
ifconfig -a
```

Sorry for the delayed answer but my ISP was down.

```

lspci -nnk | grep -iA2 net

```
```

12:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Dell Inspiron M5010 / XPS 8300 [1028:0010]
    Kernel driver in use: bcma-pci-bridge
--
13:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Dell Device [1028:0447]
    Kernel driver in use: r8169



```
```

lsusb

```
```

Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 09da:054f A4 Tech Co., Ltd 
Bus 001 Device 004: ID 0c45:6480 Microdia Sonix 1.3 MP Laptop Integrated Webcam
Bus 002 Device 003: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 002 Device 005: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 006: ID 05ac:0250 Apple, Inc. 
Bus 002 Device 007: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 002 Device 008: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 002 Device 009: ID 413c:8160 Dell Computer Corp. Wireless 365 Bluetooth



```
```

lsmod

```
```

Module                  Size  Used by
rfcomm                 47562  0 
bnep                   18240  2 
parport_pc             32867  0 
ppdev                  17114  0 
arc4                   12530  2 
coretemp               13642  0 
snd_hda_codec_idt      70774  1 
btusb                  22432  0 
bluetooth             211812  14 rfcomm,bnep,btusb
brcmsmac              541775  0 
mac80211              555272  1 brcmsmac
brcmutil               14756  1 brcmsmac
dell_wmi               12682  0 
cfg80211              208382  2 brcmsmac,mac80211
cordic                 12575  1 brcmsmac
sparse_keymap          13891  1 dell_wmi
snd_hda_intel          34063  3 
snd_hda_codec         135141  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
dell_laptop            17426  0 
dcdbas                 14491  1 dell_laptop
snd_seq_midi_event     14900  1 snd_seq_midi
video                  19653  0 
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    19257  1 dell_wmi
snd                    83674  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse               102075  0 
serio_raw              13216  0 
hid_apple              13376  0 
microcode              23030  0 
radeon                917824  3 
ttm                    88495  1 radeon
drm_kms_helper         49259  1 radeon
uvcvideo               78117  0 
videobuf2_core         33025  1 uvcvideo
drm                   290344  5 radeon,ttm,drm_kms_helper
soundcore              15092  1 snd
videodev              125126  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
joydev                 17694  0 
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
mac_hid                13254  0 
videobuf2_memops       13405  1 videobuf2_vmalloc
i2c_algo_bit           13565  1 radeon
bcma                   35762  1 brcmsmac
lpc_ich                17145  0 
mei                    41410  0 
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
ums_realtek            18257  0 
usb_storage            49288  1 ums_realtek
hid_generic            12541  0 
usbhid                 47259  0 
hid                   100815  3 hid_apple,hid_generic,usbhid
ahci                   25869  4 
libahci                27338  1 ahci
r8169                  62766  0 

```
```

iwconfig

```
```

eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"WI-FI_CONN"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:22:B0:A2:0C:66   
          Bit Rate=54 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:72   Missed beacon:0



```
```

route -n

```
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0



```
```

ifconfig -a

```
```

eth0      Link encap:Ethernet  HWaddr f0:4d:a2:cd:95:4f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:235 errors:0 dropped:0 overruns:0 frame:0
          TX packets:235 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:41299 (41.2 KB)  TX bytes:41299 (41.2 KB)


wlan0     Link encap:Ethernet  HWaddr c0:cb:38:87:ba:32  
          inet addr:192.168.0.119  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::c2cb:38ff:fe87:ba32/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2890 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1380 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1480349 (1.4 MB)  TX bytes:414531 (414.5 KB)



```

Sorry again for the delay, and thank you for helping me.

---

### Post by praseodym on 2013-05-27
Update the driver via the package "linux-backports-modules-cw-3.6-generic" (or "generic-pae" depending on your kernel) and the firmware:
```

wget media.cdn.ubuntu-de.org/forum/attachments/56/18/5007272-Broadcom_Firmware_070513.tar.gz
sudo tar xvf 5007272-Broadcom_Firmware_070513.tar.gz -C /lib/firmware 
```
Shutdown without any current source for 10 minutes and restart

---

### Post by andreic9203 on 2013-05-29
> **praseodym said:**
> Update the driver via the package "linux-backports-modules-cw-3.6-generic" (or "generic-pae" depending on your kernel) and the firmware:
```

wget media.cdn.ubuntu-de.org/forum/attachments/56/18/5007272-Broadcom_Firmware_070513.tar.gz
sudo tar xvf 5007272-Broadcom_Firmware_070513.tar.gz -C /lib/firmware 
```
Shutdown without any current source for 10 minutes and restart

I'm done that, but no result... 
Any idea? :(

---

### Post by praseodym on 2013-05-29
Check:
```

modinfo brcmsmac
locate brcmsmac.ko | grep lib
lsmod
rfkill list
iwconfig
sudo iwlist scan
dmesg | egrep 'bcma|brcm|[F]irm'
```

---

### Post by andreic9203 on 2013-06-02
> **praseodym said:**
> Check:
```

modinfo brcmsmac
locate brcmsmac.ko | grep lib
lsmod
rfkill list
iwconfig
sudo iwlist scan
dmesg | egrep 'bcma|brcm|[F]irm'
```


ok, here is the results:



```

modinfo brcmsmac

```


```

filename:       /lib/modules/3.5.0-30-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     7F13C2F3915BEEB98DAE685
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
depends:        mac80211,bcma,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.5.0-30-generic SMP mod_unload modversions 

```


```

locate brcmsmac.ko | grep lib

```


```

/lib/modules/3.2.0-43-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
/lib/modules/3.5.0-23-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
/lib/modules/3.5.0-30-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko

```


```

lsmod

```


```

Module                  Size  Used by
rfcomm                 47562  0 
bnep                   18240  2 
parport_pc             32867  0 
ppdev                  17114  0 
btusb                  22432  0 
bluetooth             211812  14 rfcomm,bnep,btusb
arc4                   12530  2 
coretemp               13642  0 
brcmsmac              541775  0 
mac80211              555272  1 brcmsmac
brcmutil               14756  1 brcmsmac
dell_wmi               12682  0 
sparse_keymap          13891  1 dell_wmi
cfg80211              208382  2 brcmsmac,mac80211
cordic                 12575  1 brcmsmac
dell_laptop            17426  0 
dcdbas                 14491  1 dell_laptop
snd_hda_codec_idt      70774  1 
microcode              23030  0 
snd_hda_intel          34063  3 
snd_hda_codec         135141  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  2 snd_hda_intel,snd_hda_codec
psmouse               102075  0 
snd_seq_midi           13325  0 
serio_raw              13216  0 
snd_rawmidi            30750  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
wmi                    19257  1 dell_wmi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
video                  19653  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
radeon                917824  3 
snd                    83674  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    88495  1 radeon
drm_kms_helper         49259  1 radeon
drm                   290344  5 radeon,ttm,drm_kms_helper
soundcore              15092  1 snd
joydev                 17694  0 
uvcvideo               78117  0 
videobuf2_core         33025  1 uvcvideo
videodev              125126  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
lpc_ich                17145  0 
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
mac_hid                13254  0 
videobuf2_memops       13405  1 videobuf2_vmalloc
bcma                   35762  1 brcmsmac
i2c_algo_bit           13565  1 radeon
mei                    41410  0 
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
hid_apple              13376  0 
ums_realtek            18257  0 
usb_storage            49288  1 ums_realtek
hid_generic            12541  0 
usbhid                 47259  0 
hid                   100815  3 hid_apple,hid_generic,usbhid
r8169                  62766  0 
ahci                   25869  4 
libahci                27338  1 ahci

```




```

rfkill list

```


```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

```


```

iwconfig

```


```

eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"WI-FI_CONN"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:22:B0:A2:0C:66   
          Bit Rate=54 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-22 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:5  Invalid misc:60   Missed beacon:0

```




```

sudo iwlist scan

```


```

eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: 00:22:B0:A2:0C:66
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:on
                    ESSID:"WI-FI_CONN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001f96039c9ff
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 000A57492D46495F434F4E4E
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 32080C1218602430486C
                    IE: Unknown: CC0700CC020000018A
                    IE: Unknown: CC0700CC0300000100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:20:A6:BB:A7:C0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000002a62437
                    Extra: Last beacon: 1044ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030101
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 7A:96:A0:E1:0F:38
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"AIESEC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004198bb6eff
                    Extra: Last beacon: 996ms ago
                    IE: Unknown: 0006414945534543
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A8E1103FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601040000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DDA20050F204104A0001101044000102103B00010310470010BC329E001DD811B286017A96A0E10F381021001D48756177656920546563686E6F6C6F6769657320436F2E2C204C74642E1023001C48756177656920576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F204000110110009487561776569415053100800020084103C000100
                    IE: Unknown: 0B0500003E127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706434120010D10
                    IE: Unknown: DD1E00904C338E1103FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401040000000000000000000000000000000000000000
          Cell 04 - Address: 7A:96:A0:E1:0F:39
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"RomTelecom-WPA-0F3A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004198bbf129
                    Extra: Last beacon: 964ms ago
                    IE: Unknown: 0013526F6D54656C65636F6D2D5750412D30463341
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A8E1103FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601040000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500003E127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706434120010D10
                    IE: Unknown: DD1E00904C338E1103FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401040000000000000000000000000000000000000000
          Cell 05 - Address: 00:20:A6:BB:A7:C1
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"FlashNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000002a5323f
                    Extra: Last beacon: 1108ms ago
                    IE: Unknown: 0008466C6173684E4554
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030101
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: 32041224606C
          Cell 06 - Address: 00:20:A6:BB:A7:C2
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:off
                    ESSID:"World Wifi Brasov"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000002a54712
                    Extra: Last beacon: 1100ms ago
                    IE: Unknown: 0011576F726C64205769666920427261736F76
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030101
                    IE: Unknown: 2A0102
                    IE: Unknown: 32041224606C
          Cell 07 - Address: F8:D1:11:B7:FB:D4
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"La Bodega cu Gratar"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000035100ed3ba
                    Extra: Last beacon: 1096ms ago
                    IE: Unknown: 00134C6120426F6465676120637520477261746172
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E1103FF00000000000000000000000000000000000000000000
                    IE: Unknown: 331A6E1103FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601051300000000000000000000000000000000000000
                    IE: Unknown: 341601051300000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD990050F204104A0001101044000102103B0001031047001000000000000010000000F8D111B7FB101021000754502D4C494E4B10230009544C2D57523734304E10240003342E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523734304E100800020086103C000101104900140024E26002000101600000020001600100020001
          Cell 08 - Address: 00:24:01:97:E7:F0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"FREE_NET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000513376217e
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 0008465245455F4E4554
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 32080C1218602430486C
                    IE: Unknown: CC0700CC020000018A
                    IE: Unknown: CC0700CC0300000100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: 00:19:E0:A1:2B:54
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"123"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000362748111
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 0003313233
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 07065A4120010D14
                    IE: Unknown: 2A0102
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F03010000000019E0A12B540219E0A12B5464002C010808
          Cell 10 - Address: 08:86:3B:1E:37:44
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"Solyomfeszek"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000be8c7e4178
                    Extra: Last beacon: 456ms ago
                    IE: Unknown: 000C536F6C796F6D6665737A656B
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1113FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1607070000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: DD1E00904C33EE1113FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3407070000000000000000000000000000000000000000
                    IE: Unknown: DDA90050F204104A0001101044000102103B00010310470010775B6680BFDE11D38D2F08863B1E37441021001442656C6B696E20496E7465726E6174696F6E616C102300114E20576972656C65737320526F757465721024000C463544383233362D342076331042000E32303131383832333630303634341054000800060050F20400011011001842656C6B696E204E20576972656C65737320526F7574657210080002008C103C000101
          Cell 11 - Address: 4C:0B:3A:62:47:C3
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"wifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001c76d28e44
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 000477696669
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C1019FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: DD09001018020100040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 12 - Address: F4:EC:38:EC:BC:28
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"KAISBERG_Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000dbc2676b
                    Extra: Last beacon: 672ms ago
                    IE: Unknown: 00104B414953424552475F4E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34090F0A00000000000000000000000000000000000000
                    IE: Unknown: 3D16090F0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD850050F204104A0001101044000102103B0001031047001000000000000010000000F4EC38ECBC281021000754502D4C494E4B10230009544C2D57523734304E10240007312E302F322E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523734304E100800020086103C000101
          Cell 13 - Address: F4:EC:38:C1:0B:F0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Tokugawa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=0000003d1a10c181
                    Extra: Last beacon: 484ms ago
                    IE: Unknown: 0008546F6B7567617761
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 050400010010
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 14 - Address: 00:22:B0:A3:54:CC
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000012e02f1273
                    Extra: Last beacon: 488ms ago
                    IE: Unknown: 0005646C696E6B
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: CC0700CC020000018A
                    IE: Unknown: CC0700CC0300000100
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0102
                    IE: Unknown: 32080C1218602430486C
          Cell 15 - Address: CA:77:F9:58:70:5C
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"mona"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=00000001bddb9dbd
                    Extra: Last beacon: 408ms ago
                    IE: Unknown: 00046D6F6E61
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: Unknown: 06020000
                    IE: Unknown: 070A555320010B1B0C021400
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 16 - Address: C0:C1:C0:A2:A0:25
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000340f56ad3e6
                    Extra: Last beacon: 356ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020004
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: 22:06:41:66:24:35
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"Connectify-me"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000000035488251
                    Extra: Last beacon: 352ms ago
                    IE: Unknown: 000D436F6E6E6563746966792D6D65
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 06020000
                    IE: Unknown: DD09001018020010000000
          Cell 18 - Address: 06:DE:2B:33:36:04
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Connectify-Alex"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a167560180
                    Extra: Last beacon: 340ms ago
                    IE: Unknown: 000F436F6E6E6563746966792D416C6578
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F20201010A0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001100000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 19 - Address: 00:18:39:AC:09:24
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"vila Ovesea"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a68ad97c00
                    Extra: Last beacon: 332ms ago
                    IE: Unknown: 000B76696C61204F7665736561
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0103
                    IE: Unknown: 32080C1218243048606C

```
```

dmesg | egrep 'bcma|brcm|[F]irm'

```


```

[    0.238581] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[   19.225379] bcma: Found chip with id 0x4313, rev 0x01 and package 0x08
[   19.225410] bcma: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   19.225434] bcma: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   19.225501] bcma: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   19.259765] bcma: Bus registered
[   19.561877] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 17
[   23.052606] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   23.052619] ieee80211 phy0: brcms_ops_config: change power-save mode: false (implement)
[   25.625749] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[   25.625754] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[   25.625756] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   25.947108] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)

```

Thank you for helping me.

---

### Post by praseodym on 2013-06-02
Try pure WPA2-AES encryption and a fixed channel

---

### Post by praseodym on 2013-06-02
Try pure WPA2-AES encryption and a fixed channel

---

### Post by andreic9203 on 2013-06-02
> **praseodym said:**
> Try pure WPA2-AES encryption and a fixed channel


Exactly, how can I do that? :|

---

### Post by praseodym on 2013-06-02
Enter the router interface, see its manual.

---

### Post by andreic9203 on 2013-06-04
> **praseodym said:**
> Enter the router interface, see its manual.

Ok, I changed to the [COLOR=#000000][I]WPA2-AES but not even a change.
[/I][/COLOR]If you have any ideas, please write here, and I'll try.[COLOR=#000000][I]
[/I][/COLOR]Thank you for trying to help me.

---

### Post by praseodym on 2013-06-04
Open the firefox and enter
```

about:config
```
Search for "ipv6" and change it to "true" via double click. Restart firefox

---

### Post by andreic9203 on 2013-06-07
> **praseodym said:**
> Open the firefox and enter
```

about:config
```
Search for "ipv6" and change it to "true" via double click. Restart firefox


No result.
At my office, recently I received a new pc with ubuntu installed on it.
Is the same version like I have at home, 12.04, but at work, all seems to work well.
Maybe, there's a possibility to installed it wrong?
I can't see where may be I fault but, I don't know.
You think I supposed to try to reinstall ubuntu?

---

### Post by andreic9203 on 2013-06-24
Hello.
Maybe this hint will help someone to understand what is happening here.
My cable internet and the wi-fi is very very slow and sometimes doesn't work at all, but when I try the USB broadband internet(romania orange provider), the internet works well. 
I supposed is something about ports.
If any of you have an idea, even a little one, please write it here.
Thanks in advance.

Andrei.

---

### Post by andreic9203 on 2013-07-03
No one, no idea? :(
I miss ubuntu :(

---

### Post by praseodym on 2013-07-04
Try the patched driver from here:

[http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Version-V5-100-82-112-DKMS](http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Version-V5-100-82-112-DKMS)

Check for 32/64 bit and kernel 3.5

---

### Post by silv3rm00n on 2013-07-04
First ping your router and check the response time
for example
ping 192.168.1.1 

then ping a dns server like 8.8.8.8

note the time, check which part is slow, your connection to router or routers connection to the isp.

---

### Post by andreic9203 on 2013-07-13
> **praseodym said:**
> Try the patched driver from here:

[http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Version-V5-100-82-112-DKMS](http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Version-V5-100-82-112-DKMS)

Check for 32/64 bit and kernel 3.5


> **silv3rm00n said:**
> First ping your router and check the response time
for example
ping 192.168.1.1 

then ping a dns server like 8.8.8.8

note the time, check which part is slow, your connection to router or routers connection to the isp.


Thank you very much for these tips, but unfortunetly, no one wasn't good.
Finally, I installed the kubuntu 13.04 and all seems to work ok. Maybe some drivers from the ubuntu don't work properly on my laptop's hardware... I don't know what to tell, but for you guys, who tried to help me, I can say 'thank you'.


Great community, mostly I like Linux and Ubuntu because of that.

---

