---
title: "Why SMC USB 2.0 adapter works in PuppyLinux and NOT in Ubuntu??"
date: 2011-09-09
forum: Networking &amp; Wireless
---

### Post by tmlop on 2011-09-09
Suddenly my SMC ez connect g 2.0 usb adapter isn't working in Ubuntu 10.10 or Kubuntu 11.04
Never had problems until now
I can see other wireless networks but not mine:confused:
The exception is Puppy Linux 5.2 where the ssid appears and I'm able to connect easy 


**UBUNTU 10.10 output**:
uname -mr
```
2.6.35-22-generic i686
```

```
Manufacturer=SMC
Product=USB2.0 WLAN
VendorID=083a  ProductID=4505  KERNEL-MODULE=zd1211rw
```

lsusb
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 18a5:0214 Verbatim, Ltd Portable Hard Drive
Bus 001 Device 002: ID 083a:4505 Accton Technology Corp. SMCWUSB-G 802.11bg
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

iwconfig wlan0
```
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

lsmod | grep zd1211rw
```
zd1211rw               43440  0 
mac80211              231541  1 zd1211rw
cfg80211              144470  2 zd1211rw,mac80211
```

dmesg | grep zd1211rw
```
[   19.062002] zd1211rw 1-2:1.0: phy0
[   19.062044] usbcore: registered new interface driver zd1211rw
[   20.903539] zd1211rw 1-2:1.0: firmware version 4725
[   20.946359] zd1211rw 1-2:1.0: zd1211b chip 083a:4505 v4810 high 00-13-f7 AL2230_RF pa0 g--N-
```

sudo lshw -C network
```
*-network               
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2
       logical name: wlan0
       serial: 00:13:f7:e6:99:4f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=zd1211rw driverversion=2.6.35-22-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
```


**In Puppy Linux 5.2 WORKS!**

Kernel		: Linux 2.6.33.2 (i686)

lsmod | grep zd1211rw
```
zd1211rw               32476  0 
mac80211               99898  1 zd1211rw
cfg80211               90319  2 zd1211rw,mac80211
usbcore                91279  6 zd1211rw,usb_storage,usbhid,uhci_hcd,ehci_hcd
```

iwlist wlan0 scan
```
wlan0     Scan completed :
          Cell 01 - Address: 00:05:CA:DF:45:A8
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=28/100  Signal level=28/100  
                    Encryption key:on
                    ESSID:"MY-SSID"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001147f506aa
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 00085A4F4E2D34354130
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010D
                    IE: Unknown: 2A0100
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 2D1A8C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160D000700000000000000000000000000000000000000
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
                    IE: Unknown: 0B0503000A127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD9D0050F204104A0001101044000102103B000103104700102880288028801880A8800005CADF45A81021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B415053100800020084103C000101
```

---

### Post by tmlop on 2011-09-10
bump

---

### Post by praseodym on 2011-09-10
Please show the complete outputs of

```
lsmod
```
from Puppy _and_ Ubuntu. Maybe using the module from Puppy should work.

---

### Post by tmlop on 2011-09-10
Could it be the adapter hardware failing?
In Puppy I have noticed that connection drops but it still works if reconnected
Ubuntu *iwlist scan* shows only 4 neighbourhood low signal networks

**_Ubuntu_**

lsmod
```

Module                  Size  Used by
arc4                    1165  2 
lm63                    5972  0 
radeon                825934  1 
snd_intel8x0           25632  0 
snd_ac97_codec         99227  1 snd_intel8x0
ttm                    56633  1 radeon
ac97_bus                1014  1 snd_ac97_codec
zd1211rw               43440  0 
drm_kms_helper         30200  1 radeon
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
mac80211              231541  1 zd1211rw
snd_timer              19067  1 snd_pcm
drm                   168054  3 radeon,ttm,drm_kms_helper
intel_agp              26360  1 
cfg80211              144470  2 zd1211rw,mac80211
snd                    49006  4 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
psmouse                59033  0 
i2c_algo_bit            5168  1 radeon
soundcore                880  1 snd
shpchp                 29886  0 
lp                      7342  0 
serio_raw               4022  0 
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
agpgart                32011  3 ttm,drm,intel_agp
parport                31492  1 lp
usb_storage            40172  0 
floppy                 54311  0 
skge                   37646  0 

