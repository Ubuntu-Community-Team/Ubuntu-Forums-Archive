---
title: "Atheros card vanished, no longer a net interface, was working before"
date: 2009-07-17
forum: Networking &amp; Wireless
---

### Post by vxbinaca on 2009-07-17
I'm running Jaunty 9.04 on a Toshiba A135-S2745 and have all the updates. At first I thought my problems were because I was using wicd as a network manager but I still get the same problem with network-manager.

The device is not being loaded as a network interface. Well it was it's just no longer being loaded as one.


sudo iwlist scanning
> 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

ifconfig -a
> 
eth0      Link encap:Ethernet  HWaddr 00:16:d4:fc:43:c1  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fefc:43c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:2508 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2354649 (2.3 MB)  TX bytes:319052 (319.0 KB)
          Interrupt:252 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

pan0      Link encap:Ethernet  HWaddr e6:e3:9a:35:05:9c  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


The relevant lshw listing:

> 
           *-network UNCLAIMED
                description: Ethernet controller
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0



lsmod:
> 
Module                  Size  Used by
i915                   65668  2 
drm                    96296  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         434100  6 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
mmc_block              17668  0 
snd_pcm                82948  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia                 44748  0 
tifm_sd                17928  0 
snd_timer              29704  2 snd_pcm,snd_seq
psmouse                61972  0 
tifm_7xx1              13824  0 
pcspkr                 10496  0 
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
serio_raw              13316  0 
sdhci_pci              15232  0 
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
tifm_core              15900  2 tifm_sd,tifm_7xx1
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sdhci                  23940  1 sdhci_pci
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
snd                    62628  20 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
input_polldev          11912  0 
video                  25360  0 
intel_agp              34108  1 
output                 11008  1 video
agpgart                42696  3 drm,intel_agp
sha256_generic         20352  0 
aes_i586               15744  2 
aes_generic            35880  1 aes_i586
cbc                    11648  1 
usbhid                 42336  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
r8169                  40836  0 
mii                    13312  1 r8169
dm_crypt               20996  1 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit


---

### Post by vxbinaca on 2009-07-17
Found it!

It's not loading the following kernel modules:

ath5k
mac80211
led-class

Once manually loaded wireless returns.

Problem is theres no crypto capability. I can't connect to any AP requiring a password.

How do I get these to automatically start loading again?

---

