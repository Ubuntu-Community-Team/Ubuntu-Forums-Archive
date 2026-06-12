---
title: "Very Slow Wireless Internet"
date: 2012-01-23
forum: Networking &amp; Wireless
---

### Post by murphybc on 2012-01-23
I just installed ubuntu on my sony vaio because I need some of the features for a class.  Everything works fine except for my wireless internet which is painfully slow.  I have tried updating but I have not been able to resolve the issue.  I am a complete beginner with ubuntu so any help would be greatly appreciated.

Thanks

---

### Post by Pyraxic on 2012-01-23
Try using Google DNS 8.8.8.8 under /etc/resolv.conf and restart networking service by running /etc/init.d/networking restart and see if that helps!

---

### Post by praseodym on 2012-01-23
Hi,

please show the terminal (CTRL+ALT+T) outputs of the commands:

```
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list
lsmod
```

---

### Post by murphybc on 2012-01-23
I believe this is what you asked for.  Thank you for the help

[PHP]blaine@blaine-VGN-NW350F:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8057 PCI-E Gigabit Ethernet Controller [11ab:4380] (rev 10)
   Subsystem: Sony Corporation Device [104d:906b]
   Kernel driver in use: sky2
--
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
   Subsystem: Foxconn International, Inc. Device [105b:e017]
   Kernel driver in use: ath9kblaine@blaine-VGN-NW350F:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8057 PCI-E Gigabit Ethernet Controller [11ab:4380] (rev 10)
   Subsystem: Sony Corporation Device [104d:906b]
   Kernel driver in use: sky2
--
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
   Subsystem: Foxconn International, Inc. Device [105b:e017]
   Kernel driver in use: ath9k
blaine@blaine-VGN-NW350F:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ca:18b5 Ricoh Co., Ltd
blaine@blaine-VGN-NW350F:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"dd-wrt"
         Mode:Managed  Frequency:2.437 GHz  Access Point: 00:23:69:95:ED:CE
         Bit Rate=58.5 Mb/s   Tx-Power=14 dBm
         Retry  long limit:7   RTS thr:off   Fragment thr:off
         Power Management:on
         Link Quality=70/70  Signal level=-26 dBm
         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
         Tx excessive retries:437  Invalid misc:121   Missed beacon:0

blaine@blaine-VGN-NW350F:~$ rfkill list
0: phy0: Wireless LAN
   Soft blocked: no
   Hard blocked: no
1: sony-wifi: Wireless LAN
   Soft blocked: no
   Hard blocked: no
blaine@blaine-VGN-NW350F:~$ lsmod

blaine@blaine-VGN-NW350F:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ca:18b5 Ricoh Co., Ltd
blaine@blaine-VGN-NW350F:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"dd-wrt"
         Mode:Managed  Frequency:2.437 GHz  Access Point: 00:23:69:95:ED:CE
         Bit Rate=58.5 Mb/s   Tx-Power=14 dBm
         Retry  long limit:7   RTS thr:off   Fragment thr:off
         Power Management:on
         Link Quality=70/70  Signal level=-26 dBm
         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
         Tx excessive retries:437  Invalid misc:121   Missed beacon:0

blaine@blaine-VGN-NW350F:~$ rfkill list
0: phy0: Wireless LAN
   Soft blocked: no
   Hard blocked: no
1: sony-wifi: Wireless LAN
   Soft blocked: no
   Hard blocked: no
blaine@blaine-VGN-NW350F:~$ lsmod[/PHP]

---

### Post by praseodym on 2012-01-24
Deactivate the hardware encryption of the driver:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
If it is not enough you can additionally deactivate the power management:

```
sudo iwconfig wlan0 power off
```

---

### Post by murphybc on 2012-01-24
That did the trick.  Thank you very much, my internet is working much better now.

---

### Post by Redflea on 2012-01-26
> **praseodym said:**
> Deactivate the hardware encryption of the driver:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
If it is not enough you can additionally deactivate the power management:

```
sudo iwconfig wlan0 power off
```

Are those first set of commands permanent, (linux noob here). I believe the echo command line above is writing the hardware encryption setting to the file ath9k.conf, so that  would be persistent after a reboot.  What about the other two lines (the sudo modprobe ones)? 

If they are not persistent, could I add the first set of commands to a file I already have in etc/pm/power.d called wireless that has the following in it:

Turn off wifi power management
```
#!/bin/sh

/sbin/iwconfig wlan0 power off
```

FWIW, I had tried these commands and they didn't help:

```
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up
```

My detailed info is here in this thread, including configuration info:

[http://ubuntuforums.org/showthread.php?t=1915695](http://ubuntuforums.org/showthread.php?t=1915695)

I tried the commands on my setup:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

They ran without error, but I didn't get much in the way of improvement...still at .6 MB/s download...

---

### Post by Redflea on 2012-01-26
> **praseodym said:**
> Hi,

please show the terminal (CTRL+ALT+T) outputs of the commands:

```
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list
lsmod
```

My results:

lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Kernel driver in use: ath9k
	Kernel modules: ath9k
--
04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Device [11ab:4380] (rev 10)
	Kernel driver in use: sky2
	Kernel modules: sky2

rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: sony-wwan: Wireless WAN
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


lsusb
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0489:e00f Foxconn / Hon Hai 
Bus 001 Device 003: ID 05ca:18b5 Ricoh Co., Ltd 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


lsmod
Module                  Size  Used by
ath9k                 306106  0 
aes_i586                7268  2 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
ppdev                   5259  0 
rfcomm                 33453  4 
sco                     7949  2 
bridge                 45646  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30656  16 rfcomm,bnep
joydev                  8740  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  1 
vgastate                8961  1 vga16fb
nouveau               467048  0 
ttm                    49847  1 nouveau
drm_kms_helper         29329  1 nouveau
snd_hda_codec_realtek   203440  1 
drm                   163747  3 nouveau,ttm,drm_kms_helper
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm                70694  3 snd_pcm_oss,snd_hda_intel,snd_hda_codec
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
arc4                    1153  2 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
btusb                  11053  2 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
i2c_algo_bit            5028  1 nouveau
uvcvideo               57438  0 
videodev               34425  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
mac80211              205434  1 ath9k
video                  17375  0 
ath                     7611  1 ath9k
snd                    54244  16 snd_hda_codec_realtek,snd_pcm_oss,snd_mixer_oss,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lp                      7028  0 
output                  1871  1 video
sony_laptop            28248  0 
cfg80211              126528  3 ath9k,mac80211,ath
intel_agp              24375  0 
agpgart                31724  3 ttm,drm,intel_agp
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
psmouse                63677  0 
serio_raw               3978  0 
sdhci_pci               5470  0 
sdhci                  15494  1 sdhci_pci
led_class               2864  2 ath9k,sdhci
parport                32635  2 ppdev,lp
ohci1394               26950  0 
sky2                   40807  0 
ieee1394               81181  1 ohci1394
ahci                   32680  2

---

