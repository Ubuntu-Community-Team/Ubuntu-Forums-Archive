---
title: "USB Wireless connection not working"
date: 2012-03-09
forum: Networking &amp; Wireless
---

### Post by djaniel on 2012-03-09
Hello,

I'm having a problem with my USB wireless adaptor on my ubuntu linux 11.10. Here's the scenario:

Shell:
nm-tool -> 
device wlan0 [ESSID] 
State: connected

Windows and MacOS connects to wlan, but Ubuntu doesn't (only ubuntu and windows run in the same pc). From the output of nm-tool, I assume that my driver is working fine. IP

I've checked the three IP address and the differ only in the last number, x.x.x.(Win, Mac, Lin). They all use the same DNS domain and IP address. But only linux doesn't have access to internet. The upper right menu shows the connected status but firefox doesn't work.

ping google.com -> fail
ping router -> fail
dhclient wlan0 ->hangs

Could you give me a suggestion on how to get this right?
Thanks
Daniel SG

---

### Post by praseodym on 2012-03-09
Pleae show the outputs of

```
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by djaniel on 2012-03-09
Hi, here it is
```

danielsg@Dientes:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0cf3:1002 Atheros Communications, Inc. TP-Link TL-WN821N v2 [Atheros AR9001U-(2)NG]
Bus 002 Device 002: ID 058f:6364 Alcor Micro Corp. 
Bus 002 Device 003: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 008 Device 002: ID 045e:0750 Microsoft Corp. Wired Keyboard 600
Bus 008 Device 003: ID 045e:076c Microsoft Corp. 


danielsg@Dientes:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
vesafb                 13809  1 
arc4                   12529  2 
nvidia              11713772  40 
carl9170               83160  0 
binfmt_misc            17540  1 
mac80211              462046  1 carl9170
ath                    24067  1 carl9170
cfg80211              199630  3 carl9170,mac80211,ath
mxm_wmi                12979  0 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  2 
snd_hda_codec         104931  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  2 snd_hda_intel,snd_hda_codec
wmi                    19256  1 mxm_wmi
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
joydev                 17693  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
i7core_edac            27942  0 
psmouse                73882  0 
edac_core              53746  3 i7core_edac
ppdev                  17113  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             36962  1 
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
serio_raw              13166  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
usbhid                 47198  0 
usb_storage            57901  1 
uas                    18027  0 
hid                    95463  1 usbhid
crc_itu_t              12707  1 firewire_core
pata_marvell           12912  0 
ahci                   26002  0 
libahci                26861  1 ahci
e1000e                160582  0 
danielsg@Dientes:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Laboratorios"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:04:96:3B:12:38   
          Bit Rate=117 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

danielsg@Dientes:~$ rfkill list
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
danielsg@Dientes:~$

```
thanks

---

### Post by praseodym on 2012-03-09
Driver should be Ok, connection, too. Set the encryption to pure WPA2-AES if possible.

Checked the router settings? MAC-address-filter off? Router-firmware up-to-date?

---

### Post by djaniel on 2012-03-09
There are some difficulties about checking router settings since I don't know where it is and I'm not the administrator :) I'm at school. I can tell you, for Windows (same hardware) and MacOS it works fine. I have noticed that Ubuntu tries to connect to router several times before connection is achieved and sometimes it fails completely.

---

### Post by praseodym on 2012-03-10
Please show
```

sudo iwlist scan
iwlist chan
dmesg | egrep 'carl|country'
```
Any strange letters or blanks in the network name (ESSID)or the key? How many letters does the key have?

---

### Post by djaniel on 2012-03-10
Hey, thanks for the interest, but I couldn't afford to waste more time trying to fix it, so I backed up and downgrade... :( Thanks again.

---

