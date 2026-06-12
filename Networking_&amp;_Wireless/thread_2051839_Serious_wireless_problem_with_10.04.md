---
title: "Serious wireless problem with 10.04"
date: 2012-09-02
forum: Networking &amp; Wireless
---

### Post by Renshu on 2012-09-02
Hello all,

Recently I upgraded my kernel to 2.6.32-42-generic-pae and all of a sudden my wireless can't seem to stay connected for an extended amount of time. 
I seems to drop in and out. 

Also quite recently my computer freezes when trying to work the network manager. 

I am runnning 10.04 on a Lenovo L512 Thinkpad, if anyone has any advice I would greatly appreciate it. 

I am considering upgrading to 12.04 , but at the same time I would like to 
maintain what I have here for one more year if possible since I do not want to devote time and energy reinstalling. 

Thanks 

Renshu ):P

---

### Post by raja.genupula on 2012-09-02
```
uname -mr
```

 ```
lspci -nnk | grep -iA2 net
```

 ```
lsmod
```

 ```
dmesg | grep -i wlan
```

 ```
ifconfig -a
```

 ```
iwconfig
```

 ```
rfkill list all
```
do those things from your terminal and post the output here .

---

### Post by steeldriver on 2012-09-02
*n/m - raja asked all the questions*

---

### Post by Renshu on 2012-09-03
Thanks for the quick response :). I will post this asap!

---

### Post by Renshu on 2012-09-03
```
uname -mr
```2.6.32-42-generic-pae i686

```
lspci -nnk | grep -iA2 net
```03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8172] (rev 10)
    Kernel driver in use: rtl819xSE
    Kernel modules: r8192se_pci
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
    Kernel driver in use: r8169
    Kernel modules: r8169


```
lsmod
```Module                  Size  Used by
michael_mic             1732  4 
arc4                    1153  2 
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
ppdev                   5259  0 
pci_stub                1102  1 
vboxpci                14595  0 
vboxnetadp             19352  0 
vboxnetflt             16780  0 
vboxdrv               252036  3 vboxpci,vboxnetadp,vboxnetflt
ipt_MASQUERADE          1407  3 
iptable_nat             4414  1 
nf_nat                 15735  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      10672  4 iptable_nat,nf_nat
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
xt_state                1098  1 
nf_conntrack           61615  5 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4,xt_state
ipt_REJECT              1928  2 
xt_tcpudp               2011  4 
iptable_filter          2271  1 
ip_tables               9991  2 iptable_nat,iptable_filter
x_tables               14299  6 ipt_MASQUERADE,iptable_nat,xt_state,ipt_REJECT,xt_tcpudp,ip_tables
bridge                 45678  0 
stp                     1655  1 bridge
kvm_intel              39448  0 
kvm                   246484  1 kvm_intel
joydev                  8740  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_codec_intelhdmi    11622  1 
snd_hda_codec_realtek   203472  1 
jmb38x_xd               7446  0 
jmb38x_ms              11185  0 
xd_card                28886  1 jmb38x_xd
i915                  291572  3 
snd_hda_intel          22165  2 
snd_hda_codec          74297  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70918  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
uvcvideo               57470  0 
snd_seq_midi            4557  0 
videodev               34457  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         29329  1 i915
psmouse                63677  0 
drm                   164436  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
intel_agp              24671  2 i915
nvram                   6203  0 
memstick                9132  1 jmb38x_ms
flash_bd                8911  1 xd_card
agpgart                31788  2 drm,intel_agp
sdhci_pci               5502  0 
sdhci                  15654  1 sdhci_pci
tpm_tis                 7584  0 
serio_raw               3978  0 
tpm                    14000  1 tpm_tis
led_class               2864  1 sdhci
tpm_bios                5266  1 tpm
snd                    54244  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
r8192se_pci           448286  0 
video                  17375  1 i915
output                  1871  1 video
soundcore               6620  1 snd
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
ahci                   32712  2 
r8169                  34396  0 
mii                     4381  1 r8169


```
dmesg | grep -i wlan
```[   42.670241] Linux kernel driver for RTL8192 based WLAN cards
[   42.670243] Copyright (c) 2007-2008, Realsil Wlan Driver
[   44.159850] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   74.361844] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready



```
ifconfig -a
```eth0      Link encap:Ethernet  HWaddr c8:0a:a9:ee:ef:67  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:30 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:367637 errors:0 dropped:0 overruns:0 frame:0
          TX packets:367637 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:50405104 (50.4 MB)  TX bytes:50405104 (50.4 MB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

virbr0    Link encap:Ethernet  HWaddr 5e:dd:e9:6a:f2:a6  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::5cdd:e9ff:fe6a:f2a6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:13291 (13.2 KB)

wlan0     Link encap:Ethernet  HWaddr f0:7b:cb:a5:28:bd  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2001:c90:86c4:71b1:f27b:cbff:fea5:28bd/64 Scope:Global
          inet6 addr: fe80::f27b:cbff:fea5:28bd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1485 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1157 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1297086 (1.2 MB)  TX bytes:234293 (234.2 KB)
          Interrupt:17 Memory:f8490000-f8490100 


```
iwconfig
```lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  ESSID:"000A79D38F93"  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.422 GHz  Access Point: 00:0A:79:D3:8F:92   
          Bit Rate=300 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management period:0us  mode:All packets received
          Link Quality=64/100  Signal level=-71 dBm  Noise level=-102 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

virbr0    no wireless extensions.

vboxnet0  no wireless extensions.


```
rfkill list all
```No output available. 

Thank you for your guidance Raja. I tried some of these but couldn't make heads or tails of it. For me this is a learning experience.

---

### Post by Renshu on 2012-09-09
Rather quiet out there. :confused: I am wondering if maybe a fresh install should be my choice. I updated my kernel to a newer version but still the same problem. The wireless just dropps out after a certian amount of time. Would appreciate any guidance if possible. 

Thank you, 

Renshu

---

