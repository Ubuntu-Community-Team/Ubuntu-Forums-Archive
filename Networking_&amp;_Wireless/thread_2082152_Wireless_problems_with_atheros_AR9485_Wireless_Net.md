---
title: "Wireless problems with atheros AR9485 Wireless Network Adapter."
date: 2012-11-08
forum: Networking &amp; Wireless
---

### Post by karnpreet on 2012-11-08
Hello,

I've recently purchased a custom built computer with no OS on it. I installed ubuntu onto it and it has a ASUS motherboad P8z77-V and a atheros AR9485 Wireless Network Adapter. It recognises the wireless router I have but it doesn't connect at all to it, it just keeps asking for the password. I really have no clue about computers so I was wondering whether someone can help me. I have the CD for the motherboard but for some reason it doesn't seem to run everytime I put it in. What shall I do?

---

### Post by NikTh on 2012-11-08
Hi and Welcome. 

Please open a terminal (CTRL+ALT+T) and copy-paste from here bellow commands one line at time. 
```
lsb_release -rcd ; uname -r
lspci -nnk | grep -iA2 net
lsmod
rfkill list all
nmcli nm status
```

Post the results back here and [put the results inside [CODE] tags.](http://ubuntuforums.org/attachment.php?attachmentid=226831&d=1352305838)

Thanks

---

### Post by karnpreet on 2012-11-08
sorry I'm taking ages to reply back, I have no internet connection on my desktop computer so I'm having to type it all out onto this, i will be posting it soon

---

### Post by karnpreet on 2012-11-08
> kevin@Kevlar:~$ lsb_release -rcd ; uname -r
Description:    Ubuntu 12.10
Release:    12.10
Codename:    quantal
3.5.0-17-generic
kevin@Kevlar:~$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 04)
    Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard [1043:849c]
    Kernel driver in use: e1000e
--
06:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device [1043:850d]
    Kernel driver in use: ath9k
kevin@Kevlar:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
isofs                  39842  1 
parport_pc             32688  0 
ppdev                  17073  0 
bnep                   18140  2 
rfcomm                 46619  0 
bluetooth             209199  10 bnep,rfcomm
ext2                   72880  1 
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_realtek    77876  1 
coretemp               13400  0 
snd_seq_midi           13324  0 
kvm                   414070  0 
snd_hda_intel          33491  5 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_rawmidi            30512  1 snd_seq_midi
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12529  2 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
eeepc_wmi              13109  0 
asus_wmi               24088  1 eeepc_wmi
snd                    78734  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_rawmidi,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
sparse_keymap          13890  1 asus_wmi
ath9k                 131308  0 
microcode              22803  0 
mac80211              539908  1 ath9k
lpc_ich                17061  0 
joydev                 17457  0 
ath9k_common           14055  1 ath9k
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
mac_hid                13205  0 
ath9k_hw              395218  2 ath9k,ath9k_common
psmouse                95552  0 
ath                    23827  3 ath9k,ath9k_common,ath9k_hw
serio_raw              13215  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
cfg80211              206566  3 ath9k,mac80211,ath
mei                    40690  0 
xts                    12880  8 
gf128mul               14951  1 xts
dm_crypt               23011  1 
hid_generic            12493  0 
usbhid                 46947  0 
hid                   100366  2 hid_generic,usbhid
mxm_wmi                12979  0 
ghash_clmulni_intel    13180  0 
aesni_intel            51037  32 
cryptd                 20403  10 ghash_clmulni_intel,aesni_intel
aes_x86_64             17208  1 aesni_intel
radeon                895653  3 
ttm                    83595  1 radeon
drm_kms_helper         46784  1 radeon
drm                   275528  5 radeon,ttm,drm_kms_helper
e1000e                199114  0 
i2c_algo_bit           13413  1 radeon
video                  19335  0 
wmi                    19070  2 asus_wmi,mxm_wmi
kevin@Kevlar:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
isofs                  39842  1 
parport_pc             32688  0 
ppdev                  17073  0 
bnep                   18140  2 
rfcomm                 46619  0 
bluetooth             209199  10 bnep,rfcomm
ext2                   72880  1 
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_realtek    77876  1 
coretemp               13400  0 
snd_seq_midi           13324  0 
kvm                   414070  0 
snd_hda_intel          33491  5 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_rawmidi            30512  1 snd_seq_midi
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12529  2 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
eeepc_wmi              13109  0 
asus_wmi               24088  1 eeepc_wmi
snd                    78734  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_rawmidi,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
sparse_keymap          13890  1 asus_wmi
ath9k                 131308  0 
microcode              22803  0 
mac80211              539908  1 ath9k
lpc_ich                17061  0 
joydev                 17457  0 
ath9k_common           14055  1 ath9k
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
mac_hid                13205  0 
ath9k_hw              395218  2 ath9k,ath9k_common
psmouse                95552  0 
ath                    23827  3 ath9k,ath9k_common,ath9k_hw
serio_raw              13215  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
cfg80211              206566  3 ath9k,mac80211,ath
mei                    40690  0 
xts                    12880  8 
gf128mul               14951  1 xts
dm_crypt               23011  1 
hid_generic            12493  0 
usbhid                 46947  0 
hid                   100366  2 hid_generic,usbhid
mxm_wmi                12979  0 
ghash_clmulni_intel    13180  0 
aesni_intel            51037  32 
cryptd                 20403  10 ghash_clmulni_intel,aesni_intel
aes_x86_64             17208  1 aesni_intel
radeon                895653  3 
ttm                    83595  1 radeon
drm_kms_helper         46784  1 radeon
drm                   275528  5 radeon,ttm,drm_kms_helper
e1000e                199114  0 
i2c_algo_bit           13413  1 radeon
video                  19335  0 
wmi                    19070  2 asus_wmi,mxm_wmi
kevin@Kevlar:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
kevin@Kevlar:~$ nmcli nm status
RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running         disconnected    enabled         enabled    enabled         disabled  


