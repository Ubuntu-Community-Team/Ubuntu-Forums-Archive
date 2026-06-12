---
title: "Lock Up on Wifi connection on 11.04"
date: 2011-09-08
forum: Networking &amp; Wireless
---

### Post by trueppp on 2011-09-08
Hi I'm new to linux, wanted to try and see if I can use my HP Mini-Note 2133 for its intended purpose (email, remote debugging, emergency software fixes). Everything is
going good except that as soon as i get a wifi connection, linux locks up.
 
I saw that in additional drivers i have the broadcomm STA driver installed, tried deactivating it and installing the b43 driver and it still locks up.
 
Has anyone had this problem before?

---

### Post by praseodym on 2011-09-08
Hi,

can you show:

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```
Can you reset the BIOS to manufacturer settings?

---

### Post by trueppp on 2011-09-08
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4312 802.11b/g Wireless LAN Controller [103c:137c]
    Kernel driver in use: wl
--
07:03.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet [14e4:169c] (rev 03)
    Subsystem: Broadcom Corporation Device [14e4:969c]
    Kernel driver in use: tg3

Module                  Size  Used by
via                    45203  0 
drm                   180037  1 via
rfcomm                 38125  8 
sco                    17779  2 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
btusb                  18160  2 
bluetooth              65565  9 rfcomm,sco,bnep,l2cap,btusb
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
snd_hda_codec_analog    75442  1 
snd_hda_intel          24140  2 
binfmt_misc            13213  1 
snd_hda_codec          90901  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               66851  0 
hp_wmi                 13418  0 
joydev                 17322  0 
snd_timer              28659  2 snd_pcm,snd_seq
sparse_keymap          13666  1 hp_wmi
lib80211_crypt_tkip    17203  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
wl                   2642531  0 
snd                    55295  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               75143  1 uvcvideo
psmouse                73312  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
shpchp                 32345  0 
i2c_viapro             12969  0 
serio_raw              12990  0 
hp_accel               21632  0 
video                  18951  0 
lib80211               14570  2 lib80211_crypt_tkip,wl
lis3lv02d              19285  1 hp_accel
input_polldev          13735  1 lis3lv02d
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
tg3                   131476  0 
hid                    77084  1 usbhid
sata_via               13464  2 


lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

---

### Post by lkjoel on 2011-09-08
Try this:
```
echo 'blacklist b43' | sudo tee -a /etc/modprobe.d/blacklist.conf
echo 'blacklist b44' | sudo tee -a /etc/modprobe.d/blacklist.conf

```
And reboot.

---

### Post by trueppp on 2011-09-08
Will do as soon as possible

---

### Post by trueppp on 2011-09-08
Did not work

---

### Post by lkjoel on 2011-09-09
Try this: [http://ubuntuforums.org/showpost.php?p=11218804&postcount=35](http://ubuntuforums.org/showpost.php?p=11218804&postcount=35)

---

