---
title: "WiFi connected but not shown in NM"
date: 2011-12-19
forum: Networking &amp; Wireless
---

### Post by Klaster on 2011-12-19
Hey there,

I'm having a weird problem with my DELL Vostro 1320 since I updated to 11.10 (no clean install). I used to use WICD but wanted to switch to the Network Manager being shipped with Oneiric. 

After deinstalling WICD, I am still connected to my wireless network but the Network Manager doesn't show anything but "WiFi switched off by hardware" (or similar, I use a German version).

Some facts:
```
Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY
``````
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:3  Signal level:188  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
``````

~$ ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:24:e8:a2:aa:7f  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:47 Basisadresse:0xe000 

eth1      Link encap:Ethernet  Hardware Adresse 00:22:5f:a3:36:5d  
          inet Adresse:192.168.1.10  Bcast:192.168.1.255  Maske:255.255.255.0
          inet6-Adresse: fe80::222:5fff:fea3:365d/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:48166 errors:0 dropped:0 overruns:0 frame:298304
          TX packets:33332 errors:37 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:60461732 (60.4 MB)  TX bytes:4339888 (4.3 MB)
          Interrupt:18 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

``````
NetworkManager.conf:
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true
```Anything else you might need?

Thanks for any help!


EDIT:
Some more information:

```
~$ rfkill list all
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
3: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

```
~$ lsmod
Module                  Size  Used by
parport_pc             36962  0 
ppdev                  17113  0 
dm_crypt               23199  0 
bnep                   18436  2 
rfcomm                 47946  8 
joydev                 17693  0 
binfmt_misc            17540  1 
nvidia              11713772  33 
snd_hda_codec_idt      70553  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
dell_laptop            13831  0 
dcdbas                 14490  1 dell_laptop
btusb                  18600  2 
bluetooth             166112  23 bnep,rfcomm,btusb
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73882  0 
serio_raw              13166  0 
snd                    68266  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lib80211_crypt_tkip    17390  0 
wl                   2568210  0 
lib80211               14991  2 lib80211_crypt_tkip,wl
ath5k                 156371  0 
ath                    24067  1 ath5k
mac80211              310872  1 ath5k
cfg80211              199587  3 ath5k,ath,mac80211
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
ahci                   26002  3 
libahci                26861  1 ahci
firewire_ohci          40722  0 
r8169                  52788  0 
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
video                  19412  0 
```

---

### Post by Klaster on 2011-12-20
Maybe the solution lies right here?


```

~$ rfkill list all 
0: brcmwl-0: Wireless LAN     
Soft blocked: no     
Hard blocked: no 

1: hci0: Bluetooth     
Soft blocked: no     
Hard blocked: no 

2: dell-wifi: Wireless LAN     
Soft blocked: yes     
Hard blocked: yes 

3: dell-bluetooth: Bluetooth     
Soft blocked: no 
Hard blocked: no

```

What does the "dell-wifi"-section mean and why is it blocked?

---

### Post by Klaster on 2011-12-21
Solved it myself.

The dell-laptop - thing was indeed the problem. Problem solved by rmmod it and then blacklist it.

---

