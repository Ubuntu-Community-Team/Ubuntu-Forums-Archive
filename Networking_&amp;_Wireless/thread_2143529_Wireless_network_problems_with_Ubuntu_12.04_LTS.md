---
title: "Wireless network problems with Ubuntu 12.04 LTS"
date: 2013-05-09
forum: Networking &amp; Wireless
---

### Post by yuvalf11 on 2013-05-09
Hey everyone,
Few days ago I have posted a thread with the same problem, but I had Ubuntu 12.10. I thought I have solved the problem but I didn't. I have a HP Pavilion g7. I have 2 problem:
1) Problem to connect to wifi network - even if I inserted the right password, it doesn't authenticate, and ask me to re-enter the password over and over.
2) If it succeed to connect to a wifi network, it disconnected automatically after 2 minutes.

when I ran in the terminal: 

```

lshw -C network

```

the output was:
```

       description: Wireless interface
       product: RT5390 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       serial: e4:d5:3d:8b:27:19
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.2.0-41-generic firmware=0.34 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:c2500000-c250ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 05
       serial: ec:9a:74:4a:e8:5c
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.31 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:3000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff

```

I'm pretty new in Ubuntu and I will really appericiate you help, Thanks!

---

### Post by praseodym on 2013-05-09
Please show the outputs of:
```

lspci -nnk | grep -iA2 net
iwconfig
lsmod
ifconfig -a
sudo iwlist scan
dmesg | grep rt2
```

---

### Post by yuvalf11 on 2013-05-10
> **praseodym said:**
> Please show the outputs of:
```

lspci -nnk | grep -iA2 net
iwconfig
lsmod
ifconfig -a
sudo iwlist scan
dmesg | grep rt2
```

```

yuval@Ben-Yuval-Ubuntu:~$ lspci -nnk | grep -iA2 net 
01:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Hewlett-Packard Company U98Z077.00 Half-size Mini PCIe Card [103c:1636]
    Kernel driver in use: rt2800pci
--
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:1671]
    Kernel driver in use: r8169

yuval@Ben-Yuval-Ubuntu:~$ iwconfig
lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.


yuval@Ben-Yuval-Ubuntu:~$ lsmod
Module                  Size  Used by
rt73usb                31735  0 
crc_itu_t              12707  1 rt73usb
rt2x00usb              20808  1 rt73usb
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
parport_pc             32866  0 
rfcomm                 47604  0 
bnep                   18281  2 
ppdev                  17113  0 
bluetooth             180153  10 rfcomm,bnep
joydev                 17693  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_hda_intel          33719  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
wmi                    19256  1 hp_wmi
psmouse                97485  0 
serio_raw              13211  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
arc4                   12529  2 
rt2800pci              18715  0 
rt2800lib              58967  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
rt2x00pci              14620  1 rt2800pci
rt2x00lib              55326  5 rt73usb,rt2x00usb,rt2800pci,rt2800lib,rt2x00pci
mac80211              506862  4 rt2x00usb,rt2800lib,rt2x00pci,rt2x00lib
snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  477763  3 
rts_pstor             445241  0 
drm_kms_helper         46978  1 i915
drm                   241971  4 i915,drm_kms_helper
cfg80211              205774  2 rt2x00lib,mac80211
eeprom_93cx6           12767  1 rt2800pci
mac_hid                13253  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
video                  19651  1 i915
mei                    41616  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62154  0 



yuval@Ben-Yuval-Ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr ec:9a:74:4a:e8:5c  
          inet addr:192.168.1.31  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ee9a:74ff:fe4a:e85c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:254073 errors:0 dropped:0 overruns:0 frame:0
          TX packets:115398 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:361637213 (361.6 MB)  TX bytes:13126448 (13.1 MB)
          Interrupt:41 Base address:0xa000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5030 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5030 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:412847 (412.8 KB)  TX bytes:412847 (412.8 KB)


wlan0     Link encap:Ethernet  HWaddr e4:d5:3d:8b:27:19  
          inet6 addr: fe80::e6d5:3dff:fe8b:2719/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:15147 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11374 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19867217 (19.8 MB)  TX bytes:1957246 (1.9 MB)


yuval@Ben-Yuval-Ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: 7C:03:4C:BA:AE:53
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=15/70  Signal level=-95 dBm  
                    Encryption key:on
                    ESSID:"HOTBOXadi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000014389c03186
                    Extra: Last beacon: 12908ms ago
                    IE: Unknown: 0009484F54424F58616469
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16010D1600000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180203F00C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:23:69:C0:C3:2D
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"FATCAT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000028ccef2186
                    Extra: Last beacon: 444ms ago
                    IE: Unknown: 0006464154434154
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020204


eth0      Interface doesn't support scanning.




yuval@Ben-Yuval-Ubuntu:~$ dmesg | grep rt2
[   13.364183] rt2800pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.364229] rt2800pci 0000:01:00.0: setting latency timer to 64
[   13.404605] Registered led device: rt2800pci-phy0::radio
[   13.404665] Registered led device: rt2800pci-phy0::assoc
[   13.404719] Registered led device: rt2800pci-phy0::quality
[   91.124702] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
[  645.654146] phy3 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -19.
[  768.245767] phy4 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x30c0 with error -19.





```


