---
title: "New to Ubuntu - Wired Connection working, Wireless doesn't!"
date: 2012-06-25
forum: Networking &amp; Wireless
---

### Post by Shrunk on 2012-06-25
Hi! I recently had a pretty long fight with a virus in windows and I got really sick of it! So with some help of my older brother I wiped windows from my Laptop (Asus K53SV) and installed Ubuntu.

Currently, my wired connection is working, but wireless is not.  "lspci -v" shows me that I have an Intel Centrino Wireless-N 100 card.

If it helps sold my problem easier: I am able to detect networks and connect to them, but I am unable to access the internet at all. Any suggestions?

---

### Post by wildmanne39 on 2012-06-25
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by Shrunk on 2012-06-25
Thank you for attempting to help me! I feel welcome already :p

```
jm@jm-K53SV:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux jm-K53SV 3.2.0-25-generic-pae #40-Ubuntu SMP Wed May 23 22:11:24 UTC 2012 i686 i686 i386 GNU/Linux
jm@jm-K53SV:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 100 [8086:08ae]
    Subsystem: Intel Corporation Centrino Wireless-N 100 BGN [8086:1005]
    Kernel driver in use: iwlwifi
--
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1277]
    Kernel driver in use: r8169
jm@jm-K53SV:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Mayhew"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:25:9C:13:24:AA   
          Bit Rate=1 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:17  Invalid misc:736   Missed beacon:0

eth0      no wireless extensions.

jm@jm-K53SV:~$ rfkill list all
0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
jm@jm-K53SV:~$ lsmod
Module                  Size  Used by
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_realtek   174055  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
nvidia              10962290  0 
rts5139               279622  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
arc4                   12473  2 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
iwlwifi               292030  0 
snd                    62064  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              436455  1 iwlwifi
soundcore              14635  1 snd
uvcvideo               67203  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
videodev               86588  1 uvcvideo
cfg80211              178679  2 iwlwifi,mac80211
joydev                 17393  0 
i915                  414663  2 
drm_kms_helper         45466  1 i915
drm                   197692  3 i915,drm_kms_helper
mei                    36570  0 
mxm_wmi                12859  0 
asus_nb_wmi            12622  0 
asus_wmi               19624  1 asus_nb_wmi
i2c_algo_bit           13199  1 i915
sparse_keymap          13658  1 asus_wmi
psmouse                72919  0 
serio_raw              13027  0 
wmi                    18744  2 mxm_wmi,asus_wmi
video                  19068  1 i915
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56321  0 

```

---

### Post by wildmanne39 on 2012-06-25
Hi, please do:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi

```
does that help? if not post the output of:
```
nm-tool
dmesg | egrep 'iwl|wlan'
```
Thanks

---

### Post by Shrunk on 2012-06-25
It worked!!!! \\:D/

Thanks a bundle!! Major kudos to you!!!

---

### Post by wildmanne39 on 2012-06-25
Hi, your welcome! please use thread tools at the top of the page to mark the thread solved.
Thanks

---

