---
title: "No Wired Network Connection - Ubuntu 10.04 Atheros AR8131"
date: 2012-04-25
forum: Networking &amp; Wireless
---

### Post by cpk011 on 2012-04-25
Hi.

I cannot get the wired network connection on my LG R570 laptop running Ubuntu 10.04. 
Here is the information on my system:

peter@peter-ubuntu:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"

peter@peter-ubuntu:~$ uname -a
Linux peter-ubuntu 2.6.32-40-generic #87-Ubuntu SMP Tue Mar 6 00:56:56 UTC 2012 x86_64 GNU/Linux

peter@peter-ubuntu:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Intel Corporation WiFi Link 6000 Series [8086:422c] (rev 35)
Kernel driver in use: iwlagn
Kernel modules: iwlagn
03:00.0 Ethernet controller [0200]: Atheros Communications AR8131 Gigabit Ethernet [1969:1063] (rev c0)
Kernel driver in use: atheros_eth
Kernel modules: atl1c, atl1e

peter@peter-ubuntu:~$ lsusb
Bus 002 Device 004: ID 0bda:0159 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 002: ID 8087:0020 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 18e8:6252 Qcom 
Bus 001 Device 002: ID 8087:0020 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

peter@peter-ubuntu:~$ iwconfig
lo no wireless extensions.
wlan0 IEEE 802.11abgn ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F |\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A" 
Mode:Managed Frequency:2.462 GHz Access Point: Not-Associated 
Tx-Power=15 dBm 
Retry long limit:7 RTS thr: off Fragment thr: off
Power Management: off

eth0 no wireless extensions.
pan0 no wireless extensions.

peter@peter-ubuntu:~$ rfkill list all
0: hci0: Bluetooth
Soft blocked: no
Hard blocked: no
1: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no

peter@peter-ubuntu:~$ lsmod
Module Size Used by
fbcon 39270 71 
tileblit 2487 1 fbcon
font 8053 1 fbcon
bitblit 5811 1 fbcon
softcursor 1565 1 bitblit
vga16fb 12757 0 
vgastate 9857 1 vga16fb
binfmt_misc 7960 1 
ppdev 6375 0 
joydev 11104 0 
rfcomm 40425 4 
sco 9649 2 
bridge 53248 0 
stp 2171 1 bridge
bnep 11916 2 
l2cap 34839 16 rfcomm,bnep
snd_hda_codec_realtek 279104 1 
atl1c 32975 0 
snd_hda_intel 25805 2 
snd_hda_codec 85791 2 snd_hda_codec_realtek,snd_hda_intel
snd_pcm_oss 41394 0 
snd_hwdep 6924 1 snd_hda_codec
snd_mixer_oss 16299 1 snd_pcm_oss
snd_pcm 87946 3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy 1782 0 
snd_seq_oss 31191 0 
snd_seq_midi 5829 0 
arc4 1473 2 
snd_rawmidi 23420 1 snd_seq_midi
snd_seq_midi_event 7267 2 snd_seq_oss,snd_seq_midi
nouveau 515227 2 
snd_seq 57481 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid i_event
iwlagn 123060 0 
ttm 61039 1 nouveau
iwlcore 125250 1 iwlagn
snd_timer 23681 2 snd_pcm,snd_seq
snd_seq_device 6888 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi ,snd_seq
psmouse 65040 0 
drm_kms_helper 30742 1 nouveau
atl1e 69878 0 
btusb 13097 2 
mac80211 238928 2 iwlagn,iwlcore
led_class 3764 1 iwlcore
snd 71283 16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec, snd_pcm_oss,snd_hwdep,snd_mixer_oss,snd_pcm,snd_se q_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bluetooth 58717 9 rfcomm,sco,bnep,l2cap,btusb
serio_raw 4918 0 
drm 200448 4 nouveau,ttm,drm_kms_helper
video 20623 0 
i2c_algo_bit 6024 1 nouveau
output 2503 1 video
cfg80211 148725 3 iwlagn,iwlcore,mac80211
intel_agp 29319 0 
soundcore 8052 1 snd
snd_page_alloc 8500 2 snd_hda_intel,snd_pcm
lp 9336 0 
parport 37160 2 ppdev,lp
usbhid 41116 0 
hid 83888 1 usbhid
usb_storage 50633 1 

Thanks.

---

### Post by cpk011 on 2012-04-26
I reinstalled Ubuntu 10.04 and now have the wired connection back.

---

### Post by cpk011 on 2012-04-26
I installed Ubuntu 10.04 and the wired network worked fine. Like you, I I updated the system using Update Manager and then I had no more wired connection. So watch out when you are using Update Manager.

---

### Post by cpk011 on 2012-05-02
I found that my problem with wired network connection was due to the faulty network cable.

---