Thanks.

---

### Post by praseodym on 2013-05-10
There is another driver loaded:
```

sudo modprobe -rfv rt73usb
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
echo "blacklist rt73usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Additionally, you can deactivate the power management:
```

sudo iwconfig wlan0 power off
```
I recommend pure WPA2-AES (CCMP) encryption.

---

### Post by yuvalf11 on 2013-05-10
> **praseodym said:**
> There is another driver loaded:
```

sudo modprobe -rfv rt73usb
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
echo "blacklist rt73usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Additionally, you can deactivate the power management:
```

sudo iwconfig wlan0 power off
```
I recommend pure WPA2-AES (CCMP) encryption.


Can you explain me what have I done here.
 When I had the wifi problem I used a wifi doungle of EDIMAX so I think that the rt73usb driver is used for the wifi doungle - if I'll need to use this doungle again, How do I remove he rt73usb driver from the black list?
For now your solution seems to work, the internal wifi is working just fine, and I hope it won't crash soon.

Praseodym, Thank you very much!
-Yuval.

[U]("http://ubuntuforums.org/member.php?u=1411497")pdate:
That solved the problem for a while (slower then it used to be), after half a hour the old problem appeared again. I really appreciated any assistance.
Thanks,
-Yuval,

---

### Post by praseodym on 2013-05-10
You can edit the file
```

gksu gedit /etc/modprobe.d/blacklist.conf
```
and remove the line with rt73usb. CHeck now with the internal card:
```

uname -a
lsmod
iwconfig
cat /etc/resolv.conf
route -n
sudo iwlist scan
```

---

### Post by yuvalf11 on 2013-05-10
```

yuval@Ben-Yuval-Ubuntu:~$ uname -a
Linux Ben-Yuval-Ubuntu 3.2.0-41-generic #66-Ubuntu SMP Thu Apr 25 03:27:11 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
yuval@Ben-Yuval-Ubuntu:~$ lsmod
Module                  Size  Used by
rt73usb                31735  0 
crc_itu_t              12707  1 rt73usb
rt2x00usb              20808  1 rt73usb
rt2800pci              18715  0 
rt2800lib              58967  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
rt2x00pci              14620  1 rt2800pci
rt2x00lib              55326  5 rt73usb,rt2x00usb,rt2800pci,rt2800lib,rt2x00pci
mac80211              506862  4 rt2x00usb,rt2800lib,rt2x00pci,rt2x00lib
cfg80211              205774  2 rt2x00lib,mac80211
eeprom_93cx6           12767  1 rt2800pci
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
parport_pc             32866  0 
rfcomm                 47604  0 
bnep                   18281  2 
ppdev                  17113  0 
bluetooth             180153  10 rfcomm,bnep
joydev                 17693  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_hda_intel          33719  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
wmi                    19256  1 hp_wmi
psmouse                97485  0 
serio_raw              13211  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
arc4                   12529  2 
snd                    79041  19 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  477763  4 
rts_pstor             445241  0 
drm_kms_helper         46978  1 i915
drm                   241971  5 i915,drm_kms_helper
mac_hid                13253  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
video                  19651  1 i915
mei                    41616  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62154  0 
yuval@Ben-Yuval-Ubuntu:~$ iwconfig
lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.


yuval@Ben-Yuval-Ubuntu:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
yuval@Ben-Yuval-Ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
yuval@Ben-Yuval-Ubuntu:~$ sudo iwlist scan
[sudo] password for yuval: 
lo        Interface doesn't support scanning.


wlan0     No scan results


eth0      Interface doesn't support scanning.


yuval@Ben-Yuval-Ubuntu:~$ 



```

---

### Post by praseodym on 2013-05-10
Try to compile this driver

[http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3473742](http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3473742)

