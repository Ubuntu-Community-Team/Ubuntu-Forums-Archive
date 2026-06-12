---
title: "Ubuntu 10.04 Wireless Problem"
date: 2012-04-05
forum: Networking &amp; Wireless
---

### Post by FishBowl Ninja on 2012-04-05
One problem I have been having was with my wireless internet, which by the way with my Wnidows 7 PC works just fine. So here is the problem, I will be connecte to the internet one minute, and the next minute my web browser cannot seach anything, my minecraft can no longger connect to server and so on, in other words I lost internet connection. But my wireless icon still says I am connected, so it somehow dissconected me from the internet and didnt tell me. Does anyone know a solution? Because I rather use Ubuntu 10.04 over Windows 7. Thanks in advance!

---

### Post by wildmanne39 on 2012-04-05
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by FishBowl Ninja on 2012-04-05
brenden@ubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"
Linux ubuntu 2.6.32-40-generic #87-Ubuntu SMP Tue Mar 6 00:56:56 UTC 2012 x86_64 GNU/Linux
brenden@ubuntu:~$ lspci -nnk | grep -iA2 net
04:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
	Kernel driver in use: ath9k
	Kernel modules: ath9k
05:00.0 Ethernet controller [0200]: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter [1969:1062] (rev c0)
	Kernel driver in use: atl1c
	Kernel modules: atl1c
brenden@ubuntu:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 045e:0745 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b044 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
brenden@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"BELLALIANT003"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:24:7B:F8:E5:1C   
          Bit Rate=78 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

brenden@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
brenden@ubuntu:~$ lsmod
Module                  Size  Used by
cryptd                  8116  0 
aes_x86_64              7912  2 
aes_generic            27607  1 aes_x86_64
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_realtek   279104  1 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
arc4                    1473  2 
snd_hda_intel          25805  1 
snd_hda_codec          85791  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23681  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath9k                 329085  0 
i915                  326140  3 
mac80211              238928  1 ath9k
ath                     9723  1 ath9k
snd                    71283  14 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 11104  0 
uvcvideo               62915  0 
videodev               40614  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
drm_kms_helper         30742  1 i915
cfg80211              148725  3 ath9k,mac80211,ath
psmouse                65040  0 
serio_raw               4918  0 
led_class               3764  1 ath9k
atl1c                  32975  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
intel_agp              29319  2 i915
drm                   200448  4 i915,drm_kms_helper
i2c_algo_bit            6024  1 i915
video                  20623  1 i915
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 41116  0 
hid                    83888  1 usbhid
ahci                   38350  1 
brenden@ubuntu:~$

---

### Post by wildmanne39 on 2012-04-05
Hi, try this please if it works we will need to make it permanent and do not reboot after running the commands:
```
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up
```
Thanks

---

