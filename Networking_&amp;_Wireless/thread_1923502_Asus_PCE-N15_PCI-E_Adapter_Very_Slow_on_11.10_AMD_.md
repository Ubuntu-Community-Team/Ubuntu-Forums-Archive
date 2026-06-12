---
title: "Asus PCE-N15 PCI-E Adapter Very Slow on 11.10 AMD Machine"
date: 2012-02-10
forum: Networking &amp; Wireless
---

### Post by clyon1 on 2012-02-10
Hello,

I recently purchased a network adapter for my desktop machine, however the speed is very very slow (3Mbps).  This particular card does have support for 11.10 from Realtek, but after installing those drivers nothing has changed.  I'm hoping that someone on here will be able to determine if this card is compatible, or if I need to send it back and purchase a different card.  Thanks in advance.

**1) Machine Brand and Model (PC/Laptop):**
```
OS: Ubuntu 11.10 (64 bit)
Processor: AMD Phenom 2 X6
Motherboard: Gigabyte 890GPA-UD3H
Desktop Computer
```

**2) Wireless Brand, Model and Wireless Chipset:**
```
Asus PCE-N15 PCI-E Adapter Wireless-N
Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
```

**3) Check interface:**
```
iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"molly"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:BF:D6:BE:5D   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=42/70  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:888   Missed beacon:0
```



**4) Check for modules:**
```
lsmod
Module                  Size  Used by
rndis_wlan             37554  0 
rndis_host             13848  1 rndis_wlan
cdc_ether              13536  1 rndis_host
usbnet                 26212  3 rndis_wlan,rndis_host,cdc_ether
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61475  1 vfat
parport_pc             36962  0 
dm_crypt               23199  0 
ppdev                  17113  0 
bnep                   18436  2 
rfcomm                 47946  8 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282548  3 vboxpci,vboxnetadp,vboxnetflt
usb_storage            57901  1 
uas                    18027  0 
snd_usb_audio         118122  1 
snd_usbmidi_lib        25371  1 snd_usb_audio
joydev                 17693  0 
uvcvideo               72711  0 
tuner_simple           18551  1 
tuner_types            24318  1 tuner_simple
wm8775                 13103  1 
snd_hda_codec_hdmi     32040  1 
tda9887                14154  1 
tda8290                22616  0 
arc4                   12529  2 
tuner                  27428  2 
cx25840                53683  1 
snd_hda_codec_realtek   330769  1 
btusb                  18600  2 
bluetooth             166112  23 bnep,rfcomm,btusb
binfmt_misc            17540  1 
rtl8192ce             137433  0 
rtlwifi               118709  1 rtl8192ce
ivtv                  160120  0 
cx2341x                28331  1 ivtv
mac80211              452259  2 rtl8192ce,rtlwifi
v4l2_common            16454  5 wm8775,tuner,cx25840,ivtv,cx2341x
videodev               92992  7 uvcvideo,wm8775,tuner,cx25840,ivtv,cx2341x,v4l2_common
v4l2_compat_ioctl32    17083  1 videodev
tveeprom               21249  1 ivtv
snd_seq_midi           13324  0 
snd_hda_intel          33390  2 
snd_rawmidi            30547  2 snd_usbmidi_lib,snd_seq_midi
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
k10temp                13166  0 
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
edac_core              53746  0 
edac_mce_amd           23709  0 
serio_raw              13166  0 
snd_pcm                96714  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
cfg80211              198044  3 rndis_wlan,rtlwifi,mac80211
sp5100_tco             13791  0 
i2c_piix4              13301  0 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  18 snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_rawmidi,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
shpchp                 37345  0 
it87                   43287  0 
hwmon_vid              12746  1 it87
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
hid_logitech           17677  0 
ff_memless             13097  1 hid_logitech
usbhid                 47198  1 hid_logitech
hid                    95463  2 hid_logitech,usbhid
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
pata_jmicron           12747  0 
crc_itu_t              12707  1 firewire_core
radeon               1016211  3 
ttm                    76805  1 radeon
drm_kms_helper         42558  1 radeon
pata_atiixp            13164  0 
drm                   236290  5 radeon,ttm,drm_kms_helper
floppy                 70365  0 
i2c_algo_bit           13423  2 ivtv,radeon
r8169                  52788  0 
ahci                   26002  2 
libahci                26861  1 ahci
wmi                    19256  0 
xhci_hcd               82820  0
``` 

