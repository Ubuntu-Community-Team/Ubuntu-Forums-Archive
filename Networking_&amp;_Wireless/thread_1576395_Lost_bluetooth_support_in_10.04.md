---
title: "Lost bluetooth support in 10.04"
date: 2010-09-17
forum: Networking &amp; Wireless
---

### Post by andi99 on 2010-09-17
Hi All!

I upgraded my netbook (HP Mini 5101) from 9.10 to 10.04 yesterday. Everthing (including bluetooth) seemed to work, as it did before. Today I tried to install a 2.6.35 kernel from maverick backports (the kernel ppa), but it didn't work for me and I removed it again. Now my bluetooth is gone (bluetooth applet does not show any devices)  but wireless still works. 

I already tried to remove and reinstall the driver package via apt-get (sudo apt-get un/install bcmwl-kernel-source bcmwl-modaliases) but nothing helped.

Any help would be appreciated. 

Thanks!

Here some additional information:

lspci -v
```

08:00.0 Network controller: Broadcom Corporation Device 4353 (rev 01)
    Subsystem: Hewlett-Packard Company Device 1510
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at e8000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: w
l
```lsb_release -d
```
Description:    Ubuntu 10.04.1 LTS
```uname -mr
```

2.6.32-24-generic i686

```lsmod
```

Module                  Size  Used by
aes_i586                7268  153 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
ppdev                   5259  0 
ipt_REJECT              1928  1 
xt_limit                1382  1 
xt_tcpudp               2011  9 
ipt_addrtype            1631  4 
xt_state                1098  6 
dm_crypt               11331  0 
snd_hda_codec_analog    58598  1 
ip6table_filter         2343  1 
ip6_tables             11227  1 ip6table_filter
nf_nat_irc              1124  0 
nf_conntrack_irc        3332  1 nf_nat_irc
nf_nat_ftp              1836  0 
nf_nat                 15735  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      10672  8 nf_nat
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
nf_conntrack_ftp        5381  1 nf_nat_ftp
nf_conntrack           61583  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_hda_intel          21941  2 
snd_hda_codec          74201  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
iptable_filter          2271  1 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
ip_tables               9991  1 iptable_filter
x_tables               14299  7 ipt_REJECT,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                  8708  0 
lib80211_crypt_tkip     7596  0 
uvcvideo               56990  0 
snd                    54148  16 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
psmouse                63245  0 
serio_raw               3978  0 
hp_accel               11144  0 
wl                   1959598  0 
lis3lv02d               6096  1 hp_accel
input_polldev           2482  1 lis3lv02d
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
led_class               2864  1 hp_accel
lib80211                5046  2 lib80211_crypt_tkip,wl
lp                      7028  0 
parport                32635  2 ppdev,lp
fbcon                  35102  71 

```sudo lshw -C network
```

  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth2
       version: 01
       serial: 00:26:82:1b:b8:00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:16 memory:e8000000-e8003fff

```ifconfig
```

eth2      Link encap:Ethernet  HWaddr 00:26:82:1b:b8:00  
          inet6 addr: fe80::226:82ff:fe1b:b800/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:643
          TX packets:0 errors:2 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 
```

---

### Post by andi99 on 2010-09-17
Hi folks!

Problem solved! I really don't know what did the trick. Here is the story (as far as I remember):

My guess: Perhaps kernel sources are installed before modaliases and my device is not recognized?

removed bcmwl-kernel-source and bcmwl-modaliases
reboot
installed bcmwl-modaliases
reboot
installed bcmwl-kernel-source
reboot
reinstalled bluez and bluetooth service
reboot
installed blueman

bluetooth service was running by now but no bluetooth device was found. In 9.10 (and yesterday evening even unter 10.04) there was a "Bluetooth" app in the system preferences. After installing blueman there was a "Bluetooth Manager" app. When starting Bluetooth Manager my device was finally recongnized and everything is back to normal.

CU ):P

---

### Post by GIGABYTEXXL on 2010-11-19
did you use synaptic manager too remove and reinstall blue tooth? after my first clean install my bluetooth was working fine. now suddenly the adapter is no longer installed or recognized.

it simply disappeared one day, no icon at the top and the blueman app says no bluetooth adapter is installed. if i boot into windows 7 it works fine.

---

