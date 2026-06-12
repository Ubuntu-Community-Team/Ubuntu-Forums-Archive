---
title: "can't connetct to the internet(wireless)"
date: 2011-09-20
forum: Networking &amp; Wireless
---

### Post by roma_g on 2011-09-20
:pHi all!
i"m using dell inspiron 1525 machine .and also i've got a dual boot (ubuntu 10.4 & win7).
untill now everything worked fine but recently i can't connect to the internet (wireles).
I have no problem with that in windows and also i can connect (in ubuntu) through cable.
Thanks .

---

### Post by lmarmisa on 2011-09-20
> **roma_g said:**
> :pHi all!
i"m using dell inspiron 1525 machine .and also i've got a dual boot (ubuntu 10.4 & win7).
untill now everything worked fine but recently i can't connect to the internet (wireles).
I have no problem with that in windows and also i can connect (in ubuntu) through cable.
Thanks .

Welcome to the forums. :D

Please, open a terminal, type these commands and post the results:

```

iwconfig
ifconfig
nm-tool
ping -c3 8.8.4.4
ping -c3 google.com

```

---

### Post by user sam on 2011-09-20
Hey, don't you mean "ifconfig" instead of "ipconfig"?

---

### Post by lmarmisa on 2011-09-20
> **user sam said:**
> Hey, don't you mean "ifconfig" instead of "ipconfig"?

Yes, you are right, sam.

---

### Post by roma_g on 2011-09-20
[EMAIL="roma@roma-laptop:~$"]roma@roma-laptop:~$[/EMAIL] iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
[EMAIL="roma@roma-laptop:~$"]roma@roma-laptop:~$[/EMAIL] 

[EMAIL="roma@roma-laptop:~$"]roma@roma-laptop:~$[/EMAIL] ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:36:c8:6d  
          inet6 addr: fe80::21d:9ff:fe36:c86d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:789 errors:0 dropped:0 overruns:0 frame:0
          TX packets:529 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:950588 (950.5 KB)  TX bytes:37928 (37.9 KB)
          Interrupt:16 
eth1      Link encap:Ethernet  HWaddr 00:1f:3a:18:cc:91  
          inet6 addr: fe80::21f:3aff:fe18:cc91/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:231
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3438 (3.4 KB)  TX bytes:30450 (30.4 KB)
          Interrupt:17 Base address:0xc000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:360 errors:0 dropped:0 overruns:0 frame:0
          TX packets:360 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28176 (28.1 KB)  TX bytes:28176 (28.1 KB)
[EMAIL="roma@roma-laptop:~$"]roma@roma-laptop:~$[/EMAIL] ping -c3 8.8.4.4
connect: Network is unreachable
[EMAIL="roma@roma-laptop:~$"]roma@roma-laptop:~$[/EMAIL]

---

### Post by roma_g on 2011-09-20
also i can see an available networks but i can ot connect anyway

---

### Post by praseodym on 2011-09-20
Hi,

please show additionally:

```
lspci -nnk | grep -iA2 net
lsmod
rfkill list
```

---

### Post by roma_g on 2011-09-20
roma@roma-laptop:~$ lspci -nnk | grep -iA2 net
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
	Kernel driver in use: sky2
	Kernel modules: sky2
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Kernel driver in use: wl
	Kernel modules: wl, ssb
roma@roma-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_idt      51978  1 
snd_hda_codec_intelhdmi    11622  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
ipt_REJECT              1928  1 
ipt_LOG                 4542  9 
xt_limit                1382  10 
xt_tcpudp               2011  7 
ipt_addrtype            1631  4 
xt_state                1098  9 
joydev                  8740  0 
snd_hda_intel          22005  2 
snd_hda_codec          74201  3 snd_hda_codec_idt,snd_hda_codec_intelhdmi,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
ip6table_filter         2343  1 
ip6_tables             11227  1 ip6table_filter
snd_seq_dummy           1338  0 
dell_wmi                1793  0 
nf_nat_irc              1124  0 
snd_seq_oss            26722  0 
nf_conntrack_irc        3332  1 nf_nat_irc
snd_seq_midi            4557  0 
nf_nat_ftp              1836  0 
snd_rawmidi            19056  1 snd_seq_midi
nf_nat                 15735  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      10672  11 nf_nat
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
nf_conntrack_ftp        5381  1 nf_nat_ftp
nf_conntrack           61615  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iptable_filter          2271  1 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lib80211_crypt_tkip     7596  0 
ip_tables               9991  1 iptable_filter
x_tables               14299  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
uvcvideo               57054  0 
i915                  287458  3 
drm_kms_helper         29329  1 i915
videodev               34361  1 uvcvideo
usbhid                 36110  0 
hid                    67032  1 usbhid
ricoh_mmc               2923  0 
snd                    54180  17 snd_hda_codec_idt,snd_hda_codec_intelhdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_laptop             6856  0 
dcdbas                  5422  1 dell_laptop
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
led_class               2864  1 sdhci
wl                   1959598  0 
v4l1_compat            13251  2 uvcvideo,videodev
psmouse                63245  0 
serio_raw               3978  0 
drm                   162409  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
lib80211                5046  2 lib80211_crypt_tkip,wl
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
intel_agp              24375  2 i915
agpgart                31724  2 drm,intel_agp
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
ahci                   32200  4 
sky2                   40807  0 
roma@roma-laptop:~$ rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
roma@roma-laptop:~$

---

### Post by wildmanne39 on 2011-09-20
Hi, I recommend opening synaptic and type in broadcom then remove your drivers and restart your computer then run this command.
```
sudo apt-get install b43-fwcutter
```
When it is done unplug your wired connection and restart your computer.

The reason I say that is I think you have drivers that are conflicting and the method I describe should fix it I just tested it on 10.04 in virtualbox.
Thank you

---

### Post by praseodym on 2011-09-20
Hi,

do you really need the firewall? Which encryption mode do you use? I recommend WPA2-AES instead of mixed WPA/WPA2 or WEP, otherwise the network-manager makes problems. For this device both b43 and the STA-driver can be used, as wildmanne39 posted the firmware-installation of the b43. Your router firmware is up-to-date? Router allows new clients (MAC-filter off)?

---

### Post by roma_g on 2011-09-21
looks like it works,i just reinstalled the b43 and added STA drivers
thank's for your help!!!

---

### Post by wildmanne39 on 2011-09-21
Hi, your welcome! glad we could help. Would you consider clicking on the red link in my signature and showing your support for me becoming an ubuntu member if you found me helpful.
Thank you

---

