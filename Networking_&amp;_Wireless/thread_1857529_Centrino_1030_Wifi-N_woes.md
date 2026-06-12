---
title: "Centrino 1030 Wifi-N woes"
date: 2011-10-10
forum: Networking &amp; Wireless
---

### Post by gangaskan on 2011-10-10
hi everyone! first time poster and i just recently converted my laptop (compal FL90) and i'm happily using ubuntu 64 :P  

however, one thing i have problems with is the wifi.  i installed a Intel 1030N  for wifi + bluetooth, however, as of recently i've been encountering issues with it actually connecting to AP's even when they're in the same room.  i have a Cisco 1200 LWAPP just about on top of me at work and i do see SSID's but when i try to connect it asks me for encryption key's again.  same with my house, cisco 851W in the same room.  i also had a netgear N router with DDWRT at one point and i had the same problems.  

sometimes it works, sometimes the wifi vanishes (the network widget disappears from the menu bar) at this time i can still see Wlan0  


it was working flawless until i started messing with the Sonicwall Netextender.  thats when i really noticed something wrong.  i couldnt get it to work and on accident removed LIBSSL.0.9.8 and CRYPTO.0.9.8 i was able to restore them from the lib's under the live disk, and its been up and running very well other than wifi.  


ive seen others have luck with upgrading their kernel to 2.6.38 (perhaps i think some were at 10.04 at the time though), turning off power save options, and removing networkmanager.state


what can i do to fix this?  
if you need me to post up anything like iwconfig, lspci or whatever let me know.

---

### Post by praseodym on 2011-10-10
Hi,

please show:

```
lsb_release -a
uname -a
lspci -nnk | grep -iA2 net
iwconfig
lsmod
dmesg | grep iwl
```
If the card is "too new" install a new driver version and/or firmware:

Firmware:
```
wget http://media.cdn.ubuntu-de.org/forum/attachments/2767012/Intel_Firmware.tar.gz
sudo tar xvf Intel_Firmware.tar.gz -C /lib/firmware
```

