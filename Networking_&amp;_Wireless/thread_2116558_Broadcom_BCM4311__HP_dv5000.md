---
title: "Broadcom BCM4311 / HP dv5000"
date: 2013-02-16
forum: Networking &amp; Wireless
---

### Post by banditpanda on 2013-02-16
Hello guys!

I am newbie in linux and need your support.
A have installed lubuntu to my old laptop (HP dv5000) and have problems with wifi. My laptop just could not detect any wireless network.
I almost try every solution in this forum for this problem and anyway i cant get this card working properly.

```

root@PandaHP:/home/panda# rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

```

root@PandaHP:/home/panda# ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:16:d4:32:82:39  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:416 errors:0 dropped:0 overruns:0 frame:0
          TX packets:416 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:33136 (33.1 KB)  TX bytes:33136 (33.1 KB)

```

I think wifi card cant detect any wireless network because wlan0 is "down" I dont know how could i get it to "up" state. :confused:

```

root@PandaHP:/home/panda# ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

```

I have tried to modify /etc/network/interfaces and add two more lines and comment two existing one
```

#auto lo
#iface lo inet loopback
auto wlan0
iface wlan0 inet dhcp

```
and this make my LAN adapter "down" after reboot. Nothing changes with wifi card.

Please help me.

Thank you.

---

### Post by praseodym on 2013-02-16
Hi,

please revert anything in the "interfaces" file and reboot. CHeck after that:
```

iwconfig
sudo iwlist scan
lspci -nnk | grep -iA2 net
lsmod
dmesg | grep iwl
```

---

### Post by banditpanda on 2013-02-16
Revert everything back in /etc/network/interfaces


```

panda@PandaHP:~$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.

```

```

panda@PandaHP:~$ sudo iwlist scan
[sudo] password for panda: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

```

panda@PandaHP:~$ lspci -nnk | grep -iA2 net
06:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1364]
	Kernel driver in use: b43-pci-bridge
--
08:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:30a5]
	Kernel driver in use: e100

```

```

panda@PandaHP:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39210  1 
uas                    17556  0 
usb_storage            39350  2 
snd_hda_codec_conexant    52202  1 
joydev                 17161  0 
coretemp               13168  0 
hp_wmi                 13616  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_intel          32515  1 
snd_hda_codec         111547  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
microcode              18209  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
rfcomm                 37276  0 
parport_pc             31968  0 
bnep                   17707  2 
ppdev                  12817  0 
bluetooth             183228  10 rfcomm,bnep
snd_timer              24411  2 snd_pcm,snd_seq
psmouse                84843  0 
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  457161  2 
serio_raw              13031  0 
lpc_ich                16925  0 
drm_kms_helper         45271  1 i915
b43                   347284  0 
snd                    61991  11 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   230463  3 i915,drm_kms_helper
bcma                   34483  1 b43
soundcore              14599  1 snd
i2c_algo_bit           13197  1 i915
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
ssb_hcd                12749  0 
wmi                    18590  1 hp_wmi
iwl3945                63695  0 
video                  18847  1 i915
mac_hid                13037  0 
iwlegacy               87736  1 iwl3945
mac80211              461161  3 b43,iwl3945,iwlegacy
cfg80211              175375  4 b43,iwl3945,iwlegacy,mac80211
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
hid_a4tech             12590  0 
usbhid                 41702  0 
hid                    82142  2 hid_a4tech,usbhid
e100                   35903  0 
ssb                    50087  2 b43,ssb_hcd

```

```

panda@PandaHP:~$ dmesg | grep iwl
[   14.644382] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   14.644388] iwl3945: Copyright(c) 2003-2011 Intel Corporation

```

nothing changes...

---

### Post by praseodym on 2013-02-17
Obviously you have a Broadcom device, Intel is the LAN controller. You only need to install the package "linux-firmware-nonfree" via Software-Center.

---

### Post by banditpanda on 2013-02-17
Yes, after installing this package wifi start working properly.
Thank you.

---

