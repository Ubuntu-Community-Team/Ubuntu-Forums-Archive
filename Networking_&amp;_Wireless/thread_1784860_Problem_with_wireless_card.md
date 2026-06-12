---
title: "Problem with wireless card"
date: 2011-06-17
forum: Networking &amp; Wireless
---

### Post by manijakkk on 2011-06-17
Hello, i need help to solve the problem with my wireless network. I have  Dell DV6 Pavilion 2115 eg laptop and i installed Ubuntu 11.4 and  internet and wireless worked, until i reboted my system it has disapear.  I cant no longer to connect to a wireless network. It dont shows me any  wireless network.
My wireless card is Atheros AR 9285 802.11b/g/n Wifi Adapter

Please help. 


PS: Sorry for my bad English.

---

### Post by blackmail on 2011-06-17
Have a look [here]("http://linuxwireless.org/en/users/Drivers/Atheros")

Hope you can find what you require, if not we will search harder :))

---

### Post by manijakkk on 2011-06-17
I am a new to ubuntu, i am using windows for whole life, how can i install this file that i am downloading

sorry for distraction

---

### Post by manijakkk on 2011-06-17
I am wondering how it worked for first time when the system was installet, after i restart my computer it stoped

---

### Post by manijakkk on 2011-06-17
lspci | grep Network

08:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

### Post by manijakkk on 2011-06-17
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   21708  1 
fat                    61374  1 vfat
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     28103  1 
binfmt_misc            17565  1 
snd_hda_codec_idt      71137  1 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
arc4                   12529  2 
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
radeon                982197  3 
ath9k                 118238  0 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
joydev                 17606  0 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
ttm                    76664  1 radeon
uvcvideo               72195  0 
mac80211              294370  1 ath9k
hp_wmi                 13706  0 
sparse_keymap          13898  1 hp_wmi
snd_timer              29602  2 snd_pcm,snd_seq
ath9k_common           13851  1 ath9k
ath9k_hw              323077  2 ath9k,ath9k_common
ath                    23773  2 ath9k,ath9k_hw
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         42136  1 radeon
ir_lirc_codec          12898  0 
lirc_dev               19232  1 ir_lirc_codec
ir_sony_decoder        12549  0 
rc_rc6_mce             12502  0 
ir_jvc_decoder         12546  0 
ir_rc6_decoder         12546  0 
ir_rc5_decoder         12546  0 
videodev               82052  1 uvcvideo
ir_nec_decoder         12546  0 
ene_ir                 22786  0 
psmouse                73535  0 
v4l2_compat_ioctl32    17078  1 videodev
hp_accel               21880  0 
lis3lv02d              19893  1 hp_accel
rc_core                26918  9 ir_lirc_codec,ir_sony_decoder,rc_rc6_mce,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,ene_ir
video                  19438  0 
input_polldev          14007  1 lis3lv02d
serio_raw              13166  0 
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   227495  5 radeon,ttm,drm_kms_helper
cfg80211              178528  3 ath9k,mac80211,ath
i2c_algo_bit           13400  1 radeon
sp5100_tco             13744  0 
edac_core              53845  0 
soundcore              12680  1 snd
edac_mce_amd           23464  0 
k10temp                13119  0 
i2c_piix4              13303  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
usb_storage            53538  1 
uas                    17996  0 
ahci                   25951  1 
r8169                  48022  0 
libahci                26642  1 ahci

---

### Post by blackmail on 2011-06-19
Since i am a noob to this whole wireless thing but i really want to help, i will try my best and also ask someone far better to take a look at this trouble...

---

### Post by blackmail on 2011-06-19
Since the last attempt did you try using the Live CD to see if it works? and also please have a look [here]("http://ubuntuforums.org/showthread.php?t=1244686")

Also do you have wireless encryption? If yes and if you turn that off from your router does the computer connect. If it does I assume that you use WPA2, try to downgrade it to WEP, i am not sure many can crack it...

Please post a reply if the guide above helped in some way, i have never faced a wireless problem so i have no previous experience with it :/

---

### Post by blackmail on 2011-06-19
Could you please post the output to this code here:

```
rfkill list all
```

---

### Post by manijakkk on 2011-06-19
when i use ubuntu from live cd just run, not install then it works no matter how muchj time i  restart my pc, when i install it it just work for once,

---

### Post by manijakkk on 2011-06-19
[FONT=monospace]0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

[/FONT]

---

### Post by blackmail on 2011-07-22
Hello, sorry for taking my time with answering back, i was a bit out of internet reach...

SO the rfkill command said that there are no blocks regarding your wireless system, so the other thing is to see if there are any other kernel error messages.
Please post the output of the command:

```
dmesg | grep -e ath -e wlan
```

this will post all kernel messages about your ath (network) and your wlan.

and also let's try to force the w-card to scan some networks in the area (do you have another phone or something to scan for the wlan networks also to compare the results if any...? it would help a bit to what's there and what does your computer see)

```
sudo iwlist wlan0 scan
```


When you have the answers I will post back what I have found.

Regards

---