Driver:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
wget http://www.orbit-lab.org/kernel/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-20*
make clean
make
sudo make install 
```
Reboot.

If you update the driver, you may need to compile again after a kernel upgrade:

```
cd compat-wireless-20*
make clean
make
sudo make install
```

---

### Post by gangaskan on 2011-10-10
here are my outputs. 


lsb_release -a
> 
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.04
Release:	11.04
Codename:	natty


uname -a
> 
Linux mobilekan 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
[/quote


lspci -nnk | grep -iA2 net
[quote] 
04:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
	Subsystem: COMPAL Electronics Inc Device [14c0:0025]
	Kernel driver in use: tg3
--
0c:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [8086:008a] (rev 34)
	Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN [8086:5305]
	Kernel driver in use: iwlagn



iwconfig
> 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.442 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
vboxnet0  no wireless extensions.


lsmod
> 
Module                  Size  Used by
hidp                   22572  0 
hid                    91020  1 hidp
binfmt_misc            17565  1 
vboxnetadp             13340  0 
vboxnetflt             28297  0 
vboxdrv               252684  2 vboxnetadp,vboxnetflt
parport_pc             36959  0 
ppdev                  17113  0 
vesafb                 13761  1 
joydev                 17606  0 
snd_hda_codec_realtek   336771  1 
nvidia              10709116  53 
arc4                   12529  2 
snd_hda_intel          33176  2 
iwlagn                333716  0 
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
uvcvideo               72195  0 
rfcomm                 47694  15 
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
sco                    18187  2 
bnep                   18308  2 
l2cap                  53570  19 hidp,rfcomm,bnep
btusb                  18600  3 
snd_pcm                96391  2 snd_hda_intel,snd_hda_codec
iwlcore               167502  1 iwlagn
bluetooth              72320  10 hidp,rfcomm,sco,bnep,l2cap,btusb
mac80211              294370  2 iwlagn,iwlcore
microcode              22702  0 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
compal_laptop          19971  0 
cfg80211              178528  3 iwlagn,iwlcore,mac80211
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73535  0 
serio_raw              13166  0 
snd                    67382  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
video                  19438  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  2 
sdhci_pci              13989  0 
firewire_ohci          40370  0 
firewire_core          62646  1 firewire_ohci
sdhci                  27387  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
libahci                26642  1 ahci
tg3                   141750  0 



dmesg | grep iwl
> 
[   12.596361] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   12.596365] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   12.596506] iwlagn 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.596516] iwlagn 0000:0c:00.0: setting latency timer to 64
[   12.596552] iwlagn 0000:0c:00.0: Detected Intel(R) Centrino(R) Wireless-N 1030 BGN, REV=0xB0
[   12.612204] iwlagn 0000:0c:00.0: device EEPROM VER=0x716, CALIB=0x6
[   12.612208] iwlagn 0000:0c:00.0: Device SKU: 0X9
[   12.612211] iwlagn 0000:0c:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   12.663929] iwlagn 0000:0c:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   12.664026] iwlagn 0000:0c:00.0: irq 49 for MSI/MSI-X
[   12.691763] iwlagn 0000:0c:00.0: loaded firmware version 17.168.5.2 build 35905
[   12.767567] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[  226.884070] iwlagn 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[  226.884108] iwlagn 0000:0c:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf8000004)
[  226.884117] iwlagn 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[  226.884129] iwlagn 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x40100106)


---

### Post by praseodym on 2011-10-11
Looks good, I think compiling is not needed. Update the driver via:

```
sudo apt-get install linux-backports-modules-cw-2.6.39-natty-generic
```
and reboot. Check:

```
iwconfig
sudo iwlist scan
iwlist chan
dmesg | grep iwl
```

---

### Post by gangaskan on 2011-10-11
i'm getting unable to locate packages errors.  


E: Unable to locate package linux-backports-modules-cw-2.6.39-natty
E: Couldn't find any package by regex 'linux-backports-modules-cw-2.6.39-natty'

---

### Post by praseodym on 2011-10-11
Do you have any connection? If no, here are the needed packages:


[http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-cw-2.6.39-natty-generic_2.6.38.11.26_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-cw-2.6.39-natty-generic_2.6.38.11.26_amd64.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.38/linux-backports-modules-cw-2.6.39-2.6.38-11-generic_2.6.38-11.7_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.38/linux-backports-modules-cw-2.6.39-2.6.38-11-generic_2.6.38-11.7_amd64.deb)

Install them by double clicking and reboot.

---

### Post by gangaskan on 2011-10-11
yeah, i'm on Ethernet right now. i'll try the packages here in a few.

---

### Post by gangaskan on 2011-10-12
> **praseodym said:**
> Do you have any connection? If no, here are the needed packages:


[http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-cw-2.6.39-natty-generic_2.6.38.11.26_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-cw-2.6.39-natty-generic_2.6.38.11.26_amd64.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.38/linux-backports-modules-cw-2.6.39-2.6.38-11-generic_2.6.38-11.7_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.38/linux-backports-modules-cw-2.6.39-2.6.38-11-generic_2.6.38-11.7_amd64.deb)

Install them by double clicking and reboot.


installed the packages and everything went well, however, still unable to connect to a SSID.  i can see them, it asks me for encryption, and nothing afterwards.

---

### Post by praseodym on 2011-10-12
Does your router send in b+g+n mode? Intel deactivated N-mode per default, better choose b+g mode in your router.

Maybe you can activate the N-mode via:

```
echo "options iwlagn 11n_disable=0" | sudo tee /etc/modprobe.d/iwlagn.conf
sudo modprobe -rf iwlagn
sudo modprobe -v iwlagn
```
but normally you need a newer kernel for that.

---

### Post by gangaskan on 2011-10-12
> **praseodym said:**
> Does your router send in b+g+n mode? Intel deactivated N-mode per default, better choose b+g mode in your router.

Maybe you can activate the N-mode via:

```
echo "options iwlagn 11n_disable=0" | sudo tee /etc/modprobe.d/iwlagn.conf
sudo modprobe -rf iwlagn
sudo modprobe -v iwlagn
```
but normally you need a newer kernel for that.


no N on my router, just B/G would that matter?

---

### Post by praseodym on 2011-10-12
No, thats Ok. Please show the outputs of 

```
iwconfig
ifconfig -a
route -n
cat /etc/resolv.conf
sudo iwlist scan
iwlist chan
dmesg | grep iwl
ping -c 4 www.ubuntuusers.de
ping -c 4 213.95.41.11
```

---

### Post by gangaskan on 2011-10-12
> **praseodym said:**
> No, thats Ok. Please show the outputs of 

```
iwconfig
ifconfig -a
route -n
cat /etc/resolv.conf
sudo iwlist scan
iwlist chan
dmesg | grep iwl
ping -c 4 www.ubuntuusers.de
ping -c 4 213.95.41.11
```

iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"CityHallPublic"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```


