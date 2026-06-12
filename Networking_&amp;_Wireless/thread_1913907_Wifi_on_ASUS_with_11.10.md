---
title: "Wifi on ASUS with 11.10"
date: 2012-01-23
forum: Networking &amp; Wireless
---

### Post by bluemoon222 on 2012-01-23
I am a relative newbie to UBUNTU and am having some issues getting Wifi stable to an ASUS X58C (previous windows vista machine)

I have installed 11.10 over the top of the old Vista image and managed to get occasional wifi connectivity using a variety of ideas and updates I found on these pages but the long and short of it is I am resorting to a fresh install and would appreciate some best practices before I go far from the standard install image next time ?

---

### Post by bluemoon222 on 2012-01-23
Probably should say that I have set the Wifi to 802.11b/g with WPA2 / the router is a Thomson Alcatel Speedtouch and the network is stable to 3 Mac's, 2 Android and 2 iOS devices elsewhere in the house

---

### Post by bluemoon222 on 2012-01-23
Probably should have also said  I have a wired connection over which I am installing all available updates

---

### Post by praseodym on 2012-01-23
Hi,

please show the outputs of
```

lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```
Any recommended driver in "aditional drivers"

---

### Post by bluemoon222 on 2012-01-24
In the end I did a reinstall and that one seems to have stabilised but FWIW output below....where do I find "additional drivers" BTW ?


steve@olga-X58C:~$ lspci -nnk | grep -iA2 net
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter [1039:0191] (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1815]
	Kernel driver in use: sis190
--
02:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
	Subsystem: AzureWave Device [1a3b:1067]
	Kernel driver in use: ath9k
steve@olga-X58C:~$ lsmod
Module                  Size  Used by
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
joydev                 17393  0 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
arc4                   12473  2 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ath9k                 112711  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              393459  1 ath9k
ath9k_common           13599  1 ath9k
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath9k_hw              293933  2 ath9k,ath9k_common
pcmcia                 39822  0 
psmouse                73673  0 
serio_raw              12990  0 
ath                    19387  2 ath9k,ath9k_hw
r592                   17808  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
yenta_socket           27428  0 
memstick               15857  1 r592
pcmcia_rsrc            18367  1 yenta_socket
cfg80211              172427  3 ath9k,mac80211,ath
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
video                  18908  0 
binfmt_misc            17292  1 
asus_laptop            19050  0 
sis_agp                13165  1 
shpchp                 32356  0 
sparse_keymap          13658  1 asus_laptop
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
hid_apple              13166  0 
usbhid                 41905  0 
hid                    77367  2 hid_apple,usbhid
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
sata_sis               12703  2 
sis190                 22575  0 
steve@olga-X58C:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"filet"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:24:D2:24:A0:9C   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:57   Missed beacon:0

steve@olga-X58C:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
steve@olga-X58C:~$

---

### Post by bluemoon222 on 2012-01-24
OK apologies....I found Additional Drivers in System Settings

It says "no proprietory drivers are in use on this system"

---

### Post by praseodym on 2012-01-24
Ok,

for this Atheros driver you need to deactivate the hardware encryption:

[http://ubuntuforums.org/showpost.php?p=11637235&postcount=5](http://ubuntuforums.org/showpost.php?p=11637235&postcount=5)

---

