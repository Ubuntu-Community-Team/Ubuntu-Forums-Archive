---
title: "wireless drops using torrent client"
date: 2011-12-22
forum: Networking &amp; Wireless
---

### Post by Papas228 on 2011-12-22
hey guys, so my wireless keeps dropping out every so often and reconnecting when i'm downloading torrents don't know why. i'm using a trendnet tew424ub adpater thanks for the help in advanced

---

### Post by praseodym on 2011-12-22
Hi,

please show

```
lsusb
lsmod
ifconfig -a
iwconfig
sudo iwlist scan
```

---

### Post by Papas228 on 2011-12-22
papo@Destroyer:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 016: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 004 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 003 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
papo@Destroyer:~$ lsmod
Module                  Size  Used by
snd_seq_dummy          12798  0 
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
parport_pc             36962  0 
ppdev                  17113  0 
vesafb                 13809  1 
snd_hda_codec_realtek   330769  1 
binfmt_misc            17540  1 
arc4                   12529  2 
joydev                 17693  0 
rtl8187                57035  0 
mac80211              462092  1 rtl8187
snd_hda_intel          33390  1 
cfg80211              199587  2 rtl8187,mac80211
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
eeprom_93cx6           12725  1 rtl8187
snd_hwdep              13668  1 snd_hda_codec
mxm_wmi                12979  0 
snd_pcm                96714  2 snd_hda_intel,snd_hda_codec
nvidia              11713772  112 
snd_seq_midi           13324  0 
usbhid                 47198  0 
hid                    95463  1 usbhid
snd_rawmidi            30547  1 snd_seq_midi
k10temp                13166  0 
edac_core              53746  0 
edac_mce_amd           23709  0 
snd_seq_midi_event     14899  1 snd_seq_midi
psmouse                73882  0 
serio_raw              13166  0 
video                  19412  0 
snd_seq                61896  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
wmi                    19256  1 mxm_wmi
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  11 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
shpchp                 37345  0 
i2c_nforce2            13058  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
floppy                 70365  0 
crc_itu_t              12707  1 firewire_core
tg3                   147729  0 
pata_jmicron           12747  0 
pata_amd               14121  0 
ahci                   26002  2 
libahci                26861  1 ahci
papo@Destroyer:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:22:68:5c:de:4b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:22:68:5c:de:4c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4307 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4307 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1306992 (1.3 MB)  TX bytes:1306992 (1.3 MB)

wlan0     Link encap:Ethernet  HWaddr 00:14:d1:32:9f:ee  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:d1ff:fe32:9fee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:231768 errors:0 dropped:0 overruns:0 frame:0
          TX packets:262578 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:172282810 (172.2 MB)  TX bytes:253585223 (253.5 MB)

papo@Destroyer:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Papo"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 30:46:9A:63:8C:D7   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-12 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:18549  Invalid misc:11355   Missed beacon:0

papo@Destroyer:~$ sudo iwlist scan
[sudo] password for papo: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

there you go my friend

---

### Post by praseodym on 2011-12-23
Change the encryption mode to WPA2-AES if possible and set "IPv6 settings" to **ignore**

---

