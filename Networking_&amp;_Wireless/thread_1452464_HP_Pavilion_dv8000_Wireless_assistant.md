---
title: "HP Pavilion dv8000 Wireless assistant"
date: 2010-04-12
forum: Networking &amp; Wireless
---

### Post by saintindica on 2010-04-12
I am new to ubuntu and because it runs so much better on this laptop I have completely erased windows from my computer. The only problem is I can not download/run hp's wireless assistant, and wicd doesn't seem to help. I'm hoping someone knows how to fix this problem. Thanks in advance for any helpful advice!

---

### Post by chili555 on 2010-04-12
What does Wireless Assistant do for you? Install the drivers for your wireless card? Locate networks to connect to? All of those things are available in Ubuntu. Please tell us what you are trying to do.

---

### Post by saintindica on 2010-04-12
Wireless assistant installs my wireless driver and toggles the on/off switch for my wifi. As of now I can not even switch it on. I have tried updating, downloading available drivers from the Hardware Drivers tool and downloading the wireless assistant exe from hp. What else can I do?

---

### Post by chili555 on 2010-04-12
Please open a terminal and do:```
sudo rfkill unblock all
rfkill list
```What kind of laptop is it? Please post:```
lsmod
```Thanks.

---

### Post by saintindica on 2010-04-12
I ran both of these and this is what came up:

sean@sean-laptop:~$ sudo rfkill unblock all
[sudo] password for sean: 
sean@sean-laptop:~$ rfkill list
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
sean@sean-laptop:~$ lsmod
Module                  Size  Used by
usblp                  12636  0 
isofs                  31620  0 
udf                    80900  0 
crc_itu_t               1852  1 udf
nls_iso8859_1           3740  0 
nls_cp437               5372  0 
vfat                   10716  0 
fat                    51452  1 vfat
binfmt_misc             8356  1 
ppdev                   6688  0 
iptable_filter          3100  0 
snd_atiixp             15720  2 
snd_atiixp_modem       11940  5 
snd_ac97_codec        101216  2 snd_atiixp,snd_atiixp_modem
ac97_bus                1532  1 snd_ac97_codec
snd_seq_dummy           2656  0 
ip_tables              11692  1 iptable_filter
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
pcmcia                 36808  0 
snd_pcm                75296  6 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
arc4                    1660  2 
snd_rawmidi            22176  1 snd_seq_midi
ecb                     2524  2 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
b43                   122200  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
x_tables               16544  1 ip_tables
yenta_socket           24296  1 
mac80211              181140  1 b43
rsrc_nonstatic         11644  1 yenta_socket
i2c_piix4               9932  0 
joydev                 10240  0 
sdhci_pci               7100  0 
cfg80211               93052  2 b43,mac80211
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
sdhci                  17504  1 sdhci_pci
tifm_7xx1               5372  0 
tifm_core               7832  1 tifm_7xx1
led_class               4096  2 b43,sdhci
k8temp                  4188  0 
snd                    59204  23 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
shpchp                 32272  0 
snd_page_alloc          9156  3 snd_atiixp,snd_atiixp_modem,snd_pcm
psmouse                56500  0 
serio_raw               5280  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
usb_storage            52768  0 
ssb                    35524  1 b43
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
8139too                22620  0 
8139cp                 19260  0 
mii                     5212  2 8139too,8139cp
radeon                636000  2 
ttm                    36212  1 radeon
drm                   160032  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
video                  19380  0 
output                  2780  1 video
ati_agp                 6760  0 
agpgart                34988  3 ttm,drm,ati_agp
.
Thanks for the help.

---

### Post by chili555 on 2010-04-13
Your wireless is not turned off. > $ rfkill list
1: phy1: Wireless LAN
Soft blocked: no
Hard blocked: noThe LED may or may not be working, but the wireless radio itself is on.

