---
title: "no internet acess via wirless"
date: 2012-02-14
forum: Networking &amp; Wireless
---

### Post by tautem on 2012-02-14
i am using ubuntu 11.10 pavilion dm4 1222tx model laptop. it is not able to get connected internet via wireless

---

### Post by raja.genupula on 2012-02-14
hi please post the output of these things here 
```
uname -mr
lspci -nnk | grep -iA2 net
lsmod
dmesg | grep -i wlan
ifconfig -a
iwconfig
rfkill list all
```

Thank you .

---

### Post by perspectoff on 2012-02-14
Some users uninstall Network-Manager and use Wicd instead.

sudo apt-get remove network-manager
sudo apt-get install wicd

---

### Post by GitarSomplak on 2012-02-15
same here, I've just installed ubuntu 11.10 and it cannot connected to internet via wireless

Gateway LT1005n N270
Atheros AR5007EG Wireless Network Adapter

help me :(

---

### Post by raja.genupula on 2012-02-15
> **GitarSomplak said:**
> same here, I've just installed ubuntu 11.10 and it cannot connected to internet via wireless

Gateway LT1005n N270
Atheros AR5007EG Wireless Network Adapter

help me :(
hi its always better to start the a new thread .
ok for issue please look at post #2 and provide the required information.

---

### Post by GitarSomplak on 2012-02-15
ok

```

haryo@ubuntu:~$ uname -mr
3.0.0-12-generic i686

haryo@ubuntu:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Acer Incorporated [ALI] Device [1025:015b]
	Kernel driver in use: r8169
--
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e008]
	Kernel driver in use: ath5k

haryo@ubuntu:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
joydev                 17393  0 
acer_wmi               23302  0 
sparse_keymap          13658  1 acer_wmi
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
arc4                   12473  2 
ath5k                 145100  0 
snd_seq_midi           13132  0 
ath                    19387  1 ath5k
mac80211              272785  1 ath5k
snd_rawmidi            25241  1 snd_seq_midi
psmouse                73673  0 
serio_raw              12990  0 
cfg80211              172392  3 ath5k,ath,mac80211
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  505108  3 
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
wmi                    18744  1 acer_wmi
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  43104  0 


haryo@ubuntu:~$ dmesg | grep -i wlan


haryo@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:23:8b:79:0b:1e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5120 (5.1 KB)  TX bytes:5120 (5.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:8e:2e:b3  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


haryo@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

haryo@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no





```

---