this is what i get when i put those codes in

---

### Post by karnpreet on 2012-11-08
Hello,

I've recently purchased a custom built computer with no OS on it. I  installed ubuntu onto it and it has a ASUS motherboad P8z77-V and a  atheros AR9485 Wireless Network Adapter. It recognises the wireless  router I have but it doesn't connect for a while, and then it connects before disconnecting before a page loads up. I really have no clue about computers so I was  wondering whether someone can help me. I have the CD for the motherboard  but for some reason it doesn't seem to run everytime I put it in. I've just changed the channel setting on the modem as well to see whether it was that but that doesn't make a difference at all. I was told by someone to print this out as you might find it helpful in solving the problem:- 
```

kevin@Kevlar:~$ lsb_release -rcd ; uname -r
Description:    Ubuntu 12.10
Release:    12.10
Codename:    quantal
3.5.0-17-generic
kevin@Kevlar:~$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 04)
    Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard [1043:849c]
    Kernel driver in use: e1000e
--
06:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device [1043:850d]
    Kernel driver in use: ath9k
kevin@Kevlar:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
isofs                  39842  1 
parport_pc             32688  0 
ppdev                  17073  0 
bnep                   18140  2 
rfcomm                 46619  0 
bluetooth             209199  10 bnep,rfcomm
ext2                   72880  1 
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_realtek    77876  1 
coretemp               13400  0 
snd_seq_midi           13324  0 
kvm                   414070  0 
snd_hda_intel          33491  5 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_i  ntel
snd_rawmidi            30512  1 snd_seq_midi
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12529  2 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
eeepc_wmi              13109  0 
asus_wmi               24088  1 eeepc_wmi
snd                    78734  20  snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_i   ntel,snd_hda_codec,snd_rawmidi,snd_hwdep,snd_pcm,s   nd_seq,snd_timer,snd_seq_device
sparse_keymap          13890  1 asus_wmi
ath9k                 131308  0 
microcode              22803  0 
mac80211              539908  1 ath9k
lpc_ich                17061  0 
joydev                 17457  0 
ath9k_common           14055  1 ath9k
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
mac_hid                13205  0 
ath9k_hw              395218  2 ath9k,ath9k_common
psmouse                95552  0 
ath                    23827  3 ath9k,ath9k_common,ath9k_hw
serio_raw              13215  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
cfg80211              206566  3 ath9k,mac80211,ath
mei                    40690  0 
xts                    12880  8 
gf128mul               14951  1 xts
dm_crypt               23011  1 
hid_generic            12493  0 
usbhid                 46947  0 
hid                   100366  2 hid_generic,usbhid
mxm_wmi                12979  0 
ghash_clmulni_intel    13180  0 
aesni_intel            51037  32 
cryptd                 20403  10 ghash_clmulni_intel,aesni_intel
aes_x86_64             17208  1 aesni_intel
radeon                895653  3 
ttm                    83595  1 radeon
drm_kms_helper         46784  1 radeon
drm                   275528  5 radeon,ttm,drm_kms_helper
e1000e                199114  0 
i2c_algo_bit           13413  1 radeon
video                  19335  0 
wmi                    19070  2 asus_wmi,mxm_wmi
kevin@Kevlar:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
isofs                  39842  1 
parport_pc             32688  0 
ppdev                  17073  0 
bnep                   18140  2 
rfcomm                 46619  0 
bluetooth             209199  10 bnep,rfcomm
ext2                   72880  1 
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_realtek    77876  1 
coretemp               13400  0 
snd_seq_midi           13324  0 
kvm                   414070  0 
snd_hda_intel          33491  5 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_i  ntel
snd_rawmidi            30512  1 snd_seq_midi
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12529  2 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
eeepc_wmi              13109  0 
asus_wmi               24088  1 eeepc_wmi
snd                    78734  20  snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_i   ntel,snd_hda_codec,snd_rawmidi,snd_hwdep,snd_pcm,s   nd_seq,snd_timer,snd_seq_device
sparse_keymap          13890  1 asus_wmi
ath9k                 131308  0 
microcode              22803  0 
mac80211              539908  1 ath9k
lpc_ich                17061  0 
joydev                 17457  0 
ath9k_common           14055  1 ath9k
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
mac_hid                13205  0 
ath9k_hw              395218  2 ath9k,ath9k_common
psmouse                95552  0 
ath                    23827  3 ath9k,ath9k_common,ath9k_hw
serio_raw              13215  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
cfg80211              206566  3 ath9k,mac80211,ath
mei                    40690  0 
xts                    12880  8 
gf128mul               14951  1 xts
dm_crypt               23011  1 
hid_generic            12493  0 
usbhid                 46947  0 
hid                   100366  2 hid_generic,usbhid
mxm_wmi                12979  0 
ghash_clmulni_intel    13180  0 
aesni_intel            51037  32 
cryptd                 20403  10 ghash_clmulni_intel,aesni_intel
aes_x86_64             17208  1 aesni_intel
radeon                895653  3 
ttm                    83595  1 radeon
drm_kms_helper         46784  1 radeon
drm                   275528  5 radeon,ttm,drm_kms_helper
e1000e                199114  0 
i2c_algo_bit           13413  1 radeon
video                  19335  0 
wmi                    19070  2 asus_wmi,mxm_wmi
kevin@Kevlar:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
kevin@Kevlar:~$ nmcli nm status
RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running         disconnected    enabled         enabled    enabled         disabled
```

