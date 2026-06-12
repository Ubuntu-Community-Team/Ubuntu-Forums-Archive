---
title: "Wireless Networking disconnects - Ubuntu 10.04"
date: 2012-02-06
forum: Networking &amp; Wireless
---

### Post by seastick on 2012-02-06
On my Acer laptop my wireless connection started failing.  It would connect on startup but then drop off.  It then reconnected only to drop off and so on.  It connects then disconnects several times a minute - I had ping running and it would ping my wireless router for a while then say the network was unreachable.  I think this has only been since the latest update.  It makes it impossible to use.  Windows 7 on the same laptop connects fine so it doesn't seem to be hardware.
Also, the network manager applet that monitors the connection has disappeared from the panel!  How do I get it back - using " add to panel" doesn't list it at all.
All assistance gratefully received.

---

### Post by praseodym on 2012-02-06
Try

```
nm-applet
```

from terminal. Please show the outputs of

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by seastick on 2012-02-13
Thanks for that.  Here is the output as requested:

lspci:
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
    Kernel driver in use: tg3
    Kernel modules: tg3
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
    Kernel driver in use: ath9k
    Kernel modules: ath9k

lsusb:
Bus 002 Device 003: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 04fc:2801 Sunplus Technology Co., Ltd 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lsmod:
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
joydev                  8740  0 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_intelhdmi    11622  1 
snd_hda_codec_realtek   203440  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
snd_hda_intel          22165  2 
i915                  290500  3 
snd_hda_codec          74201  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70918  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ath9k                 306430  0 
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              205434  1 ath9k
ath                     7611  1 ath9k
drm_kms_helper         29329  1 i915
snd                    54244  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               57470  0 
videodev               34425  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
soundcore               6620  1 snd
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
psmouse                63677  0 
serio_raw               3978  0 
drm                   164436  4 i915,drm_kms_helper
intel_agp              24671  2 i915
cfg80211              126528  3 ath9k,mac80211,ath
led_class               2864  1 ath9k
agpgart                31788  2 drm,intel_agp
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36206  0 
hid                    67288  1 usbhid
usb_storage            40065  0 
tg3                   109580  0 
ahci                   32712  2 

iwconfig:
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

rfkill list:
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

I hope this is helpful.  It'd be really good to get a reliable connection again.

As an aside, can I get an email alert that there has been a reply to my posting?

Appreciate your help.

---

### Post by praseodym on 2012-02-13
Deactivate the hardware encryption of the driver and the power management of the card:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
sudo iwconfig wlan0 power off
```

---

### Post by seastick on 2012-02-13
Thanks, will do.  As it has become intermittent it might be a day or two before I can say it's solved.
Any idea why this may have become a problem?
Will I need to do this again if I update anything?
Thanks for your help, I appreciate it.

---

### Post by praseodym on 2012-02-14
Try to update the driver:

```
sudo apt-get install --reinstall linux-backports-modules-wireless-lucid-generic
```
and reboot.

---

### Post by seastick on 2012-02-16
All done, and so far no network failures.  Except that on start up the connection bounces several times before becoming stable - is this expected?  Can it be prevented - i.e. startup and the network connects, like it used to.
Also, has removing the hardware encryption made the system less secure?
Finally, will upgrading to 10.10 have any effect (positive or negative)?
Thanks for your help.

---

