---
title: "wireless disabled"
date: 2012-04-13
forum: Networking &amp; Wireless
---

### Post by fire planet on 2012-04-13
hi,
i installed ubuntu11.10 just now,but wireless is disable !! on network menu(on the top of desktop) i can see an option for enabling the wireless but it is inactive.
&#1614;Also i opened the network setting and set the wireless on, but strangely it doesn't remain on !
any suggestion to solve this problem?

i had not connect to internet when i installing the ubuntu,i dont know but may it cause the problem?

---

### Post by praseodym on 2012-04-13
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of:

```
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list
lsmod
```
What computer is that?

---

### Post by fire planet on 2012-04-14
i entered those command in terminal ,  a lot of information displayed :

 **lspci -nnk | grep -iA2 net :**
```
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57790 Gigabit Ethernet PCIe [14e4:1694] (rev 01)
    Subsystem: Lenovo Device [17aa:38d3]
    Kernel driver in use: tg3
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0510]
    Kernel driver in use: brcmsmac
```


**lsusb :**
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 090c:37b5 Feiya Technology Corp. 
Bus 005 Device 002: ID 0489:e00d Foxconn / Hon Hai 
```

**iwconfig :**
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```
          
**rfkill list :**
```
0: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
4: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

```

**lsmod :**
```
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  8 
parport_pc             32114  0 
ppdev                  12849  0 
wl                   2646601  0 
lib80211               14570  1 wl
bcma                   19571  0 
arc4                   12473  2 
joydev                 17393  0 
acer_wmi               23302  0 
snd_hda_codec_conexant    52418  1 
uvcvideo               67271  0 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
videodev               85626  1 uvcvideo
brcmsmac              591864  0 
snd_seq_midi           13132  0 
brcmutil               16885  1 brcmsmac
btusb                  18160  2 
snd_rawmidi            25241  1 snd_seq_midi
psmouse                73673  0 
serio_raw              12990  0 
bluetooth             148839  23 bnep,rfcomm,btusb
mac80211              272785  1 brcmsmac
snd_seq_midi_event     14475  1 snd_seq_midi
binfmt_misc            17292  1 
cfg80211              172392  2 brcmsmac,mac80211
ideapad_laptop         13575  0 
sparse_keymap          13658  2 acer_wmi,ideapad_laptop
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
crc_ccitt              12595  1 brcmsmac
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    18744  1 acer_wmi
i915                  505108  3 
snd                    55902  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
drm_kms_helper         32889  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
drm                   192226  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            13096  0 
usb_storage            44173  1 ums_realtek
uas                    17699  0 
ahci                   21634  1 
libahci                25727  1 ahci
tg3                   132972  0 
```

what should i do now?

---

### Post by fire planet on 2012-04-14
i solved my wireless problem from this link:
[http://askubuntu.com/questions/98168/i-cant-enable-an-intel-5100agn-wireless-card](http://askubuntu.com/questions/98168/i-cant-enable-an-intel-5100agn-wireless-card)

---