ifconfig -a 

```
 
eth0      Link encap:Ethernet  HWaddr 00:1b:38:6b:02:bd  
          inet addr:10.1.2.186  Bcast:10.1.255.255  Mask:255.255.0.0
          inet6 addr: fe80::21b:38ff:fe6b:2bd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1769 errors:0 dropped:0 overruns:0 frame:0
          TX packets:642 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:770504 (770.5 KB)  TX bytes:69547 (69.5 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr bc:77:37:03:b9:ca  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
10.1.0.0        0.0.0.0         255.255.0.0     U     1      0        0 eth0
0.0.0.0         10.1.1.6        0.0.0.0         UG    0      0        0 eth0

```

iwlist scan
```


lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1D:E5:81:52:03
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=70/70  Signal level=-28 dBm  
                    Encryption key:on
                    ESSID:"LMC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000028f4e1a574
                    Extra: Last beacon: 410ms ago
                    IE: Unknown: 00034C4D43
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030108
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B0500000C0000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E04008F000F00FF035900365468466C4C5741505000000000000000000027
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD180050F2020101800003000000270000004200000072000000
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
          Cell 02 - Address: 00:1C:0F:82:FB:E3
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"LMC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002c16dd7c943
                    Extra: Last beacon: 540ms ago
                    IE: Unknown: 00034C4D43
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B0502000C0000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E05008F000F00FF035900466C6F6F72372D4C574150000000000002000027
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD180050F2020101800003000000270000004200000072000000
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
          Cell 03 - Address: 00:1D:E5:81:52:00
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:on
                    ESSID:"CityofLorain"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000028f4e0218c
                    Extra: Last beacon: 440ms ago
                    IE: Unknown: 000C436974796F664C6F7261696E
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030108
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B0500000A0000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E04008F000F00FF035900365468466C4C5741505000000000000000000027
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD180050F2020101800003000000270000004200000072000000
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
          Cell 04 - Address: 00:1D:E5:81:52:01
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000028f48ee18c
                    Extra: Last beacon: 5810ms ago
                    IE: Unknown: 000100
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030108
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B0500000A0000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E04008F000F00FF035900365468466C4C5741505000000000000000000027
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD180050F2020101800003000000270000004200000072000000
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 05 - Address: 00:1C:0F:82:FE:00
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"CityofLorain"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000018f968fd18c
                    Extra: Last beacon: 5610ms ago
                    IE: Unknown: 000C436974796F664C6F7261696E
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050000090000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E06008F000F00FF035900436F6D6D4465765F417000000000000000000027
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD180050F2020101800003000000270000004200000072000000
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401

```

iwlist chan 
```


lo        no frequency information.

eth0      no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.447 GHz (Channel 8)

```

dmesg |grep iwl 

```


[   17.674399] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   17.674403] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   17.674562] iwlagn 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.674573] iwlagn 0000:0c:00.0: setting latency timer to 64
[   17.674609] iwlagn 0000:0c:00.0: Detected Intel(R) Centrino(R) Wireless-N 1030 BGN, REV=0xB0
[   17.690636] iwlagn 0000:0c:00.0: device EEPROM VER=0x716, CALIB=0x6
[   17.690640] iwlagn 0000:0c:00.0: Device SKU: 0X9
[   17.690642] iwlagn 0000:0c:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   17.699521] iwlagn 0000:0c:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   17.699617] iwlagn 0000:0c:00.0: irq 49 for MSI/MSI-X
[   17.736536] iwlagn 0000:0c:00.0: loaded firmware version 17.168.5.1 build 33993
[   17.799099] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'

```

