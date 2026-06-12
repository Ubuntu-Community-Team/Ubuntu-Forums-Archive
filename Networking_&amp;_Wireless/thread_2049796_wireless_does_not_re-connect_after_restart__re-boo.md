---
title: "wireless does not re-connect after restart / re-boot"
date: 2012-08-29
forum: Networking &amp; Wireless
---

### Post by semperlinux on 2012-08-29
Hardware - ACER 7740G laptop
OS - Linux 12.04.1 - precise pangolin - Kubuntu

Hi Forum,

Problem:- the wireless connection will not re-connect when I re-boot / restart the machine.

Wireless setup is configured in System Settings / Network and Connectivity / Network Settings /  Network Connections / Wireless.

I can set-up the wireless connection no problem and it runs fine until I shut down / re-start.
If the e'net cable is plugged in, the system just starts with the wired connection.
If the cable is not plugged in, no internet connection.

"Connect automatically" in the wireless set-up interface is checked.

The following is the entire content of etc/network/interfaces.........
"
auto lo
iface lo inet loopback

"
(N.B. nothing about a wireless connection.)

The following is the content of etc/Network Manager/NetworkManager.conf.........
"

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=00:26:2D:7A:4F:81,

[ifupdown]
managed=false

"

The mac address given is that for the e'net connection - the wireless card is obviously different.
Again, no info about a wireless connection.


Anyone any ideas ?

Many thanks,
Semperlinux.

---

### Post by praseodym on 2012-08-29
Hi,

please show the terminal outputs (CTRL+ALT+T) of these commands:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```
Cable connection is always preferred. What kind of computer do you use?

---

### Post by semperlinux on 2012-08-29
Thanks for the reply praseodym.

Information requested as follows.........................

jrm@acer:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
        Subsystem: Acer Incorporated [ALI] Aspire 7740G [1025:033d]
        Kernel driver in use: tg3
--
05:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
        Subsystem: Quanta Microsystems, Inc EM306 802.11bgn Wireless Half-size Mini PCIe Card [AR9283] [1a32:0306]
        Kernel driver in use: ath9k
jrm@acer:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 004: ID 04f2:b044 Chicony Electronics Co., Ltd Acer CrystalEye Webcam
jrm@acer:~$ lsmod
Module                  Size  Used by
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
binfmt_misc            17540  1 
joydev                 17693  0 
arc4                   12529  2 
acer_wmi               28418  0 
sparse_keymap          13890  1 acer_wmi
snd_hda_codec_hdmi     32474  1 
psmouse                87692  0 
serio_raw              13211  0 
snd_seq_midi           13324  0 
intel_ips              18174  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
ath9k                 132390  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event                                       
mac80211              506816  1 ath9k                                                                 
snd_hda_codec_realtek   224066  1                                                                     
v4l2_compat_ioctl32    17128  1 videodev                                                              
ath9k_common           14053  1 ath9k                                                                 
ath9k_hw              411151  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
cfg80211              205544  3 ath9k,mac80211,ath
snd_hda_intel          33773  4 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
fglrx                3263886  83 
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13253  0 
snd_timer              29990  2 snd_seq,snd_pcm
snd                    78855  18 snd_hda_codec_hdmi,snd_rawmidi,snd_seq,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_device,snd_timer
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
vesafb                 13844  1 
usbhid                 47199  0 
hid                    99559  1 usbhid
tg3                   152032  0 
video                  19596  0 
wmi                    19256  1 acer_wmi
jrm@acer:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

jrm@acer:~$ rfkill list
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
jrm@acer:~$ 


Hardware is an ACER 7740G laptop.

I have no bother configuring a working wireless connection - the problem is when I shut down and restart or re-boot - the wireless connection simply doesn't fire up again.

I'm sure I need to write it into a config file so that it will be found / read on boot up.
Which config file and what to put in it is what I'm not sure about.

---

### Post by 10ghost on 2012-08-30
I have exactly  the same problem. Initially when I restart or reboot and it does and carry out that action again and it would start working but now it doesn't anymore. I issued the command listed and it produced similar result as above. Your help would much appreciated.

---

### Post by semperlinux on 2012-09-03
Hi Forum,

Nobody got any ideas on this one ?

I found a posting from wieman01 (24/6/2006) whjch seemed to give a good wireless set-up description but it didn't work !!

Could someone / anyone with a working setup (not afflicted with this problem) please post the contents of the following files...............

etc/network/interfaces      and
etc/Network Manager/NetworkManager.conf

Many thanks

---

### Post by slow photon on 2012-11-15
I'm having the same problem. I am using a Linksys AE1000 usb wireless card with the Ralink RT3572 Linux drivers. Internet works fine, but requires the password to be manually entered after restart in the network preferences for my wireless network.

---

### Post by semperlinux on 2012-11-15
It looks like this is not a problem in general so it's time to change tack.

I also have a problem with the sound / video configuration on this machine so I'm thinking to ditch KUBUNTU and try the latest Ubuntu and see what happens.

Thanks for your input anyway.

---

