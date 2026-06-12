---
title: "BCM4331 problems"
date: 2013-04-09
forum: Networking &amp; Wireless
---

### Post by andrix10 on 2013-04-09
For some reason recently my wireless connection is unstable, it connects for a while then dces and cant establish connection anymore
```
03:00.0 Network controller: Broadcom Corporation BCM4331 802.11a/b/g/n (rev 02)
```
i tried fixing it by using this [https://help.ubuntu.com/community/MacBookPro8-2/Oneiric#Wireless](https://help.ubuntu.com/community/MacBookPro8-2/Oneiric#Wireless) but it didnt fix it
I have ubuntu 12.04 LTS

---

### Post by Hadaka on 2013-04-09
Hi, please post the output of..
```
lspci -nn | egrep '0200|0280'
lsmod
rfkill list all
```
thanks.

---

### Post by andrix10 on 2013-04-09
```
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4] (rev 10)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
```

```
Module                  Size  Used by
btrfs                 638248  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
ufs                    78131  0 
qnx4                   13309  0 
hfsplus                83544  0 
hfs                    49479  0 
minix                  31453  0 
ntfs                  100206  0 
vfat                   17308  0 
msdos                  17132  0 
fat                    55605  2 vfat,msdos
jfs                   175085  0 
xfs                   747494  0 
reiserfs              230943  0 
ext2                   67987  0 
usb_storage            39683  0 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_cirrus    23322  1 
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 37291  0 
bnep                   17711  2 
arc4                   12473  2 
b43                   339138  0 
snd_hda_intel          32719  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac80211              440734  1 b43
cfg80211              178818  2 b43,mac80211
snd_seq_midi           13132  0 
i915                  423514  4 
drm_kms_helper         45466  1 i915
drm                   197641  5 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
joydev                 17393  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
bcma                   25587  1 b43
ssb                    55319  1 b43
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               67203  0 
apple_gmux             12655  0 
videodev               86588  1 uvcvideo
applesmc               18978  0 
bcm5974                17199  0 
input_polldev          13648  1 applesmc
pcmcia                 39826  2 b43,ssb
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mei                    36570  0 
video                  19115  2 i915,apple_gmux
apple_bl               13425  0 
pcmcia_core            21511  1 pcmcia
mac_hid                13077  0 
snd                    62218  16 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
btusb                  17919  1 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
bluetooth             164387  13 rfcomm,bnep,btusb
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
hid_apple              13166  0 
usbhid                 41937  0 
hid                    77428  2 hid_apple,usbhid
firewire_ohci          40180  0 
firewire_core          56940  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
tg3                   137318  0 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
```

```
0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no



```

---

### Post by Hadaka on 2013-04-09
Hi, let's get rid of this first,
```

1: phy0: Wireless LAN     Soft blocked: yes
```

click the wireless icon...upper right and make sure the wireless
enable is checked.
please check and report back
thanks.

---

### Post by andrix10 on 2013-04-09
well im really sorry about that, using the usb tethering and forgot that i turned off wifi

```
Module                  Size  Used bybtrfs                 638248  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
ufs                    78131  0 
qnx4                   13309  0 
hfsplus                83544  0 
hfs                    49479  0 
minix                  31453  0 
ntfs                  100206  0 
vfat                   17308  0 
msdos                  17132  0 
fat                    55605  2 vfat,msdos
jfs                   175085  0 
xfs                   747494  0 
reiserfs              230943  0 
ext2                   67987  0 
usb_storage            39683  0 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_cirrus    23322  1 
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 37291  0 
bnep                   17711  2 
arc4                   12473  2 
b43                   339138  0 
snd_hda_intel          32719  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac80211              440734  1 b43
cfg80211              178818  2 b43,mac80211
snd_seq_midi           13132  0 
i915                  423514  4 
drm_kms_helper         45466  1 i915
drm                   197641  5 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
joydev                 17393  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
bcma                   25587  1 b43
ssb                    55319  1 b43
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               67203  0 
apple_gmux             12655  0 
videodev               86588  1 uvcvideo
applesmc               18978  0 
bcm5974                17199  0 
input_polldev          13648  1 applesmc
pcmcia                 39826  2 b43,ssb
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mei                    36570  0 
video                  19115  2 i915,apple_gmux
apple_bl               13425  0 
pcmcia_core            21511  1 pcmcia
mac_hid                13077  0 
snd                    62218  16 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
btusb                  17919  1 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
bluetooth             164387  13 rfcomm,bnep,btusb
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
hid_apple              13166  0 
usbhid                 41937  0 
hid                    77428  2 hid_apple,usbhid
firewire_ohci          40180  0 
firewire_core          56940  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
tg3                   137318  0 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci



```

```
0: hci0: Bluetooth    
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no



```

---

### Post by andrix10 on 2013-04-09
well im really sorry about that, using the usb tethering and forgot that i turned off wifi

```
Module                  Size  Used bybtrfs                 638248  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
ufs                    78131  0 
qnx4                   13309  0 
hfsplus                83544  0 
hfs                    49479  0 
minix                  31453  0 
ntfs                  100206  0 
vfat                   17308  0 
msdos                  17132  0 
fat                    55605  2 vfat,msdos
jfs                   175085  0 
xfs                   747494  0 
reiserfs              230943  0 
ext2                   67987  0 
usb_storage            39683  0 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_cirrus    23322  1 
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 37291  0 
bnep                   17711  2 
arc4                   12473  2 
b43                   339138  0 
snd_hda_intel          32719  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac80211              440734  1 b43
cfg80211              178818  2 b43,mac80211
snd_seq_midi           13132  0 
i915                  423514  4 
drm_kms_helper         45466  1 i915
drm                   197641  5 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
joydev                 17393  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
bcma                   25587  1 b43
ssb                    55319  1 b43
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               67203  0 
apple_gmux             12655  0 
videodev               86588  1 uvcvideo
applesmc               18978  0 
bcm5974                17199  0 
input_polldev          13648  1 applesmc
pcmcia                 39826  2 b43,ssb
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mei                    36570  0 
video                  19115  2 i915,apple_gmux
apple_bl               13425  0 
pcmcia_core            21511  1 pcmcia
mac_hid                13077  0 
snd                    62218  16 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
btusb                  17919  1 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
bluetooth             164387  13 rfcomm,bnep,btusb
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
hid_apple              13166  0 
usbhid                 41937  0 
hid                    77428  2 hid_apple,usbhid
firewire_ohci          40180  0 
firewire_core          56940  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
tg3                   137318  0 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci



```

```
0: hci0: Bluetooth    
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no



```

i assume [COLOR=#000000][FONT=Ubuntu Mono]lspci -nn | egrep '0200|0280' will be the same[/FONT][/COLOR]

---

### Post by Hadaka on 2013-04-09
Hi, thanks for unblocking that..
ok lets see if we can get you going...
please do..
```
sudo apt-get install linux-firmware-nonfree 
sudo modprobe -r b43
sudo modprobe b43
```

*IF it continues to drop out after this
see next post.
thanks.

---

### Post by Hadaka on 2013-04-09
your card  is b/g/n and a broadcom,
for whatever reason broadcom and linux dont always
function correctly at N speeds. so.... you can perhaps
disable the N part in your router, providing you dont have
other computers using N speed. another possible fix is to
issue this command towards your wifi card.

```
sudo modprobe -r b43
sudo modprobe b43 nohwcrypt=1
```
hope this helps.

---

