---
title: "very slow wireless on ubuntu 11.10"
date: 2011-12-21
forum: Networking &amp; Wireless
---

### Post by tubbzor on 2011-12-21
I recently installed updates and the internet became very very slow now..timing out of pages most of the time.  I have tried some other things people posted and it hasn't worked for me. please help!

---

### Post by wildmanne39 on 2011-12-21
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by tubbzor on 2011-12-21
```
cat: /ect/lsb-release: No such file or directory
Linux tubbzor 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: AzureWave Device [1a3b:1089]
	Kernel driver in use: ath9k
--
04:00.0 Ethernet controller [0200]: Atheros Communications AR8131 Gigabit Ethernet [1969:1063] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1820]
	Kernel driver in use: atl1c
caleb@tubbzor:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Tebbe"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:18:F8:49:12:40   
          Bit Rate=135 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:71   Missed beacon:0


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

Module                  Size  Used by
nls_iso8859_1          12713  2 
nls_cp437              16991  2 
vfat                   17585  2 
fat                    61475  1 vfat
bnep                   18436  2 
rfcomm                 47946  8 
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
snd_hda_codec_hdmi     32040  1 
ses                    17417  0 
enclosure              15269  1 ses
snd_hda_codec_realtek   330769  1 
arc4                   12529  2 
psmouse                73882  0 
serio_raw              13166  0 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
i7core_edac            27942  0 
edac_core              53746  3 i7core_edac
btusb                  18600  2 
bluetooth             166112  23 bnep,rfcomm,btusb
snd_hda_intel          33390  3 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k                 127538  0 
mac80211              462092  1 ath9k
snd_timer              29991  2 snd_seq,snd_pcm
video                  19412  0 
ath9k_common           13839  1 ath9k
asus_laptop            19722  0 
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_rawmidi,snd_seq,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_device,snd_timer
radeon               1016226  3 
sparse_keymap          13890  1 asus_laptop
ath9k_hw              312914  2 ath9k,ath9k_common
ath                    24067  2 ath9k,ath9k_hw
cfg80211              199587  3 ath9k,mac80211,ath
ttm                    76805  1 radeon
drm_kms_helper         42558  1 radeon
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm                   236290  5 radeon,ttm,drm_kms_helper
mei                    41480  0 
i2c_algo_bit           13423  1 radeon
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            57901  2 
uas                    18027  0 
usbhid                 47198  0 
hid                    95463  1 usbhid
atl1c                  41643  0 

```

thank you

---

### Post by wildmanne39 on 2011-12-21
Hi, please try this and if it works we will need to make it permanent, run then commands one line at a time and do not restart your computer after you run the commands.
```
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up

```
Thanks

---

### Post by tubbzor on 2011-12-21
yes! these worked wonderfully! how to make them permanent?

thank you!

---

### Post by wildmanne39 on 2011-12-21
Hi, your welcome! please do this:
```
gksudo gedit /etc/modprobe.d/ath9k.conf
```
Add a single line:
```
options ath9k nohwcrypt=1
```
Proofread carefully, save and close gedit. Reboot, would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

---

### Post by tubbzor on 2011-12-21
when I ran that command and typed that into gedit and tried to save gedit gives me an error saying "could not find the file /ect/modprobe.d/ath9k.conf." and will not let me save it!

---

### Post by wildmanne39 on 2011-12-22
Hi, just copy and paste all commands and see if that helps.
Thanks

---

### Post by tubbzor on 2011-12-22
yes copy-pasting worked! thank you much again

---

### Post by wildmanne39 on 2011-12-22
Hi, your welcome!
Enjoy

---

