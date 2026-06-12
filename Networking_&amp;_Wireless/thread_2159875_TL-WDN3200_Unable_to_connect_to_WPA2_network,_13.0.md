---
title: "TL-WDN3200 Unable to connect to WPA2 network, 13.04"
date: 2013-07-04
forum: Networking &amp; Wireless
---

### Post by jonfan on 2013-07-04
Hi all,

recently reinstalled Ubuntu on my computer and I've been having a bit of a hard time getting my usb wireless adapter to play nice.

Background: it's a custom built desktop and I'm using the TP-Link WDN3200 N600 Wireless Adapter. I'm using a new, fresh install of Ubuntu 13.04

I followed the guide located here [http://www.ctheroux.com/2012/09/ralink-rt5572-based-wifi-usb-dongle-setup-on-ubuntu-12-04/](http://www.ctheroux.com/2012/09/ralink-rt5572-based-wifi-usb-dongle-setup-on-ubuntu-12-04/) and my system now detects the usb adapter and can detect networks.

But, like many others that I've seen, I cannot connect to my WPA2 secured network. I know many have asked this same topic, but I'm relatively inexperienced at this and some of the guides seemed to be outdated.


Thanks for any help you can give and I will update if I find a solution.

EDIT:

here's some more information:

the wireless adapter shows up as ra0.

lsusb gives
```
Bus 002 Device 004: ID 148f:5572 Ralink Technology, Corp.
```

iwconfig gives
```
ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-27 dBm  Noise level:-27 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ifconfig gives
```
ra0       Link encap:Ethernet  HWaddr a0:f3:c1:2a:61:c9            inet6 addr: fe80::a2f3:c1ff:fe2a:61c9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4599 errors:0 dropped:1 overruns:0 frame:0
          TX packets:2043 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:935816 (935.8 KB)  TX bytes:227683 (227.6 KB)

```

lsmod gives
```
Module                  Size  Used byrt5572sta             810831  1 
dm_crypt               22820  1 
bnep                   18036  2 
rfcomm                 42641  0 
bluetooth             228619  10 bnep,rfcomm
parport_pc             28152  0 
ppdev                  17073  0 
snd_hda_codec_hdmi     36913  2 
snd_hda_codec_realtek    78399  1 
snd_hda_intel          39619  12 
nvidia              11309139  50 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
coretemp               13355  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
kvm_intel             132891  0 
snd_rawmidi            30180  1 snd_seq_midi
kvm                   443165  1 kvm_intel
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
lp                     17759  0 
snd                    68876  33 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
parport                46345  3 lp,ppdev,parport_pc
mei                    41158  0 
soundcore              12680  1 snd
gpio_ich               13476  0 
mxm_wmi                13021  0 
microcode              22881  0 
serio_raw              13215  0 
joydev                 17377  0 
wmi                    19070  1 mxm_wmi
lpc_ich                17061  0 
mac_hid                13205  0 
pata_acpi              13038  0 
hid_logitech           26585  0 
ff_memless             13013  1 hid_logitech
hid_generic            12540  0 
usbhid                 47074  1 hid_logitech
hid                   101002  3 hid_generic,hid_logitech,usbhid
ghash_clmulni_intel    13259  0 
firewire_ohci          40103  0 
aesni_intel            55399  8406 
firewire_core          64508  1 firewire_ohci
i915                  600396  2 
crc_itu_t              12707  1 firewire_core
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  4 ghash_clmulni_intel,aesni_intel,ablk_helper
video                  19390  1 i915
i2c_algo_bit           13413  1 i915
drm_kms_helper         49394  1 i915
drm                   286028  3 i915,drm_kms_helper
r8169                  67446  0 
ahci                   25731  2 
libahci                31364  1 ahci

```

If I can provide any more information, please let me know!

---

### Post by jonfan on 2013-07-05
I've found some more guides on trying to fix this issue, but none of them seem to work for me, or end up in the person getting a new USB adapter.

I went ahead and ran lshw, here's the output

```

xxxxx@XXXXX:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168 PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 06
       serial: 50:e5:49:49:f2:07
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.100 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:44 ioport:ee00(size=256) memory:fbeff000-fbefffff memory:fbef8000-fbefbfff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: ra0
       serial: a0:f3:c1:2a:61:c9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN multicast=yes wireless=Ralink STA



```

Similar problem was found here [http://www.ubuntuforums.org/showthread.ph p?t=2158806]("http://www.ubuntuforums.org/showthread.php?t=2158806") I'm going to try and follow those steps.

---

