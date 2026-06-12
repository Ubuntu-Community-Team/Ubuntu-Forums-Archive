---
title: "TP-Link Network card TF3200 with Ubuntu 12.04 connection problems"
date: 2012-12-01
forum: Networking &amp; Wireless
---

### Post by ras123 on 2012-12-01
Hi,
Since my motherboards LAN card damaged, installed a new TP-Link TF3200 network card in PCI slot. Now I couldn't connect to Internet using this (in windows it is working), the network manager shows as both "Wired Network" and "device is not ready" as inactive link.  By using editing network link in network manager I can add a device with a mac address with eth1 tag, but no connection.
Do I need to install driver?  but I think it is already with ubuntu 12.04, some info are provided below,
> modinfo sundance
filename:       /lib/modules/3.2.0-33-generic-pae/kernel/drivers/net/ethernet/dlink/sundance.ko
license:        GPL
description:    Sundance Alta Ethernet driver
author:         Donald Becker <becker@scyld.com>
srcversion:     76069AF61EE953600C1E625
alias:          pci:v000013F0d00000200sv*sd*bc*sc*i*
alias:          pci:v000013F0d00000201sv*sd*bc*sc*i*
alias:          pci:v00001186d00001002sv*sd*bc*sc*i*
alias:          pci:v00001186d00001002sv00001186sd00001040bc*sc*i*
alias:          pci:v00001186d00001002sv00001186sd00001012bc*sc*i*
alias:          pci:v00001186d00001002sv00001186sd00001003bc*sc*i*
alias:          pci:v00001186d00001002sv00001186sd00001002bc*sc*i*
depends:        
intree:         Y
vermagic:       3.2.0-33-generic-pae SMP mod_unload modversions 686 
parm:           media:array of charp
parm:           debug:Sundance Alta debug level (0-5) (int)
parm:           rx_copybreak:Sundance Alta copy breakpoint for copy-only-tiny-frames (int)
parm:           flowctrl:Sundance Alta flow control [0|1] (int)
and  sudo modprobe sundance returns nothing

Thanking You,
Ras

---

### Post by praseodym on 2012-12-01
Please show the following outputs:

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```

---

### Post by ras123 on 2012-12-01
The results are given below,
> 
 lspci -nnk | grep -iA2 net
02:05.0 Ethernet controller [0200]: Sundance Technology Inc / IC Plus Corp IC Plus IP100A Integrated 10/100 Ethernet MAC + PHY [13f0:0200] (rev 31)
    Subsystem: Sundance Technology Inc / IC Plus Corp Device [13f0:0201]
    Kernel driver in use: sundance


lin@lin:~$ lsmod
Module                  Size  Used by
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
ufs                    78131  0 
qnx4                   13309  0 
hfsplus                83507  0 
hfs                    49479  0 
minix                  31418  0 
ntfs                  100171  0 
msdos                  17132  0 
jfs                   175085  0 
xfs                   747494  0 
reiserfs              230896  0 
ext2                   67987  0 
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55605  2 msdos,vfat
uas                    17828  0 
usb_storage            39646  0 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
arc4                   12473  2 
snd_hda_codec_hdmi     31775  1 
ppdev                  12849  0 
rt2800usb              22373  0 
rt2800lib              53264  1 rt2800usb
crc_ccitt              12595  1 rt2800lib
rt2x00usb              20061  1 rt2800usb
rt2x00lib              48836  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              436455  3 rt2800lib,rt2x00usb,rt2x00lib
snd_usb_audio         101566  1 
cfg80211              178679  2 rt2x00lib,mac80211
snd_hda_codec_via      46138  1 
snd_hda_intel          32765  4 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_pcm                80845  4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_hwdep              13276  2 snd_usb_audio,snd_hda_codec
snd_usbmidi_lib        24603  1 snd_usb_audio
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_rawmidi            25424  2 snd_usbmidi_lib,snd_seq_midi
serio_raw              13027  0 
k10temp                12990  0 
sp5100_tco             13495  0 
i2c_piix4              13093  0 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_seq,snd_rawmidi
snd                    62064  22 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_seq,snd_rawmidi,snd_timer,snd_seq_device
radeon                737926  3 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197599  5 radeon,ttm,drm_kms_helper
parport_pc             32114  1 
soundcore              14635  1 snd
i2c_algo_bit           13199  1 radeon
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
asus_atk0110           17742  0 
shpchp                 32325  0 
wmi                    18744  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41906  0 
hid                    77392  1 usbhid
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sundance               26629  0 
pata_atiixp            12999  0 


lin@lin:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

          
lin@lin:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no



---

### Post by praseodym on 2012-12-02
Ok,

I thought it is wireless. Please show:

```
cat /etc/udev/rules.d/70-persistent-net.rules
ifconfig -a
cat /etc/resolv.conf
cat /etc/network/interfaces
```

---

### Post by ras123 on 2012-12-02
The results are
> 
lin@lin:~$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:0a.0/0000:02:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="90:e6:ba:bd:67:53", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x148f:0x2070 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="b0:48:7a:8f:72:3b", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x13f0:/sys/devices/pci0000:00/0000:00:14.4/0000:02:05.0 (sundance)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="64:70:02:04:e8:c8", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


lin@lin:~$ ifconfig -a
eth1      Link encap:Ethernet  HWaddr 64:70:02:04:e8:c8  
          inet6 addr: fe80::6670:2ff:fe04:e8c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:23
          collisions:0 txqueuelen:1000 
          RX bytes:172 (172.0 B)  TX bytes:4260 (4.2 KB)
          Interrupt:20 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:857 errors:0 dropped:0 overruns:0 frame:0
          TX packets:857 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:111775 (111.7 KB)  TX bytes:111775 (111.7 KB)

wlan0     Link encap:Ethernet  HWaddr b0:48:7a:8f:72:3b  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:38235 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26382 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49751651 (49.7 MB)  TX bytes:2529081 (2.5 MB)

lin@lin:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1

lin@lin:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback



---

### Post by ras123 on 2012-12-06
Any solution?

---

### Post by ras123 on 2013-01-28
bump

---

