---
title: "Cannot find my wireless network in Ubuntu"
date: 2012-11-04
forum: Networking &amp; Wireless
---

### Post by Malondron on 2012-11-04
Hi,

I have installed Ubuntu 12.04 as a dual boot with my Windows 7.

When running from the LiveCD, my wireless network could be found and I used it then. After installation, my network does not appear in the list of networks, although a large number of others do.

I tried again with the LiveCD, but it now fails as well.

Information:

1) Acer Aspire 5742G

2) 03:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)

3) eth0      Link encap:Ethernet  HWaddr 88:ae:1d:a6:6d:c8  
          inet addr:192.168.0.193  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::8aae:1dff:fea6:6dc8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5387 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4127 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5708925 (5.7 MB)  TX bytes:602278 (602.2 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 4c:0f:6e:8f:8e:0a  
          inet6 addr: fe80::4e0f:6eff:fe8f:8e0a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:270 errors:0 dropped:0 overruns:0 frame:0
          TX packets:270 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27941 (27.9 KB)  TX bytes:27941 (27.9 KB)

4) hidp                   22628  0 
dm_crypt               23125  1 
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  12 
bnep                   18281  2 
joydev                 17693  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224173  1 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_seq_midi           13324  0 
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
lib80211_crypt_tkip    17390  0 
wl                   2568210  0 
btusb                  18288  2 
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
mei                    41616  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
bluetooth             180104  24 hidp,rfcomm,bnep,btusb
lib80211               14381  2 lib80211_crypt_tkip,wl
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
acer_wmi               28418  0 
v4l2_compat_ioctl32    17128  1 videodev
sparse_keymap          13890  1 acer_wmi
psmouse                97443  0 
serio_raw              13211  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
radeon                804460  3 
ttm                    76949  1 radeon
drm_kms_helper         46978  1 radeon
drm                   241921  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13423  1 radeon
tg3                   152032  0 
usbhid                 47199  0 
hid                    99559  2 hidp,usbhid
mxm_wmi                12979  0 
video                  19596  0 
wmi                    19256  2 acer_wmi,mxm_wmi

5) too long to paste, attached

6)  *-network               
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 88:ae:1d:a6:6d:c8
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=sb ip=192.168.0.193 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:46 memory:b3000000-b300ffff
  *-network
       description: Wireless interface
       product: BCM43225 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 4c:0f:6e:8f:8e:0a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:b2000000-b2003fff

7)
  
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


8) Description:    Ubuntu 12.04.1 LTS

9) 3.2.0-32-generic x86_64
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                Ignoring unknown interface eth0=eth0.



I have tried a number of things from different forums, but nothing have helped so far, and I know very little about wireless networks, so I need help.

Thank you for your attention.

Best regards,

Andreas
10)

---

### Post by Malondron on 2012-11-05
It turned out I got bitten by the infamous WIFI on channel > 11 bug.

This has now been rectified.

Andreas

---

