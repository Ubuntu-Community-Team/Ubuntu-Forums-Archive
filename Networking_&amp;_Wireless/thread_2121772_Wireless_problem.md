---
title: "Wireless problem"
date: 2013-03-03
forum: Networking &amp; Wireless
---

### Post by stephencurto on 2013-03-03
I'm new to ubuntu, and no very little of how it operates.

I downloaded and installed ubuntu 12.10 and everything seemed to work. My wireless connected without a hitch, but when I try to use an internet browser it won't load any pages. According to the computer, my "wireless" is still "connected" I'm just not getting any internet, except for right away for about 10 seconds after disconnecting and reconnecting. How do I get it to be a stable internet connection?

I'm going through a wireless router that is supplying stable internet to other devices, and to this one with windows on the other partition, so it's an ubuntu problem. 

Help! I want to like Ubuntu, but if i can never do an internet search, it's a lost cause....

---

### Post by praseodym on 2013-03-03
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
iwconfig
sudo iwlist scan
rfkill list
lsmod
```

---

### Post by stephencurto on 2013-03-04
stephencurto@Meeeeeeewith7es:~$ uname -a
Linux Meeeeeeewith7es 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686 i686 i686 GNU/Linux


stephencurto@Meeeeeeewith7es:~$ lspci -nnk | grep -iA2 net
03:08.0 Ethernet controller [0200]: Intel Corporation NM10/ICH7 Family LAN Controller [8086:27dc] (rev 01)
    Subsystem: Dell Device [1028:01ab]
    Kernel driver in use: e100


stephencurto@Meeeeeeewith7es:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"2WIRE824"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: B0:E7:54:49:EB:31   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:5  Invalid misc:12   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.



stephencurto@Meeeeeeewith7es:~$ sudo iwlist scan
[sudo] password for stephencurto: 
wlan0     Scan completed :
          Cell 01 - Address: B0:E7:54:49:EB:31
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"2WIRE824"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004cf332d35b
                    Extra: Last beacon: 24ms ago
                    IE: Unknown: 00083257495245383234
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 02 - Address: C0:83:0A:C2:1F:D9
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"2WIRE552"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000207d71e4137
                    Extra: Last beacon: 492ms ago
                    IE: Unknown: 00083257495245353532
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030105
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.



stephencurto@Meeeeeeewith7es:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


stephencurto@Meeeeeeewith7es:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
uas                    17556  0 
usb_storage            39350  1 
arc4                   12473  2 
gpio_ich               13159  0 
dcdbas                 14054  0 
snd_ca0106             39163  2 
snd_ac97_codec        105616  1 snd_ca0106
ac97_bus               12670  1 snd_ac97_codec
snd_usb_audio         104872  2 
snd_pcm                80163  3 snd_ca0106,snd_ac97_codec,snd_usb_audio
microcode              18209  0 
snd_hwdep              13272  1 snd_usb_audio
snd_usbmidi_lib        24225  1 snd_usb_audio
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
rfcomm                 37276  0 
ath9k_htc              85558  0 
parport_pc             31968  0 
bnep                   17707  2 
snd_rawmidi            25382  3 snd_ca0106,snd_usbmidi_lib,snd_seq_midi
bluetooth             183228  10 rfcomm,bnep
ppdev                  12817  0 
snd_timer              24411  2 snd_pcm,snd_seq
mac80211              461161  1 ath9k_htc
ath9k_common           13783  1 ath9k_htc
snd_seq_device         14137  3 snd_seq_midi,snd_seq,snd_rawmidi
joydev                 17161  0 
ath9k_hw              376155  2 ath9k_htc,ath9k_common
ath                    19187  3 ath9k_htc,ath9k_common,ath9k_hw
snd                    61991  18 snd_ca0106,snd_ac97_codec,snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_seq,snd_rawmidi,snd_timer,snd_seq_device
cfg80211              175375  3 ath9k_htc,mac80211,ath
soundcore              14599  1 snd
snd_page_alloc         14036  2 snd_ca0106,snd_pcm
lpc_ich                16925  0 
psmouse                84843  0 
serio_raw              13031  0 
radeon                820703  3 
ttm                    75534  1 radeon
drm_kms_helper         45271  1 radeon
drm                   230463  5 radeon,ttm,drm_kms_helper
mac_hid                13037  0 
i2c_algo_bit           13197  1 radeon
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
hid_generic            12445  0 
hid_microsoft          12686  0 
e100                   35903  0 
usbhid                 41702  0 
hid                    82142  3 hid_generic,hid_microsoft,usbhid

---

### Post by stephencurto on 2013-03-04
sorry for the late reply... and the smileys. I just copied and pasted... and I'm on a different computer for posting, then the one I'm working on the ubuntu with.

---

### Post by praseodym on 2013-03-05
Mark the text in advanced mode and click on the "#" button for code-tags.

Obviously its an USB device. I am using the same driver here. Deactivate the hardware encryption of the driver:
```

echo "options ath9k_htc nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9khtc.conf
sudo modprobe -rfv ath9k_htc
sudo modprobe -v ath9k_htc
```
Additionally there are 2 networks with the same name. I recommend changing the encryption to WPA2-AES only.

---

