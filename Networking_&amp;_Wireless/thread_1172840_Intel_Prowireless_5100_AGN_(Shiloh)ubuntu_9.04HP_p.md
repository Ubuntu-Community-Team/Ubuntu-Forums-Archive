---
title: "Intel Pro/wireless 5100 AGN (Shiloh)/ubuntu 9.04/HP pavilion dv5 laptop"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by WhatAGuy on 2009-05-29
Hello. I am having a problem with my built in wireless card on my new laptop. As of right now i have vista ubuntu duel booted on this system, in vista the wireless works perfect, in ubuntu not so much.
At first the wireless button was shut off(little orange touch button),but after installing compat-wireless-2009-05-28, know i can turn the little button to blue, which means that its on. But i still can not pickup any networks.

1) HP pavilion dv5 laptop

2)02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection

3) wlan0     Link encap:Ethernet  HWaddr 00:22:fa:b1:9a:a8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

4)Module                  Size  Used by
i915                   65540  2 
drm                    96296  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bnep                   20224  2 
ipt_MASQUERADE         10752  1 
iptable_nat            13700  1 
nf_nat                 25876  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      21388  4 iptable_nat,nf_nat
nf_defrag_ipv4          9984  1 nf_conntrack_ipv4
xt_state               10112  1 
nf_conntrack           72008  5 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4,xt_state
ipt_REJECT             11136  2 
xt_tcpudp              11008  4 
iptable_filter         10752  1 
ip_tables              19472  2 iptable_nat,iptable_filter
x_tables               23044  6 ipt_MASQUERADE,iptable_nat,xt_state,ipt_REJECT,xt_tcpudp,ip_tables
bridge                 56340  0 
stp                    10500  1 bridge
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
arc4                    9856  2 
ecb                    10752  2 
iwlagn                123776  0 
iwlcore               125956  1 iwlagn
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
mac80211              224040  2 iwlagn,iwlcore
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
cfg80211               92448  2 iwlcore,mac80211
leds_hp_disk           10756  0 
led_class              12036  2 iwlcore,leds_hp_disk
snd_seq_oss            37760  0 
uvcvideo               63240  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                 18368  0 
compat_ioctl32          9344  1 uvcvideo
psmouse                61972  0 
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               41600  1 uvcvideo
serio_raw              13316  0 
pcspkr                 10496  0 
soundcore              15200  1 snd
v4l1_compat            21764  2 uvcvideo,videodev
video                  25360  0 
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
intel_agp              34108  1 
btusb                  19608  2 
output                 11008  1 video
lis3lv02d              17848  0 
agpgart                42696  3 drm,intel_agp
usb_storage            82880  0 
r8169                  40836  0 
mii                    13312  1 r8169
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

5) so much info, if need ill post

6)*-network               
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 00
       serial: 00:22:fa:b1:9a:a8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn

7)lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Failed to read scan data : Resource temporarily unavailable

virbr0    Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

8) na

9) 2.6.28-11-generic i686

10)  * Reconfiguring network interfaces...                                                                                                                       Ignoring unknown interface eth0=eth0.
                                                                                                                                                      [ OK ]

Alright thats all the information i know to give, if you need anyhting else just ask. And thankyou for your time guys you all do great work on this forum.

---

