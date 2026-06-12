---
title: "Very slow wireless new umbuntu user"
date: 2012-04-16
forum: Networking &amp; Wireless
---

### Post by remfan85 on 2012-04-16
Hi very new to Umbuntu 11.10, i seem to have a very slow conection to any wireless network. saw some posts before about this but i didn't know if the changes the other users made to their systems would work, 
 
Thx in advance
 
way better than windows though!

---

### Post by williamcharles on 2012-04-16
what is your ethernet controller?
give output of 
> lspci | grep Ethernet

---

### Post by gordintoronto on 2012-04-16
More importantly, what is your wireless controller. It might be helpful if you describe your computer.

---

### Post by wildmanne39 on 2012-04-16
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by remfan85 on 2012-04-20
```
darragh@darragh-NF108-NF208:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux darragh-NF108-NF208 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686 i686 i386 GNU/Linux
darragh@darragh-NF108-NF208:~$ lspci -nnk | grep -iA2 net
05:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Askey Computer Corp. Device [144f:7179]
	Kernel driver in use: brcmsmac
--
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354]
	Subsystem: Samsung Electronics Co Ltd Device [144d:c08c]
	Kernel driver in use: sky2
darragh@darragh-NF108-NF208:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 2232:1005  
Bus 003 Device 002: ID 0a5c:219c Broadcom Corp. 
darragh@darragh-NF108-NF208:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"dacwireless"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:23:F8:D5:DA:98   
          Bit Rate=54 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:216   Missed beacon:0

darragh@darragh-NF108-NF208:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
darragh@darragh-NF108-NF208:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38408  8 
wl                   2646601  0 
lib80211               14570  1 wl
bcma                   19571  0 
joydev                 17393  0 
arc4                   12473  2 
snd_hda_codec_realtek   254163  1 
uvcvideo               67271  0 
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_realtek,snd_hda_intel
videodev               85626  1 uvcvideo
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
psmouse                73673  0 
btusb                  18160  2 
bluetooth             148839  23 bnep,rfcomm,btusb
serio_raw              12990  0 
brcmsmac              591864  0 
brcmutil               16885  1 brcmsmac
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
binfmt_misc            17292  1 
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              393421  1 brcmsmac
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
i915                  509519  3 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              172427  2 brcmsmac,mac80211
drm_kms_helper         32889  1 i915
crc_ccitt              12595  1 brcmsmac
drm                   192194  4 i915,drm_kms_helper
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  2 
libahci                25727  1 ahci
sky2                   49317  0 

```

---

### Post by wildmanne39 on 2012-04-20
Hi, please do:
```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
reboot let us know if that helps.
Thanks

---

