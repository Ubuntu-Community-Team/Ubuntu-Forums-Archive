---
title: "hp 620 wireless lan not working"
date: 2011-08-06
forum: Networking &amp; Wireless
---

### Post by hampsterr on 2011-08-06
hi,
i installed ubuntu 10.04 in my laptop hp 620 and wired connection is working but wireless is not working at all.

i checked the old posts and when i enter the command "iwconfig" it shows the following:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

i read in the older posts that the "Access Point: Not-Associated" should be "Access Point: Invalid" and the command that is used for this purpose is " sudo iwconfig wlan0 ap auto"
and it did work-but for sometime, and again it showed me "not associated" when i restarted.

---> and according to an older forum, it says that the MODE should be MASTER instead of MANAGED, and i don't know how i can change it, kindly help me please, i don't wana miss it..

---

### Post by hampsterr on 2011-08-06
and will it work on ubuntu 11.04?

and how can i check my network adopter make and model?

---

### Post by wildmanne39 on 2011-08-06
Hi, run these commands in a terminal please:
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
rfkill list all
```
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by ambrosze on 2011-08-12
hi all,

i have the same issue as hampsterr (HP 620 on ubuntu 11.04) but the output from **iwconfig** is

[I]lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11bgn  ESSID:off/any 
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off  
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on[/I]


**sudo lshw -C network output**

[I]*-network DISABLED      
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: e0:2a:82:51:80:68
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-10-generic firmware=0.11 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d8800000-d880ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:85:00.0
       logical name: eth0
       version: 02
       serial: 64:31:50:83:57:25
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:45 ioport:2000(size=256) memory:d0410000-d0410fff memory:d0400000-d040ffff memory:d0420000-d043ffff
[/I]


**lspci -nn | grep 0280 **output is 

*02:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]*


**rfkill list all** output is

0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no


**lsmod** output

[I]ambrose@ambrose-HP-620:~$ lsmod
Module                  Size  Used by
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_idt      71137  1 
joydev                 17606  0 
rt2860sta             543010  0 
arc4                   12529  2 
snd_hda_intel          33211  2 
rt2800pci              18487  0 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
binfmt_misc            17565  1 
snd_hwdep              13604  1 snd_hda_codec
rt2800lib              45181  1 rt2800pci
crc_ccitt              12667  2 rt2860sta,rt2800lib
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rt2x00pci              14322  1 rt2800pci
rt2x00lib              49235  3 rt2800pci,rt2800lib,rt2x00pci
hp_wmi                 13706  0 
sparse_keymap          13898  1 hp_wmi
snd_seq_midi           13324  0 
mac80211              294370  3 rt2800lib,rt2x00pci,rt2x00lib
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
i915                  514975  3 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73535  0 
serio_raw              13166  0 
uvcvideo               72195  0 
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              178528  2 rt2x00lib,mac80211
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
eeprom_93cx6           12725  1 rt2800pci
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm_kms_helper         42136  1 i915
drm                   227495  4 i915,drm_kms_helper
i2c_algo_bit           13400  1 i915
video                  19438  1 i915
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  2 
libahci                26642  1 ahci
r8169                  48022  0 
[/I]

I would be grateful if someone out there can help me resolve this issue.

Note that - the wifi/ wireless/ bluetooth indicator light is flicking white - orange.

---