---

### Post by NikTh on 2012-11-08
OK,
2 things I can see. 

1) The network-manager seems disabled-disconnected 
> ```
RUNNING STATE WIFI-HARDWARE WIFI WWAN-HARDWARE WWAN 
running disconnected enabled enabled enabled disabled
```

2)You use the ath9k module .This module has an option that might help you to stabilize your connection.

First try with network-manager , this command 

```
nmcli nm enabled true
``` and see if things are better. 

OR

Try this code 
```
echo 'options ath9k nohwcrypt=1' | sudo tee /etc/modprobe.d/ath9k.conf
``` 
and reboot your PC to see.

Thanks

---

### Post by ahallubuntu on 2012-11-08
If you have "no clue" about computers, I'm going to suggest you stick to the 12.04 LTS version of Ubuntu, because that one will be supported until 2017 whereas 12.10 will be supported for only another 18 months.

You'll probably have the same wireless issues in 12.04, though.  It seems one solution for your card is found here:

[http://ubuntuforums.org/showthread.php?mode=hybrid&t=1942326&highlight=atheros+acer+722](http://ubuntuforums.org/showthread.php?mode=hybrid&t=1942326&highlight=atheros+acer+722)

First try the fix there to disable hardware encryption.  Open terminal window then type:

```
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k nohwcrypt=1
```

If that works, make it permanent this way:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf 
```

---

### Post by mörgæs on 2012-11-09
Please don't double-post.
Threads merged.

---

### Post by gkorland on 2013-05-16
I'm having the same problem (moving from Win7 to Ubuntu 13.04) but non of the above solutions helped.

---

### Post by praseodym on 2013-05-16
Dear gkorland,

please show these outputs:
```

lspci -nnk | grep -iA2 net
lsmod
iwconfig
ifconfig -a
rfkill list
sudo iwlist scan
```

---

### Post by Stickee on 2013-06-01
> **ahallubuntu said:**
> If you have "no clue" about computers, I'm going to suggest you stick to the 12.04 LTS version of Ubuntu, because that one will be supported until 2017 whereas 12.10 will be supported for only another 18 months.

You'll probably have the same wireless issues in 12.04, though.  It seems one solution for your card is found here:

[http://ubuntuforums.org/showthread.php?mode=hybrid&t=1942326&highlight=atheros+acer+722](http://ubuntuforums.org/showthread.php?mode=hybrid&t=1942326&highlight=atheros+acer+722)

First try the fix there to disable hardware encryption.  Open terminal window then type:

```
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k nohwcrypt=1
```

If that works, make it permanent this way:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf 
```

Thanks this fixed it for me.

I was able to connect to my router, but was getting around 50% packet loss and very high pings.  This fix has stabilized things for me.

---

