---
title: "Wireless - device not ready."
date: 2012-02-26
forum: Networking &amp; Wireless
---

### Post by Sorrow7 on 2012-02-26
Hi guys, I would very much appreciate your help. I keep getting 'device not ready' under my wireless networks.

I have just upgraded my dell mini netbook from 8.04 to 10.04.

Here are some terminal outputs for information : 

> mark@mark-netbook:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Kernel driver in use: r8169
    Kernel modules: r8169

mark@mark-netbook:~$ lsusb
Bus 005 Device 002: ID 413c:02b0 Dell Computer Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0c45:63e4 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

mark@mark-netbook:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
rfcomm                 33453  4 
sco                     7949  2 
joydev                  8740  0 
bridge                 45646  0 
ppdev                   5259  0 
snd_hda_codec_realtek   203440  1 
stp                     1655  1 bridge
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bnep                    9436  2 
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
l2cap                  30656  16 rfcomm,bnep
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
dell_wmi                1793  0 
snd_timer              19130  2 snd_pcm,snd_seq
arc4                    1153  2 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  289715  3 
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
b43                   163556  0 
compal_laptop           2034  0 
uvcvideo               57438  0 
drm_kms_helper         29329  1 i915
mac80211              205434  1 b43
dcdbas                  5422  0 
psmouse                63677  0 
jmb38x_ms               7311  0 
intel_agp              24375  2 i915
sdhci_pci               5470  0 
videodev               34425  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
soundcore               6620  1 snd
drm                   163747  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
btusb                  11053  2 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
cfg80211              126528  2 b43,mac80211
serio_raw               3978  0 
sdhci                  15494  1 sdhci_pci
led_class               2864  2 b43,sdhci
memstick                8237  1 jmb38x_ms
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 intel_agp,drm
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
r8169                  34140  0 
mii                     4381  1 r8169
ssb                    38934  1 b43

mark@mark-netbook:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: compal-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: compal-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

mark@mark-netbook:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.

mark@mark-netbook:~$ sudo iwlist scan
[sudo] password for mark: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

pan0      Interface doesn't support scanning.I have preformed an update over a wired connection and still no luck.

Any help is appreciated.

---

### Post by praseodym on 2012-02-26
Firmware installation via:

```
wget [http://media.cdn.ubuntu-de.org/forum...irmware.tar.gz](http://media.cdn.ubuntu-de.org/forum...irmware.tar.gz) 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/
```

---

### Post by Sorrow7 on 2012-02-26
404 not found, bad link?

---

### Post by praseodym on 2012-02-26
Sorry, I c/p the link from another thread, it was abbreviated. Here is the "original" one:

```
wget [http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz) 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/
```
If not, click on the link and unpack it to "/lib/firmware" as described

---

### Post by Sorrow7 on 2012-02-26
awesome that works, thanks very much!

---

### Post by Sorrow7 on 2012-02-26
actually ..... no the wireless seems to be active and i have found my home network. however when I try to connect i type in the password and the wireless icon animates for about a minute till it asks me for the password again. the password is correct and the router is working with other wireless devices over the network. 

Any ideas?

---

### Post by praseodym on 2012-02-26
Any blanks or strange letters in the ESSID or the key? You are using the NetworkManager or Wicd?

---

### Post by Sorrow7 on 2012-02-26
Im not sure which one im using. Its just the standard connection manager that comes with 10.04, along the top panel. 

I just rebooted it and it did connect, but only briefly and i was unable to do anything over the connection.

---

### Post by praseodym on 2012-02-26
Checkbox all user sights in "USERS&GROUPS", login again, remove your wireless profile, and set up a new one. Seems to be the NM

---

### Post by Sorrow7 on 2012-02-26
I dont see the option for that? I tried selecting all the boxes and then deleting the wireless profile then rebooting and still not working.

---

### Post by Sorrow7 on 2012-02-26
As its a separate topic is moving this to [this thread]("http://ubuntuforums.org/showthread.php?p=11721279#post11721279"). Your continued help is appreciated!

---