**5 ) Kernel boot messages:**
Repeated over and over:
```
[61758.054213] Valid eCryptfs headers not found in file header region or xattr region
[61758.054219] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
```

**6 ) Network configuration**
```
sudo lshw -C network
  *-network               
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 14:da:e9:f1:90:18
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.0.0-15-generic firmware=N/A ip=192.168.1.118 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:ee00(size=256) memory:fdefc000-fdefffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 03
       serial: 1c:6f:65:98:06:f8
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:51 ioport:de00(size=256) memory:fdaff000-fdafffff memory:fdaf8000-fdafbfff memory:fda00000-fda1ffff
```

**7 ) Scan for networks:**
```
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:BF:D6:BE:5D
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:off
                    ESSID:"molly"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b396ce183
                    Extra: Last beacon: 92256ms ago
                    IE: Unknown: 00056D6F6C6C79
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F4000000

```
**8 ) Ubuntu Version:***
```
lsb_release -d
Description:	Ubuntu 11.10
```

**9 ) Kernel/architecture (including 32 vs. 64 bit):***
```
uname -mr
3.0.0-15-generic x86_64
```

**10) Restarting the network:**
```
sudo /etc/init.d/networking restart

* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...
```

---

### Post by praseodym on 2012-02-11
Hi,

which driver did you install? From where? Please show:

```
modinfo rtl8192ce | egrep 'versi|filen'
```

Alternatively update the driver via:

```
sudo apt-get install --reinstall linux-headers-generic build-essential
wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl_92ce_92se_92de_Ubuntu_11.x_mac80211_0004.0816.2011.tar.gz
tar xvf rtl_92ce_92se_92de_Ubuntu_11.x_mac80211_0004.0816.2011.tar.gz
cd rtl_92ce_92se_92de_Ubuntu_11.x_mac80211_0004.0816.2011
make
sudo make install
sudo cp -r firmware/* /lib/firmware 
```
Reboot and check the driver version again

---

### Post by clyon1 on 2012-02-11
I installed the drivers from [this site]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=272&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE"), I found the link in another forum post.

```
modinfo rtl8192ce | egrep 'versi|filen'
filename:       /lib/modules/3.0.0-15-generic/updates/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
srcversion:     ED0E45761BDA499D03495A3
vermagic:       3.0.0-15-generic SMP mod_unload modversions
```

I will work on updating the driver now.

---

### Post by clyon1 on 2012-02-11
Seems to be the same information, however my wireless doesn't work at all now.  It connected to the router for a second, and keeps disconnecting, with no internet.

```
modinfo rtl8192ce | egrep 'versi|filen'
filename:       /lib/modules/3.0.0-15-generic/updates/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
srcversion:     ED0E45761BDA499D03495A3
vermagic:       3.0.0-15-generic SMP mod_unload modversions 
```

---

### Post by praseodym on 2012-02-11
Please show

> locate rtl8192ce.ko | grep lib

---

### Post by clyon1 on 2012-02-11
Here it is.


```
locate rtl8192ce.ko | grep lib
/lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
/lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
/lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
/lib/modules/3.0.0-13-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
/lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
/lib/modules/3.0.0-15-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
/lib/modules/3.0.0-15-generic/updates/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
```

---

### Post by praseodym on 2012-02-11
Rename the original one:

```
sudo mv /lib/modules/3.0.0-15-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko /lib/modules/3.0.0-15-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.bak
sudo depmod -a
sudo update-initramfs -u
```
Reboot (again).

---

### Post by clyon1 on 2012-02-11
The wireless adapter is connected again, but still with only speeds of about 3Mbps.  Just for comparison, my netbook connected to the same router running Ubuntu with its internal adapter get's between 18-22Mbps. I'm using speedtest.net to capture the data speeds.

---

### Post by praseodym on 2012-02-12
Ok, now check

```
iwconfig
ifconfig -a
cat /etc/resolv.conf
iwlist chan
sudo iwlist scan
dmesg | egrep 'rtl8|r8|country'
```

---

### Post by clyon1 on 2012-02-12
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"molly"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:BF:D6:BE:5D   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0
```

```
ifconfig -a
eth0      Link encap:Ethernet  HWaddr 1c:6f:65:98:06:f8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:50 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:103 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10355 (10.3 KB)  TX bytes:10355 (10.3 KB)

