---
title: "Wifi sporadic slow loading"
date: 2011-11-20
forum: Networking &amp; Wireless
---

### Post by larascal on 2011-11-20
Hi everyone,

Firstly I am a total noob at this but, I performed a clean install of ubuntu 11.10 which is working wonderfully apart from an annoying wifi issue.

It connects to the network without a problem and will load the first few pages lightning quick, but then for some reason it will either not load or load very very slowly.

Wifi card appears to be an atheros ar2413, and I think I have the correct drivers installed.

Very frustrating as Ubuntu has been a revelation after escaping from Windows hell!

Hope some one can help...

---

### Post by praseodym on 2011-11-20
Hi,

please show the terminal (CTRL+ALT+T) outputs of the commands:

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
```
The driver ath5k is buggy, you need to deactivate the hardware encryption of it via:
```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```

---

### Post by larascal on 2011-11-20
> 02:04.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)
	Subsystem: Askey Computer Corp. Device [144f:7094]
	Kernel driver in use: ath5k
--
02:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Kernel driver in use: 8139too
claire@knuckle-head:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
snd_hda_codec_realtek   254125  1 
snd_hda_codec_si3054    12864  1 
joydev                 17393  0 
snd_hda_intel          24262  5 
snd_hda_codec          91754  3 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_seq_midi           13132  0 
snd_atiixp_modem       18604  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_via82xx_modem      18377  0 
snd_intel8x0m          18498  0 
snd_ac97_codec        106082  3 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m
arc4                   12473  2 
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  9 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec
snd_seq_midi_event     14475  1 snd_seq_midi
pcmcia                 39822  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ath5k                 145100  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ath                    19387  1 ath5k
mac80211              272785  1 ath5k
cfg80211              172392  3 ath5k,ath,mac80211
snd                    55902  22 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_atiixp_modem,snd_rawmidi,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_pcm,snd_seq,snd_timer,snd_seq_device
psmouse                73673  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
serio_raw              12990  0 
snd_page_alloc         14115  5 snd_hda_intel,snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_pcm
binfmt_misc            17292  1 
i2c_piix4              13093  0 
shpchp                 32356  0 
ati_agp                13242  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
usb_storage            44173  0 
8139too                23283  0 
uas                    17699  0 
8139cp                 22636  0 
crc_itu_t              12627  1 firewire_core
pata_atiixp            12967  0 
sata_sil               13278  2 

second command gave me an output of > options ath5k nohwcrypt=1


this has given me very fast wifi but every 20 or seconds the network drops out for around 10 seconds and then reconnects.




thanks for your reply to my first post.

---

### Post by praseodym on 2011-11-20
Which encryption mode do you use? I recommend WPA2-AES, which is the safest. The network-manager has some problems with mixed WPA/WPA2

---

### Post by larascal on 2011-11-20
Its WPA2 Personal. Its one of the those modems that come with a pre existing network name and password. Due to sharing an apartment with other people, I would get shot if I mess with the modem. Can I alter the settings some other way?

Thanks again

---

### Post by praseodym on 2011-11-20
You can deactivate IPv6:
```
echo "net.ipv6.conf.all.disable_ipv6=1" | sudo tee -a /etc/sysctl.conf
```
and reboot. Check:
```
sudo iwlist scan #which is your network here?
ifconfig -a
iwconfig
route -n
cat /etc/resolv.conf
dmesg | grep ath
```

---

### Post by larascal on 2011-11-20
```
wlan0     Scan completed :
          Cell 01 - Address: A0:21:B7:D0:19:82
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"virginmedia6017871"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002d1d231a8f
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 001276697267696E6D6564696136303137383731
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030104
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1604051300000000000000000000000000000000000000
                    IE: Unknown: DD710050F204104A0001101044000102103B000103104700104D73C5C27E6B5243D6440AAB1719670B102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F2040001101100094E6574676561724150100800020088
                    IE: Unknown: DD090010180203F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3404051300000000000000000000000000000000000000

```

this was output from second suggested command. still experiencing the same dropout every 10 seconds followed by automatic reconnect but, wifi is blazing fast when connected!

---

### Post by praseodym on 2011-11-20
> ```
                    IE: IEEE 802.11i/[COLOR="Red"]WPA2[/COLOR] Version 1
                    ...
                    IE: [COLOR="Red"]WPA[/COLOR] Version 1
```
Its mixed WPA/WPA2. Try Wicd with Add-On instead of the NM:

```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service network-manager stop
sudo apt-get remove --purge network-manager network-manager-gnome
sudo service wicd restart
```
Choose **wlan0** as interface name and **wext** as driver.

---

### Post by larascal on 2011-11-20
Still no luck after trying above. Its definitely not a signal problem as other devices are connected fine. Feels like a solution is about to be found though.

Thanks for your help!

---

### Post by praseodym on 2011-11-20
Use the DNS-Servers of your ISP (or those of google public: 8.8.8.8 and 8.8.4.4) instead of automatic or the router IP address

---

