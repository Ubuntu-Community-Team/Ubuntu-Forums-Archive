---
title: "Trouble getting several wifi cards to work"
date: 2011-09-27
forum: Networking &amp; Wireless
---

### Post by Beeblebrx on 2011-09-27
I have new Lucid install on two laptops: #1 Toshiba Tecra 8200, #2 Sony Vaio PCG-SR71. (old P3 cpu's). The Tecra has an internal wifi, while the vaio does not. I also have 2 external cards I would like to get working on these LT's. #a Linksys USB (ralink rt73usb driver) #b USR5410 pcmcia card.

PROBLEM 1:
I cannot get the internal card on the Toshiba to work. # lspci not much help, shows a TI PCI1410 cardbus controller (can't tell if that's it). I found this on archlinux: "go with orinoco_cs (wavemon). There is an "orinoco" entry in udev for this device. Wicd sees the wifi netork but cannot connect to even a simple WEP network (bad passwd error). What am I doing wrong?

PROBLEM 2:
In order to get #a working, I installed rutilt for rt200x drivers - No help.  Same problem as #1 for Toshiba, while the Vaio is not even table to detect the wifi network.  Running rutilt gives: can't get frequency/channel code 22). # dmesg shows no errors but # lspci does not show the device.

PROBLEM 3:
The USR5410 card is not recognised at all. I am thinking of building the acx100 port from source for both LT's. Objections? Maybe there's an easier solution?

Thanks for reading.

---

### Post by Beeblebrx on 2011-09-27
SOME INFO FROM THE TOSHIBA:

# lspci -nmk | grep -iA2 net 
NOTHING

# lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 13b1:0020 Linksys WUSB54GC v1 802.11g Adapter [Ralink RT73]
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr off
          Encryption key off
          Power Management off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan1     IEEE 802.11bg  ESSID off/any
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr off   Fragment thr off
          Encryption key off
          Power Management on

# rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:C1:15:C3:9A
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key on
                    ESSID:"BERKK9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000021cb4030f6
                    Extra: Last beacon: 124ms ago
                    IE: Unknown: 00064245524B4B39
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C

wlan1     No scan results

# lsmod
Module                  Size  Used by
arc4                    1141  2 
rt73usb                23499  0 
crc_itu_t               1319  1 rt73usb
rt2x00usb               9319  1 rt73usb
rt2x00lib              33886  2 rt73usb,rt2x00usb
mac80211              255996  2 rt2x00usb,rt2x00lib
dm_crypt               14720  0 
snd_ymfpci             27590  0 
gameport                7778  1 snd_ymfpci
snd_ac97_codec        101869  1 snd_ymfpci
ac97_bus                 982  1 snd_ac97_codec
snd_pcm_oss            36427  0 
michael_mic             2008  4 
snd_mixer_oss          13581  1 snd_pcm_oss
snd_pcm                68662  3 snd_ymfpci,snd_ac97_codec,snd_pcm_oss
snd_opl3_lib            8008  1 snd_ymfpci
snd_hwdep               5424  1 snd_opl3_lib
snd_page_alloc          6801  2 snd_ymfpci,snd_pcm
orinoco_cs              8000  1 
snd_mpu401_uart         5388  1 snd_ymfpci
orinoco                64902  1 orinoco_cs
snd_seq_dummy           1358  0 
snd_seq_oss            26216  0 
cfg80211              153414  3 rt2x00lib,mac80211,orinoco
snd_seq_midi            4460  0 
snd_rawmidi            18745  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      5720  2 snd_seq_oss,snd_seq_midi
snd_seq                45875  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              17803  4 snd_ymfpci,snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device          5281  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 35273  1 orinoco_cs
ppdev                   5096  0 
snd                    50697  13 snd_ymfpci,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
toshiba_acpi            8252  0 
irda                  176328  0 
yenta_socket           20510  0 
sparse_keymap           3194  1 toshiba_acpi
pcmcia_rsrc             9840  1 yenta_socket
rfkill                 14987  2 cfg80211,toshiba_acpi
parport_pc             26143  1 
pcmcia_core            13330  4 orinoco_cs,pcmcia,yenta_socket,pcmcia_rsrc
soundcore               6048  1 snd
psmouse                52655  0 
crc_ccitt               1281  1 irda
lp                      7373  0 
shpchp                 24986  0 
serio_raw               3744  0 
parport                29468  3 ppdev,parport_pc,lp
mac_hid                 3029  0 
intel_agp               9614  1 
intel_gtt              13296  1 intel_agp
e100                   27925  0 
mii                     4091  1 e100
video                  10930  0 
agpgart                27414  2 intel_agp,intel_gtt

---