```

dmesg | grep usb
```
[    0.208038] usbcore: registered new interface driver usbfs
[    0.208068] usbcore: registered new interface driver hub
[    0.208119] usbcore: registered new device driver usb
[    2.264020] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    2.504063] usb 1-3: new high speed USB device using ehci_hcd and address 3
[    2.651019] scsi2 : usb-storage 1-3:1.0
[    2.651223] usbcore: registered new interface driver usb-storage
[    8.648058] usb 1-2: reset high speed USB device using ehci_hcd and address 2
[    8.799918] usbcore: registered new interface driver zd1211rw
```

dmesg | grep firmware
```
[ 2195.303811] zd1211rw 1-2:1.0: firmware version 4725
```


**_Puppy_**

lsmod

```
Module                  Size  Used by
aes_generic            25730  1 
radeon                515838  1 
drm_kms_helper         17823  1 radeon
ttm                    31586  1 radeon
drm                   106327  4 radeon,drm_kms_helper,ttm
i2c_algo_bit            3539  1 radeon
iptable_mangle          1189  0 
iptable_nat             2666  0 
nf_nat                 10083  1 iptable_nat
ipt_REJECT              1485  1 
nf_conntrack_ftp        4020  0 
nf_conntrack_irc        2359  0 
iptable_filter           958  1 
xt_state                 895  4 
nf_conntrack_ipv4       7063  7 iptable_nat,nf_nat
nf_conntrack           36999  6 iptable_nat,nf_nat,nf_conntrack_ftp,nf_conntrack_irc,xt_state,nf_conntrack_ipv4
nf_defrag_ipv4           755  1 nf_conntrack_ipv4
ip_tables               7321  3 iptable_mangle,iptable_nat,iptable_filter
arc4                     962  2 
ecb                     1377  2 
snd_intel8x0           19143  0 
zd1211rw               32476  0 
snd_ac97_codec         75789  1 snd_intel8x0
ac97_bus                 686  1 snd_ac97_codec
mac80211               99898  1 zd1211rw
snd_pcm_oss            26845  0 
snd_mixer_oss           9963  1 snd_pcm_oss
cfg80211               90319  2 zd1211rw,mac80211
snd_pcm                45385  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy            907  0 
snd_seq_oss            18888  0 
snd_seq_midi            3156  0 
snd_seq_midi_event      3592  2 snd_seq_oss,snd_seq_midi
snd_rawmidi            11924  1 snd_seq_midi
snd_seq                32379  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          3601  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              11986  2 snd_pcm,snd_seq
snd                    30859  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_timer
skge                   28480  0 
soundcore               3403  1 snd
snd_page_alloc          4645  2 snd_intel8x0,snd_pcm
serio_raw               2928  0 
pcspkr                  1179  0 
fbcon                  27736  0 
bitblit                 3514  1 fbcon
softcursor               805  1 bitblit
tileblit                1509  1 fbcon
font                    6916  1 fbcon
intel_agp              19189  1 
i2c_i801                6146  0 
agpgart                18904  3 ttm,drm,intel_agp
i2c_core               11497  5 radeon,drm_kms_helper,drm,i2c_algo_bit,i2c_i801
shpchp                 21148  0 
pci_hotplug            18286  1 shpchp
evdev                   5517  0 
thermal                 9263  0 
button                  3522  0 
processor              24987  0 
fuse                   42549  0 
aufs                  110466  1 
nls_iso8859_1           2937  1 
nls_cp437               4465  1 
usb_storage            29717  1 
usbhid                 18009  0 
squashfs               15984  1 
uhci_hcd               15444  0 
ehci_hcd               25830  0 
usbcore                91279  6 zd1211rw,usb_storage,usbhid,uhci_hcd,ehci_hcd
floppy                 40152  0
```

dmesg | grep usb
```
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
usbcore: registered new interface driver hiddev
usbcore: registered new interface driver usbhid
usbhid: USB HID core driver
usbcore: registered new interface driver usb-storage
usb 1-2: new high speed USB device using ehci_hcd and address 2
usb 1-3: new high speed USB device using ehci_hcd and address 3
scsi2 : usb-storage 1-3:1.0
usb-storage: device found at 3
usb-storage: waiting for device to settle before scanning
usb-storage: device scan complete
usb 1-2: reset high speed USB device using ehci_hcd and address 2
usbcore: registered new interface driver zd1211rw
usb 1-2: firmware: requesting zd1211/zd1211b_ub
usb 1-2: firmware: requesting zd1211/zd1211b_uphr
```

dmesg | grep firmware 
```
usb 1-2: firmware: requesting zd1211/zd1211b_ub
usb 1-2: firmware: requesting zd1211/zd1211b_uphr
zd1211rw 1-2:1.0: firmware version 4725
```

---

### Post by praseodym on 2011-09-10
Looks like Puppy uses a firewall. You can update the driver via

Maverick:
```
sudo apt-get install linux-backports-modules-wireless-maverick-generic
```

Natty:
```
sudo apt-get install linux-backports-modules-cw-2.6.39-natty-generic
```
reboot after that.

---

### Post by tmlop on 2011-09-11
Can I do a local install ?
dpkg -i **linux-backports-modules-wireless-maverick-generic_2.6.35.30.38_i386.deb **

I've been trying other distros but no results :(

---

### Post by praseodym on 2011-09-11
Yes, but with "sudo dpkg ..." or double clicking.

---

### Post by tmlop on 2011-09-11
I need to setup ethernet cable to do that
I better buy a new wireless NIC :roll:
Would the Conceptronic C300Ri ( chip Ralink RT3062 ) be a good choice?

Thanks for helping

---

### Post by praseodym on 2011-09-11
You need this package:

[http://www.gtlib.gatech.edu/pub/ubuntu//pool/main/l/linux-backports-modules-2.6.35/linux-backports-modules-wireless-2.6.35-22-generic_2.6.35-22.12_i386.deb](http://www.gtlib.gatech.edu/pub/ubuntu//pool/main/l/linux-backports-modules-2.6.35/linux-backports-modules-wireless-2.6.35-22-generic_2.6.35-22.12_i386.deb)

if you can download it with another computer. Double click and reboot

---

### Post by tmlop on 2011-09-11
> **praseodym said:**
> You need this package:

[http://www.gtlib.gatech.edu/pub/ubuntu//pool/main/l/linux-backports-modules-2.6.35/linux-backports-modules-wireless-2.6.35-22-generic_2.6.35-22.12_i386.deb](http://www.gtlib.gatech.edu/pub/ubuntu//pool/main/l/linux-backports-modules-2.6.35/linux-backports-modules-wireless-2.6.35-22-generic_2.6.35-22.12_i386.deb)

if you can download it with another computer. Double click and reboot

Not working either!

Maybe I need Wicd manager
it's in the official repositories?

---

### Post by praseodym on 2011-09-11
Yes, it is. You can additionally install the Add-on from one of the developers for several encryption modes:

```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service network-manager stop
sudo service wicd restart
```
Deactivate the NM in autostart, choose **wlan0** as wireless interface and **wext** as driver.

---

### Post by tmlop on 2011-09-12
Meanwhile, I've changed to a Athlon 64 platform and tested the adapter but the result is the same.

As usual it works on Puppy! Even tested the adapter on a old Pentium 4 and it was capable of working with only USB 1.0!!

I will give Wicd a try

---

### Post by tmlop on 2011-09-15
Wicd doesn't work either! :(
Lists 7 low signal networks but not mine

I wonder how the adapter still works on Puppy!

In conclusion I need to buy a new nic

---