pings  (i'm on eth0 currently no wifi)

```


PING ubuntuusers.de (213.95.41.13) 56(84) bytes of data.
64 bytes from lisa.ubuntu-eu.org (213.95.41.13): icmp_req=1 ttl=44 time=443 ms
64 bytes from lisa.ubuntu-eu.org (213.95.41.13): icmp_req=2 ttl=44 time=389 ms
From 10.1.1.6: icmp_seq=3 Redirect Network(New nexthop: 10.1.1.220)
64 bytes from lisa.ubuntu-eu.org (213.95.41.13): icmp_req=3 ttl=44 time=380 ms
64 bytes from lisa.ubuntu-eu.org (213.95.41.13): icmp_req=4 ttl=44 time=320 ms

--- ubuntuusers.de ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 12010ms
rtt min/avg/max/mdev = 320.486/383.466/443.522/43.623 ms

PING 213.95.41.11 (213.95.41.11) 56(84) bytes of data.
64 bytes from 213.95.41.11: icmp_req=1 ttl=44 time=511 ms
64 bytes from 213.95.41.11: icmp_req=2 ttl=44 time=317 ms
64 bytes from 213.95.41.11: icmp_req=3 ttl=44 time=307 ms
64 bytes from 213.95.41.11: icmp_req=4 ttl=44 time=345 ms

--- 213.95.41.11 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 307.548/370.307/511.149/82.486 ms

```

---

### Post by praseodym on 2011-10-12
The network "CityHallPublic" seems to be hidden. Is it public? Try to "connect to a hidden network" and/or add the hardware address of the network you want to connect to into the field "BSSID".

> ```
          Cell 04 - Address: [COLOR="Red"]00:1D:E5:81:52:01[/COLOR]
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"[COLOR="Red"]\x00[/COLOR]"
```

---

### Post by gangaskan on 2011-10-12
> **praseodym said:**
> The network "CityHallPublic" seems to be hidden. Is it public? Try to "connect to a hidden network" and/or add the hardware address of the network you want to connect to into the field "BSSID".

its not hidden.  all of our network SSID's are broadcasting.

will not work via hardware address or hidden network for BSSID either.

---

### Post by praseodym on 2011-10-12
Which network dou you want to connect to? Traffic on Channel 8, identical ESSIDs on Cell 1 and 2. I recommend using different ESSIDs and changing the channel.

---

### Post by gangaskan on 2011-10-13
> **praseodym said:**
> Which network dou you want to connect to? Traffic on Channel 8, identical ESSIDs on Cell 1 and 2. I recommend using different ESSIDs and changing the channel.

i figured out my issue.  after running the live disc and encountering the same issues i installed my old B/G adapter in, its a lintel too.  wireless works fine.  is there a way i can just use the Bluetooth module in the other N adapter?  when i have 2 cards in they seem to cancel out each other, i "see" both adapters in the network manager, but cant connect or enable anything.

---

### Post by praseodym on 2011-10-13
What card is that? Show the "lspci" output again. The Bluetooth module is USB?

---

### Post by collisionystm on 2011-10-13
> **gangaskan said:**
> hi everyone! first time poster and i just recently converted my laptop (compal FL90) and i'm happily using ubuntu 64 :P  

however, one thing i have problems with is the wifi.  i installed a Intel 1030N  for wifi + bluetooth, however, as of recently i've been encountering issues with it actually connecting to AP's even when they're in the same room.  i have a Cisco 1200 LWAPP just about on top of me at work and i do see SSID's but when i try to connect it asks me for encryption key's again.  same with my house, cisco 851W in the same room.  i also had a netgear N router with DDWRT at one point and i had the same problems.  

sometimes it works, sometimes the wifi vanishes (the network widget disappears from the menu bar) at this time i can still see Wlan0  


it was working flawless until i started messing with the Sonicwall Netextender.  thats when i really noticed something wrong.  i couldnt get it to work and on accident removed LIBSSL.0.9.8 and CRYPTO.0.9.8 i was able to restore them from the lib's under the live disk, and its been up and running very well other than wifi.  


ive seen others have luck with upgrading their kernel to 2.6.38 (perhaps i think some were at 10.04 at the time though), turning off power save options, and removing networkmanager.state


what can i do to fix this?  
if you need me to post up anything like iwconfig, lspci or whatever let me know.

I had this same exact card.

The 3.0 Kernel carries the proper drivers for it. Intel packs all of their drivers into the linux kernel itself. Every time you get a kernel update, you get the latest intel drivers as well.

NOTE:

On Windows 7 with this wireless card, you must disable all power management for it. You do this in power options and advanced. There is a bug with this card and power management, although on the 3.0 kernel it seems to be unaffected.

---