First line should be:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
```
rt2800pci should be blacklisted, rt73usb still loaded?!

I do not know if it works with kernels>31

---

### Post by yuvalf11 on 2013-05-10
I don't speak dutch. Should I run the entire code?

---

### Post by praseodym on 2013-05-10
Its German ;)

Run the code in the black boxes via copy/paste, but not the last 2 lines
```

sudo dkms remove -m Ralink_5390sta -v 2.5.0.3 --all
sudo rm -r /var/lib/dkms/Ralink_5390sta/2.5.0.3 
```

these are for uninstallations.

---

### Post by yuvalf11 on 2013-05-10
I ran the code, and install that driver. It's still not working.
BTW, the rt73usb driver is for an external wifi doungle the I used when the internal wifi didn't work.

What do you advise to do now?
-Yuval.

---

### Post by yuvalf11 on 2013-05-10
I ran the entire code. it's still not working :(
what do you advise to do next?

BTW, the rt73usb driver is used for the external wifi doungle that I used when the I started to have the wifi problems.

Thanks,
-Yuval.

---

### Post by praseodym on 2013-05-10
Errors during the installation?

Check
```

iwconfig
lsmod
sudo iwlist scan
dmesg | egrep 'rt2|rt5'
```

---

### Post by yuvalf11 on 2013-05-10
When I asked you what to run I had a problem, (after the dhkm build) and then I deleted everything and install everything again and I didn't have any problems.
The output:

```

yuval@Ben-Yuval-Ubuntu:~$ iwconfig
lo        no wireless extensions.


ra0       Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.462 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=46/100  Signal level:-92 dBm  Noise level:-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


eth0      no wireless extensions.


yuval@Ben-Yuval-Ubuntu:~$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
joydev                 17693  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180153  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
psmouse                97485  0 
serio_raw              13211  0 
snd_hda_intel          33719  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
uvcvideo               72627  0 
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
videodev               98259  1 uvcvideo
rt5390sta            1349571  1 
v4l2_compat_ioctl32    17128  1 videodev
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
wmi                    19256  1 hp_wmi
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  477763  4 
mac_hid                13253  0 
drm_kms_helper         46978  1 i915
rts_pstor             445241  0 
drm                   241971  5 i915,drm_kms_helper
soundcore              15091  1 snd
i2c_algo_bit           13423  1 i915
video                  19651  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62154  0 
yuval@Ben-Yuval-Ubuntu:~$ sudo iwlist scan
[sudo] password for yuval: 
Sorry, try again.
[sudo] password for yuval: 
lo        Interface doesn't support scanning.


ra0       Scan completed :
          Cell 01 - Address: 7C:03:4C:BA:AE:53
                    Protocol:802.11b/g/n
                    ESSID:"HOTBOXadi"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=2/100  Signal level=-89 dBm  Noise level=-84 dBm
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102


eth0      Interface doesn't support scanning.


yuval@Ben-Yuval-Ubuntu:~$ dmesg | egrep 'rt2|rt5'
[ 5650.036410] <==== rt28xx_init, Status=0
[ 6434.150783] <==== rt28xx_init, Status=0
[ 6457.143592] <==== rt28xx_init, Status=0
[ 6933.600527] <==== rt28xx_init, Status=0
[ 7497.985760] <==== rt28xx_init, Status=0
[ 7673.810926] <==== rt28xx_init, Status=0
[ 7911.534560] <==== rt28xx_init, Status=0
[ 9458.833887] <==== rt28xx_init, Status=0
[ 9655.569531] <==== rt28xx_init, Status=0
[ 9851.370903] <==== rt28xx_init, Status=0
[10190.010977] <==== rt28xx_init, Status=0
[10211.952349] <==== rt28xx_init, Status=0
[10427.727386] <==== rt28xx_init, Status=0
[10913.183028] <==== rt28xx_init, Status=0
[11271.802955] <==== rt28xx_init, Status=0
[11458.639910] <==== rt28xx_init, Status=0
[11745.263964] <==== rt28xx_init, Status=0
[12429.532277] <==== rt28xx_init, Status=0
[12477.415816] <==== rt28xx_init, Status=0



```

Thanks!

---

### Post by praseodym on 2013-05-11
Great! Thanks for the info

---

### Post by yuvalf11 on 2013-05-11
I still have the wifi problem. Any advise?

Thanks,
-Yuval.

---

### Post by praseodym on 2013-05-12
Try pure WPA2-AES (CCMP) encryption in your router. Check after that
```

sudo iwlist scan
iwconfig
ifconfig -a
route -n
cat /etc/resolv.conf
```

---

