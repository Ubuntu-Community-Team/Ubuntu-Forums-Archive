---
title: "RALINK USB wireless LAN adaptor not answering ARPs"
date: 2009-11-27
forum: Networking &amp; Wireless
---

### Post by bobg-m on 2009-11-27
Hi, I have a problem with a Kubuntu 9.10 Twin Intel Celeron E1400 system at 2GHz with 1G RAM. The system is running over wireless LAN. I have a RALINK USB WLAN external stick, and the network is configured at boot from an entry in /etc/network/interfaces.

The system joins the network fine at boot and has a rock-steady connection. Outgoing connections work great, no problem at all.

Inbound connections (I use port 80 for mythweb and 22 for ssh) have the symptom that occasionally a connection is not established. Having explored with wireshark, it is clear that ARP queries to this system are often not answered. All other packet types appear ok. When attempting to connect from another local system on my LAN I get 'no path to host' as the local system cannot resolve the IP address to a MAC. Adding the MAC to the local system's cache manually solves the issue 100% repeatedly.
```

sudo  arp -s cuthred 00:1f:1f:08:71:be
```

It's using the rt73usb driver as [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) implies it should. Occasionally, and without any apparent cause, it'll start answering ARPs again and all will be well. The symptoms don't appear to be tied to rebooting, or busyness of the network, or overlapping channels with other WLANs etc. Does anyone have any ideas?

```
bob@cuthred:~$ uname -a
Linux cuthred 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux
```



```
bob@cuthred:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:09.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
03:09.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)

```
lshw gives
```
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1f:1f:08:71:be
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.5 multicast=yes wireless=IEEE 802.11bg
```

```
bob@cuthred:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 2040:8400 Hauppauge
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1c6b:a120 Philips & Lite-ON Digital Solutions Corporation
Bus 001 Device 003: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

```
bob@cuthred:~$ more /etc/network/interfaces
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-psk <my hashed wpa-psk key as produced by wpa_passphrase>
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid prx56sw
```


```
bob@cuthred:~$ lsmod                                                                                                                                              
Module                  Size  Used by                                                                                                                             
snd_hda_codec_realtek   277860  1                                                                                                                                 
snd_hda_intel          31880  2                                                                                                                                   
snd_hda_codec          87584  2 snd_hda_codec_realtek,snd_hda_intel                                                                                               
snd_hwdep               9352  1 snd_hda_codec                                                                                                                     
snd_pcm_oss            44704  0                                                                                                                                   
snd_mixer_oss          18976  1 snd_pcm_oss                                                                                                                       
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss                                                                                           
snd_seq_dummy           3460  0                                                                                                                                   
snd_seq_oss            33440  0                                                                                                                                   
snd_seq_midi            8192  0                                                                                                                                   
snd_rawmidi            27360  1 snd_seq_midi                                                                                                                      
arc4                    2144  2                                                                                                                                   
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi                                                                                                          
iptable_filter          3872  0                                                                                                                                   
ecb                     3296  2                                                                                                                                   
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event                                                                         
ip_tables              21200  1 iptable_filter                                                                                                                    
rt73usb                29092  0                                                                                                                                   
snd_timer              26992  2 snd_pcm,snd_seq                                                                                                                   
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
crc_itu_t               2336  1 rt73usb
x_tables               25832  1 ip_tables
rt2500usb              23364  0
dvb_usb_dib0700        58184  33
dib7000p               19272  3 dvb_usb_dib0700
dib7000m               16836  1 dvb_usb_dib0700
dvb_usb                19276  1 dvb_usb_dib0700
dvb_core              104528  1 dvb_usb
dib3000mc              14344  1 dvb_usb_dib0700
rt2x00usb              13600  2 rt73usb,rt2500usb
rt2x00lib              34624  3 rt73usb,rt2500usb,rt2x00usb
led_class               5256  1 rt2x00lib
snd                    77096  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
input_polldev           4720  1 rt2x00lib
joydev                 13088  0
mac80211              210104  2 rt2x00usb,rt2x00lib
dibx000_common          4196  3 dib7000p,dib7000m,dib3000mc
soundcore               9088  1 snd
dib0070                 8868  3 dvb_usb_dib0700
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
hid_logitech           10112  0
cfg80211              109144  2 rt2x00lib,mac80211
lp                     11908  0
psmouse                57124  0
ff_memless              6504  1 hid_logitech
serio_raw               6596  0
usbhid                 43968  1 hid_logitech
ppdev                   8232  0
parport_pc             37352  1
parport                40528  3 lp,ppdev,parport_pc
usb_storage            65952  0
fbcon                  41344  72
tileblit                3136  1 fbcon
font                    8832  1 fbcon
bitblit                 6688  1 fbcon
softcursor              2336  1 bitblit
sky2                   55556  0
i915                  246984  2
drm                   193856  2 i915
i2c_algo_bit            7076  1 i915
intel_agp              32816  2 i915
video                  23612  1 i915
output                  3680  1 video
```

Any ideas as to what I should try next?

---

### Post by Nekos on 2009-11-30
Same problem here, the system occasionally doesn't answer to arp request

arp -s IP MAC fix the problem but isn't a final solution.

Bus 001 Device 002: ID 07d1:3c03 D-Link System DWL-G122 802.11g Adapter [ralink rt73]

2.6.31-15-generic-pae #50-Ubuntu SMP Tue Nov 10 16:12:10 UTC 2009 i686 GNU/Linux

seems to be a bug of rt73usb driver

---

### Post by bobg-m on 2009-11-30
Yes, I suspected as much. Looks like I need to get onto RALINK. Any other evidence from people using other devices and the same driver?

---

### Post by bobg-m on 2011-02-20
OK, I've changed my DSL Router to a TP_Link device, and the problem appears to have gone away. SO I assume this is some incompatibility between Netgear and RA-Link. It's not clear to me on which side the bug resides.

---

