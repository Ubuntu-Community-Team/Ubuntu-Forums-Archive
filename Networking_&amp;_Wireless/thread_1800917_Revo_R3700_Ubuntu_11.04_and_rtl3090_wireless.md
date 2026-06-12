---
title: "Revo R3700 Ubuntu 11.04 and rtl3090 wireless"
date: 2011-07-09
forum: Networking &amp; Wireless
---

### Post by Scorpuk on 2011-07-09
Cant seem to get this to work.

Have done the following:


Downloaded rt3090-dkms_2.4.0.4-0ubuntu0~ppa0_all.deb from here [https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.4.0.4-0ubuntu0%7Eppa0_all.deb]("https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.4.0.4-0ubuntu0%7Eppa0_all.deb") 


Which I installed successfully with:

```
sudo dpkg -i rt3090-dkms_2.4.0.4-0ubuntu0~ppa0_all.deb 
```


Added the following to my blacklist:

> ...
blacklist rt2800pci
blacklist rt2860sta


and then added rt3090sta to /etc/modules



Further info:
```

john@john-Aspire-R3700:~$ modinfo rt3090sta
filename:       /lib/modules/2.6.38-8-generic/updates/dkms/rt3090sta.ko
license:        GPL
version:        2.4.0.4
srcversion:     9A7B078F56A0351E1A34B06
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
depends:        cfg80211
vermagic:       2.6.38-8-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)
john@john-Aspire-R3700:~$ 
```


```
john@john-Aspire-R3700:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a000] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation N10/ICH7 Family SATA IDE Controller [8086:27c0] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GT218 [ION] [10de:0a64] (rev a2)
01:00.1 Audio device [0403]: nVidia Corporation High Definition Audio Controller [10de:0be3] (rev a1)
02:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
john@john-Aspire-R3700:~$
``` 


```
john@john-Aspire-R3700:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.437 GHz  Access Point: 00:50:7F:9A:4A:20   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-29 dBm  Noise level:-29 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

john@john-Aspire-R3700:~$
```


```
john@john-Aspire-R3700:~$ lsmod
Module                  Size  Used by
parport_pc             36959  0 
ppdev                  17113  0 
vesafb                 13761  1 
binfmt_misc            17565  1 
nvidia              10709116  40 
snd_hda_codec_hdmi     28103  4 
snd_hda_codec_realtek   336693  1 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73535  0 
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usbhid                 46956  0 
hid                    91020  1 usbhid
serio_raw              13166  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
rt3090sta             980165  1 
cfg80211              178528  1 rt3090sta
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
r8169                  48022  0 
john@john-Aspire-R3700:~$ 
```


My wireless connection is hidden and I select "wpa & wpa2 Personal" in the connect to hidden wireless network, as its wpa2 personal. Unfortunately I cannot change any of the router setting as its a works one, but I can connect no probs with any other windows computer. :-|


So far this is the only problem I know stopping me upgrading my mythtv server and frontends. :-(


Any help would be appreciated.

---

### Post by Scorpuk on 2011-07-10
Bump. :(

---

### Post by Scorpuk on 2011-07-14
Nobody?

---