wlan0     Link encap:Ethernet  HWaddr 14:da:e9:f1:90:18  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::16da:e9ff:fef1:9018/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7272 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5951 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8572364 (8.5 MB)  TX bytes:1872023 (1.8 MB)

```

```
cat /etc/resolv.conf
# Generated by NetworkManager
domain hsd1.or.comcast.net.
search hsd1.or.comcast.net.
nameserver 75.75.75.75
nameserver 75.75.76.76

```

```
iwlist chan
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
          Current Frequency:2.412 GHz (Channel 1)

```

```
sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:26:F3:AF:46:C8
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Exile"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000036a2824121
                    Extra: Last beacon: 468ms ago
                    IE: Unknown: 00054578696C65
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A0E1016FFFF000001000000000000000000000000030000000000
                    IE: Unknown: 3D1606000000000000000000000000000000000000000000
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
                    IE: Unknown: 0B05000005127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706555320010B10
          Cell 02 - Address: 60:33:4B:E7:3D:E5
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"houseofturds"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000ca6f5a5837
                    Extra: Last beacon: 404ms ago
                    IE: Unknown: 000C686F7573656F667475726473
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAC4117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001300000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301720320
                    IE: Unknown: DD070017F203020180
                    IE: Unknown: DD0E0017F2070001010660334BE73DE5
          Cell 03 - Address: 00:14:BF:D6:BE:5D
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"molly"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000260a804183
                    Extra: Last beacon: 824ms ago
                    IE: Unknown: 00056D6F6C6C79
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020014000000
          Cell 04 - Address: C0:C1:C0:E4:FC:29
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"grahamsfranchise"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009369354a6b
                    Extra: Last beacon: 148ms ago
                    IE: Unknown: 001067726168616D736672616E6368697365
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081100000000000000000000000000000000000000
                    IE: Unknown: DD690050F204104A0001101044000102103B0001031047001085DADBDC315515501D21BE0FC7147DA110210005436973636F102300054531353030102400063132333435361042000234321054000800060050F2040001101100054531353030100800020084103C000101
                    IE: Unknown: DD090010180200F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: C0:C1:C0:E4:FC:2A
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"grahamsfranchise-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009369355706
                    Extra: Last beacon: 144ms ago
                    IE: Unknown: 001667726168616D736672616E63686973652D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081100000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

```

The last command didn't do anything? dmesg | egrep 'rtl8|r8|country'

---

### Post by praseodym on 2012-02-13
Try Wicd instead of the NM:

```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
```
Deactivate the NM in "autostart", choose **wlan0** as interface name, and **wext** as driver:

```
sudo service network-manager stop
sudo service wicd restart
```

---

### Post by clyon1 on 2012-02-13
It doesn't seem to have helped any.  One thing though, during the install is said something about adding users to something, and I'm not sure if I got my username selected and I couldn't get that screen to appear by re-installing.  Not sure if that would affect it.

---

### Post by clyon1 on 2012-02-20
Anybody have any other ideas? Or recommendations of PCI-E wireless network cards they know will work?

---

### Post by Joshica on 2012-03-29
So, I have this card in Ubuntu 11.10, 64 bit.  Lots of problems, super laggy even though in my games they report 68-100ms.  Anyway, after a lot of research and nothing good, I started fiddling with my wireless settings on my router.  I was getting about 325 average ping on Speedtest.net, and topping out at 3Mbps down, about 1 up.  

I had read to turn off N for the card, but it didn't help.  Instead, being the only wireless-N card in the house, the other is G, as are the phones, I set my router to Wireless-G only, instead of mixed mode.

After that I couldn't browse any pages or even the router, so I just disconnected from my network, waited 5 second, reconnected, and now my ping is as low as 75 ms, getting 200 average though, but my down rate is up to 15Mbps, and up is 5.5ish.

Will keep playing around in WoW and Minecraft and doing Speedtest to see how it holds up, but so far it greatly improved my results.

Best of luck! I did mess with other random settings so just in case you need I'll list what I can remember later.

---

### Post by Joshica on 2012-03-30
Still working really well, I do have the odd lag spike or on some boots, it gets on the network, yet I can't use the internet.  So I disconnect and reconnect to my router and then it's good to go.  Latency on speedtest sometimes gets back up to 300, but the speed is still 15MBps instead of 3.

---

### Post by Victoryofthepeople on 2012-05-21
Had the same issue, but the tech support recommended me to reinstall the latest Asus drivers instead of the realtek ones. Fixed everything for me.

---

