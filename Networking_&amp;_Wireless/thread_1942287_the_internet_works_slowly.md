---
title: "the internet works slowly"
date: 2012-03-17
forum: Networking &amp; Wireless
---

### Post by Grab&amp;Drop on 2012-03-17
hi
English is not my main language so im sorry if I have mistakes.
 
k so my problem is this: we switched to another internet supply a few weeks ago.
we have two computer in the house- one is my netbook that running xubuntu and the second was with ubuntu, now it is with linux mint.

in the second computer this internet worked well and even very good, in the ubuntu and in the linux mint.

in my netbook, it works, sorry for the work, poop.
yea, its just loading pages slowly. I tried to install some software that makes the network download 100MB/s, and it helped a little.

sometimes the internet works fair, and sometimes, like I said, poop.

I thought the problem was at the OS, but when I ran linux mint from DOK on the netbook, the same problem appeared.

wot can I do? and sorry about my bad and american english.
thx.

---

### Post by praseodym on 2012-03-17
Hi,

add the nameservers of your provider (or those of google public 8.8.8.8 and 8.8.4.4) in the network-manager applet (IPv4-settings->change to Automatic DHCP, addresses only) and add them in "DNS-servers".

---

### Post by Grab&amp;Drop on 2012-03-17
nothin :(

---

### Post by praseodym on 2012-03-17
Which software did you install adiitionally? Please show the outputs of

> lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
route -n

---

### Post by Grab&amp;Drop on 2012-03-18
lspci -nnk | grep -iA2 net:

```
01:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
	Subsystem: Acer Incorporated [ALI] Device [1025:0349]
	Kernel driver in use: atl1c
--
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e016]
	Kernel driver in use: ath9k

```


lsusb:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0402:9665 ALi Corp. 
Bus 002 Device 002: ID 04fc:05da Sunplus Technology Co., Ltd 

```


lsmod:
```
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  4 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  0 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
arc4                   12473  2 
binfmt_misc            17292  1 
ath9k                 112711  0 
joydev                 17393  0 
mac80211              393459  1 ath9k
ath9k_common           13599  1 ath9k
ath9k_hw              293933  2 ath9k,ath9k_common
acer_wmi               23302  0 
ath                    19387  2 ath9k,ath9k_hw
psmouse                73673  0 
snd_hda_codec_realtek   254125  1 
serio_raw              12990  0 
sparse_keymap          13658  1 acer_wmi
cfg80211              172427  3 ath9k,mac80211,ath
snd_hda_intel          24262  3 
snd_hda_codec          91859  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
i915                  509487  4 
ahci                   21634  2 
drm_kms_helper         32889  1 i915
drm                   192194  5 i915,drm_kms_helper
libahci                25727  1 ahci
atl1c                  36638  0 
i2c_algo_bit           13199  1 i915
wmi                    18744  1 acer_wmi
video                  18908  1 i915

```


ifconfig -a:
```
eth0      Link encap:Ethernet  HWaddr 88:ae:1d:7f:c1:d0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2357 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2357 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:91666 (91.6 KB)  TX bytes:91666 (91.6 KB)

wlan0     Link encap:Ethernet  HWaddr 5c:ac:4c:12:49:f9  
          inet addr:10.100.102.4  Bcast:10.100.102.255  Mask:255.255.255.0
          inet6 addr: fe80::5eac:4cff:fe12:49f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5791 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6995 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3277044 (3.2 MB)  TX bytes:984934 (984.9 KB)
```


iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"netvision"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:2A:31:1E:64   
          Bit Rate=58.5 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=36/70  Signal level=-74 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:781  Invalid misc:30   Missed beacon:0

```


route -n:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.100.102.1    0.0.0.0         UG    0      0        0 wlan0
10.100.102.0    0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0

```

---

### Post by praseodym on 2012-03-18
Deactivate the hardware encryption of the driver and the power management of the card:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
sudo iwconfig wlan0 power off
```
I recommend using WPA2-AES encryption if possible.

---

### Post by Grab&amp;Drop on 2012-03-18
> **praseodym said:**
> Deactivate the hardware encryption of the driver and the power management of the card:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
sudo iwconfig wlan0 power off
```
I recommend using WPA2-AES encryption if possible.

thx is worked :)

---

