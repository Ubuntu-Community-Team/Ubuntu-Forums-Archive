---
title: "Network Manager shows connection, but internet keeps dropping every ~5 minutes"
date: 2011-12-22
forum: Networking &amp; Wireless
---

### Post by Basher101 on 2011-12-22
so i have this small issue which is driving me nuts. The Network Manager shows my connection via eth0. But sometimes when im just surfing the web the internet connection drops..nm-applet keeps showing that the connection is fine but i still do not get any internet connection wit the browser. 

I am using Chrmoium Webbrowser and skype, nothing else. 

Here is the output of ifconfig
```
@Armageddon:~$ ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 8c:89:a5:65:67:5f  
          inet Adresse:192.168.178.27  Bcast:192.168.178.255  Maske:255.255.255.0
          inet6-Adresse: fe80::8e89:a5ff:fe65:675f/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:6656 errors:0 dropped:6656 overruns:0 frame:6656
          TX packets:7081 errors:0 dropped:96 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:6124153 (6.1 MB)  TX bytes:871146 (871.1 KB)
          Interrupt:46 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:1331 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1331 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:53678 (53.6 KB)  TX bytes:53678 (53.6 KB)
```

---

### Post by praseodym on 2011-12-22
Hi,

what hardware is in use?
```
uname -a
lspci -nnk | grep -iA2 net
lsmod
route -n
cat /etc/network/interfaces
cat /etc/resolv.conf
```

---

### Post by Basher101 on 2011-12-22
```
Linux Armageddon 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
stiv@Armageddon:~$ lspci -nnk | grep -iA2 net
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7681]
	Kernel driver in use: r8169
stiv@Armageddon:~$ lsmod
Module                  Size  Used by
parport_pc             36962  1 
ppdev                  17113  0 
dm_crypt               23199  0 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  5 
snd_hda_codec_realtek   330769  1 
joydev                 17693  0 
snd_usb_audio         118064  3 
snd_usbmidi_lib        25371  1 snd_usb_audio
nvidia              11713772  50 
mxm_wmi                12979  0 
snd_hda_intel          33390  3 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_pcm                96714  5 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  2 snd_usbmidi_lib,snd_seq_midi
wmi                    19256  1 mxm_wmi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73882  0 
shpchp                 37345  0 
sbs                    18586  0 
sbshc                  13784  1 sbs
max6650                14329  0 
snd                    68266  23 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
f71882fg               36045  0 
coretemp               13420  0 
serio_raw              13166  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41480  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
dm_raid45              78155  0 
xor                    12894  1 dm_raid45
dm_mirror              22203  0 
dm_region_hash         20918  1 dm_mirror
dm_log                 18564  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 648854  0 
zlib_deflate           27139  1 btrfs
libcrc32c              12644  1 btrfs
uvesafb                29305  1 
usbhid                 47198  0 
hid                    95463  1 usbhid
xhci_hcd               82820  0 
i915                  566827  0 
ahci                   26002  1 
libahci                26861  1 ahci
r8169                  52788  0 
drm_kms_helper         42558  1 i915
drm                   236290  2 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
zram                   18463  1 
stiv@Armageddon:~$ route -n
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.178.1   0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.178.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0
stiv@Armageddon:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

I use a custom by me built Desktop PC (see specs below). The MSI motherboard has an onboard Realtek Ethernet port

p.s. the Internet itself is 100% stable. I have NEVER expirienced a disconnect in Windows 7. EVER.

---

### Post by Basher101 on 2011-12-22
sry for double post...my internet screwd again T.T

---

### Post by praseodym on 2011-12-22
Install the "real" driver for this device:

```
sudo apt-get install --reinstall linux-headers-generic build-essential dkms
wget [http://r8168.googlecode.com/files/r8168-8.027.00.tar.bz2](http://r8168.googlecode.com/files/r8168-8.027.00.tar.bz2)
tar xvf r8168-8.027.00.tar.bz2
cd r8168-8.027.00/
sudo sh ./autorun.sh
```

In German [here]("http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217") ;-)

---

### Post by Basher101 on 2011-12-22
ooooooooooh i guess i deleted a "generic" too much with synaptic (i was cleaning up after a kernel update) *facepalms*


thanks alot mate..very appreciated. (dankeschöön, zu spät gesehn das du aus Berlin bis hahaha wie verplant man sein kann^^)

---

### Post by praseodym on 2011-12-22
Cleaning up the system _never_ with the janitor (also wants to remove apps which are not quite often used) but with

```
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
```

---