The correct driver for your wireless card is loaded:> [COLOR="Red"]b43[/COLOR] 122200 0
mac80211 181140 1 [COLOR="Red"]b43[/COLOR]Let's see if the needed firmware is loaded:```
ls /lib/firmware/b43
```If you get a listing of firmware files, for instance, ucode5.fw, ucode9.fw, etc., then you have the firmware. Now, run:```
iwconfig
```Do you have a wireless interface, wlan0 perhaps? If so, detach the ethernet cable, click the Network Manager icon and try to connect.

If not, let's look under the hood and figure out what's going wrong. Please post:```
dmesg | grep b43
```

---

### Post by Bucky Ball on 2010-04-13
Plug in an ethernet cable and boot the computer and get online. You should get a bunch of updates. With any luck, the wireless card will be picked up and you will be offered the restricted drivers. Try this before getting anymore involved.

Also, System->Admin->Hardware Drivers. Anything disabled in there? Most HP cards work fine nowadays without endless tweaking. Just plug that cable in if you haven't already. The easy way to set up the card. Forget wireless assistant, a windows thing. You don't need it.

---

### Post by chili555 on 2010-04-13
> **Bucky Ball said:**
> Plug in an ethernet cable and boot the computer and get online. You should get a bunch of updates. With any luck, the wireless card will be picked up and you will be offered the restricted drivers. Try this before getting anymore involved.

Also, System->Admin->Hardware Drivers. Anything disabled in there? Most HP cards work fine nowadays without endless tweaking. Just plug that cable in if you haven't already. The easy way to set up the card. Forget wireless assistant, a windows thing. You don't need it.I think he has done all that:> I have tried updating, downloading available drivers from the Hardware Drivers tool 

---

### Post by saintindica on 2010-04-13
Ok so it looks like I don't have the firmware for this. Here is what I got from running those commands:

sean@sean-laptop:~$ ls /lib.firmware/b43
ls: cannot access /lib.firmware/b43: No such file or directory
sean@sean-laptop:~$ ls/lib/firmware/b43
bash: ls/lib/firmware/b43: No such file or directory
sean@sean-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sean@sean-laptop:~$ dmesg | grep b43
[    2.492774] b43-pci-bridge 0000:06:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   12.512811] b43-phy0: Broadc

Thanks Chili, wouldn't be able to figure this out without your help!

---

### Post by chili555 on 2010-04-13
You still have the command wrong. It is not:```
sean@sean-laptop:~$ ls/lib/firmware/b43
```It is, instead:```
sean@sean-laptop:~$ ls  /lib/firmware/b43
```The space inbetween 'ls' and '/lib/firmware/b43' is important and needed. Please try again.

---

### Post by saintindica on 2010-04-13
Sorry about that, here it is again:

sean@sean-laptop:~$ ls /lib/firmware/b43
a0g0bsinitvals5.fw   a0g1initvals5.fw     lp0bsinitvals13.fw  n0initvals11.fw
a0g0bsinitvals9.fw   a0g1initvals9.fw     lp0bsinitvals14.fw  pcm5.fw
a0g0initvals5.fw     b0g0bsinitvals13.fw  lp0bsinitvals15.fw  ucode11.fw
a0g0initvals9.fw     b0g0bsinitvals5.fw   lp0initvals13.fw    ucode13.fw
a0g1bsinitvals13.fw  b0g0bsinitvals9.fw   lp0initvals14.fw    ucode14.fw
a0g1bsinitvals5.fw   b0g0initvals13.fw    lp0initvals15.fw    ucode15.fw
a0g1bsinitvals9.fw   b0g0initvals5.fw     n0absinitvals11.fw  ucode5.fw
a0g1initvals13.fw    b0g0initvals9.fw     n0bsinitvals11.fw   ucode9.fw

---

### Post by chili555 on 2010-04-13
You have the firmware, you have an interface, dmesg doesn't report any complaints, so click the Network manager icon and connect, please. You will need to detach the ethernet cable first. NM will not connect wirelessly if you already have an ethernet connection.

---

### Post by saintindica on 2010-04-13
Scratch that...I was using wicd nm instead of network manager. Installed and ran and I am now connected. Thanks for helping out a n00b.

---

### Post by chili555 on 2010-04-13
Please try:```
sudo iwconfig wlan0 power on
sudo iwconfig wlan0 txpower 20
```If the '20' option works, try 22, then 23, etc. until it errors. If 20 errors, try 15, 14, etc. until we have the highest possible txpower. Then do:```
sudo iwlist wlan0 scan
```Please post the result. If you do get scan results, try Wicd again.

---

### Post by ubernes on 2010-04-25
So I've had the same problem and followed the whole thread, but sadly for me my wireless is still not working. Here's what I got from the last step:

mark@mark-laptop:~$ sudo iwconfig wlan0 power on
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
mark@mark-laptop:~$ sudo iwconfig wlan0 txpower 20
mark@mark-laptop:~$ sudo iwconfig wlan0 txpower 22
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan0 ; Invalid argument.
mark@mark-laptop:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down

:confused:

---

### Post by GoodMourning on 2010-07-25
I've also been following this thread. It appears I don't have the firmware. Any help on how to get it? I'll post my terminal stuff below.

sam@sam-laptop:~$ sudo rfkill unblock all
sam@sam-laptop:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
sam@sam-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_intelhdmi    13090  1 
snd_hda_codec_idt      61418  1 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
arc4                    1473  2 
snd_hda_intel          25645  2 
snd_hda_codec          85727  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
b43                   174953  0 
mac80211              238128  1 b43
i915                  317872  3 
drm_kms_helper         30742  1 i915
snd                    70978  17 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               62403  0 
videodev               40486  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
drm                   198770  4 i915,drm_kms_helper
i2c_algo_bit            6024  1 i915
psmouse                64608  0 
jmb38x_ms               8643  0 
serio_raw               4918  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
cfg80211              148386  2 b43,mac80211
intel_agp              29225  2 i915
memstick               10121  1 jmb38x_ms
sdhci_pci               6700  0 
sdhci                  17928  1 sdhci_pci
joydev                 11072  0 
hp_accel               12168  0 
lis3lv02d               7583  1 hp_accel
input_polldev           3106  1 lis3lv02d
video                  20623  1 i915
led_class               3732  3 b43,sdhci,hp_accel
output                  2503  1 video
lirc_ene0100            7532  0 
lirc_dev               11302  1 lirc_ene0100
lp                      9336  0 
parport                37160  2 ppdev,lp
ssb                    43517  1 b43
ahci                   37646  2 
r8169                  39554  0 
mii                     5237  1 r8169
sam@sam-laptop:~$ ls /lib/firmware/b43
ls: cannot access /lib/firmware/b43: No such file or directory

---

### Post by chili555 on 2010-07-25
Can you hook up the ethernet cable and then click System > Administration > Hardware Drivers? The firmware will be downloaded and installed for you automagically.

---

### Post by Zaopunk on 2010-12-20
Ok I am in the same boat, but when I tried this part I came up with
0: hp-wifi: Wireless LAN
     Soft blocked: no
     Hard blocked: yes
1: phy0: Wireless LAN
   soft blocked: no
   Hard blocked: no

I can't get the ethernet to connect either...

---

