---
title: "Realtek Network Card/Ubuntu 10.10 64bit/Toshiba Satellite A665-S6065"
date: 2010-12-18
forum: Networking &amp; Wireless
---

### Post by Habib CB on 2010-12-18
Note: Please keep in mind that Im not english speaker xD
Hello, Im a new Linux user, I have just installed Ubuntu 10.10 64bit on my laptop Toshiba Satellite A665-S6065 and I can connect to wired network but I can not connect to wireless network "Network Connections disconnected". Im following this post [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

1. Machine Brand and Model (PC/Laptop): Toshiba Satellite A665-S6065
2. Wireless Brand, Model and Wireless Chipset:
```
 lspci
```Output:
```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)

``````
 lspci -nn
```Output
```
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
```3. Check interface:
```
ifconfig
```Output
```
eth0      Link encap:Ethernet  HWaddr 88:ae:1d:52:de:6a  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::8aae:1dff:fe52:de6a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3092 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2718 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3732010 (3.7 MB)  TX bytes:361909 (361.9 KB)
          Interrupt:51 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 70:f1:a1:fe:f9:e8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:ffffc90012100000-ffffc90012100100 
``````
iwconfig
```Output
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.447 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```4. Check for modules:
```
lsmod
```Output
```
Module                  Size  Used by
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
nvidia              10221046  40 
snd_hda_codec_nvhdmi    15451  4 
joydev                 11363  0 
snd_hda_codec_realtek   299524  1 
snd_hda_intel          26019  2 
snd_hda_codec         100919  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_seq_midi            5932  0 
snd_hwdep               6660  1 snd_hda_codec
snd_rawmidi            22207  1 snd_seq_midi
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
uvcvideo               62379  0 
lp                     10201  0 
psmouse                62080  0 
video                  22176  0 
videodev               49359  1 uvcvideo
output                  2527  1 video
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               4910  0 
i7core_edac            18090  0 
parport                37032  3 parport_pc,ppdev,lp
edac_core              46822  1 i7core_edac
jmb38x_ms               8667  0 
memstick               10185  1 jmb38x_ms
snd                    64117  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12486  1 videodev
r8192se_pci           507324  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
usbhid                 42062  0 
hid                    84678  1 usbhid
ahci                   21857  0 
libahci                26199  3 ahci
r8169                  42222  0 
sdhci_pci               7765  0 
sdhci                  18400  1 sdhci_pci
led_class               3393  1 sdhci
mii                     5261  1 r8169

```5. Kernel boot messages: (dmesg) Should I post this output (is veeery big!) ?

6. Network configuration:
```
sudo lshw -C network
```Output
```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: 88:ae:1d:52:de:6a
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.11 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:51 ioport:7000(size=256) memory:d3104000-d3104fff memory:d3100000-d3103fff
  *-network
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 10
       serial: 70:f1:a1:fe:f9:e8
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0017.0507.2010 firmware=63 latency=0 link=no multicast=yes wireless=802.11bgn
       resources: irq:17 ioport:5000(size=256) memory:d7300000-d7303fff
```7. Scan for networks:
```
iwlist scan
```Output
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :

```8. Ubuntu version: Ubuntu 10.10 64bit

9. Kernel/architecture (including 32 vs. 64 bit):
```
uname -mr
```Output
```
2.6.35-23-generic x86_64
```10. Restarting the network:
```
sudo /etc/init.d/networking restart
```Output
```
 * Reconfiguring network interfaces...                                                                                                                                  Ignoring unknown interface eth0=eth0.
```What can I do to connect wireless?
**Thanks for reading and for the help!!**

---

### Post by Habib CB on 2010-12-18
Help please :(

---

### Post by Habib CB on 2010-12-18
No body?

---

### Post by Habib CB on 2010-12-18
...

---

