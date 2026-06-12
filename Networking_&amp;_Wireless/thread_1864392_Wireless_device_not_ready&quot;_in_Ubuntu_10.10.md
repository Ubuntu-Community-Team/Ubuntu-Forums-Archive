---
title: "Wireless device not ready&quot; in Ubuntu 10.10"
date: 2011-10-18
forum: Networking &amp; Wireless
---

### Post by SyncMr on 2011-10-18
Hi,

I am using Ubuntu 10.10 on Lenovo Z575 laptop. At times (rarely) my wireless connection works fine but most times the I could see "Wireless device is not ready" on clicking the wireless icon.

But I am able to connect through wired connection. Also my wifi works perfectly in Windows 7.

Here are the output of few commands. Kindly help in solving the problem. 

Output of iwconfig:
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```Output of sudo lshw -c network:
```

sudo lshw -c network
[sudo] password for prag: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: f0:de:f1:77:55:1d
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.2.4 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:42 ioport:1000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network DISABLED
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 38:59:f9:ab:f3:13
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.35-30-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f0100000-f010ffff

```Output of : lsmod
```

lsmod
Module                  Size  Used by
parport_pc             26058  0 
ppdev                   5556  0 
binfmt_misc             6599  1 
joydev                  8767  0 
snd_hda_codec_realtek   218460  1 
snd_hda_codec_atihdmi     2411  1 
snd_hda_intel          22235  2 
rt2860sta             504366  0 
snd_hda_codec          87552  3 snd_hda_codec_realtek,snd_hda_codec_atihdmi,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
arc4                    1165  2 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
rt2800pci               8852  0 
rt2800lib              28961  1 rt2800pci
rt2x00usb               9779  1 rt2800lib
rt2x00pci               6029  1 rt2800pci
snd_seq_midi_event      6047  1 snd_seq_midi
crc_ccitt               1351  2 rt2860sta,rt2800pci
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
rt2x00lib              27307  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
mac80211              231927  3 rt2x00usb,rt2x00pci,rt2x00lib
acer_wmi               13929  0 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55911  0 
led_class               2633  2 rt2x00lib,acer_wmi
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
video                  18712  0 
cfg80211              144790  2 rt2x00lib,mac80211
psmouse                59033  0 
output                  1883  1 video
snd                    49102  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               4022  0 
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
i2c_piix4               8635  0 
eeprom_93cx6            1345  1 rt2800pci
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
ahci                   19326  2 
libahci                21728  1 ahci
r8169                  36553  0 
mii                     4425  1 r8169

```Output of iwlist scan
```

iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

```Kernel Archi: 2.6.35-30-generic i686

---

### Post by chili555 on 2011-10-18
Please try this in a terminal:```
sudo su
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us have your report. Thanks.

---

### Post by SyncMr on 2011-10-18
Thanks a lot. It worked. :)

---

