---
title: "Atheros AR928x &amp; Ubuntu 11.04"
date: 2011-08-01
forum: Networking &amp; Wireless
---

### Post by Bl00dyMurd3r on 2011-08-01
Before anyone tells me to search, i have spent days on this problem..

----------------------------

So i have a Gateway NV5214u laptop (64bit AMD), and it's got an Atheros AR928x wireless card

Basically this particular wireless card refuses to work for me on ubuntu (It will show available access points but it will never let me connect to them)

I have seen a bunch of tutorials from searching google on how to make it work but they're all non working methods that make absolutely no sense 

Also, I have tried ndiswrapper with a Win xp driver, all that happened was my wireless was completely disabled (Ubuntu stopped listing networks)

I even tried some terminal thing that involved a get:// address but it went no where.
-----------------------------------

[B]Someone please tell me the exact steps on how to get this card working on ubuntu 11.04
[/B]

thanks!


EDIT: if needed, ill run the lshw -C network command and post the results

oh yeah and my network is running on 802.11n with WPA2-AES encryption if that matters

---

### Post by wildmanne39 on 2011-08-01
Hi, please run these commands 
```
sudo lshw -C network
```
```
lsmod
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.

Also I believe you need WPA2 without the AES. 
Thank you

---

### Post by Bl00dyMurd3r on 2011-08-01
Thanks for the help, here's what the terminal returned:

Also, i the wireless security on my router from WPA2 AES to WPA2 TKIP or AES, and ubuntu still won't connect

```
sudo lshw -C network:
-----------------------------

 *-network               
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: 00:1f:16:b3:74:68
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=sb v2.19 latency=0 link=no multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:f0300000-f030ffff
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlan0
       version: 01
       serial: 00:22:5f:d3:43:c4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f0400000-f040ffff

``````
lsmod:
----------------------------

Module                  Size  Used by
usbhid                 46956  0 
hid                    91020  1 usbhid
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_conexant    57511  1 
arc4                   12529  2 
snd_hda_intel          33211  2 
radeon                982197  3 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
ath9k                 118238  0 
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ttm                    76664  1 radeon
mac80211              294370  1 ath9k
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
drm_kms_helper         42136  1 radeon
snd_seq_midi_event     14899  1 snd_seq_midi
joydev                 17606  0 
drm                   227495  5 radeon,ttm,drm_kms_helper
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
ath9k_common           13851  1 ath9k
snd_timer              29602  2 snd_pcm,snd_seq
ath9k_hw              323077  2 ath9k,ath9k_common
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72195  0 
i2c_algo_bit           13400  1 radeon
ath                    23773  2 ath9k,ath9k_hw
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               82052  1 uvcvideo
psmouse                73535  0 
soundcore              12680  1 snd
sp5100_tco             13744  0 
v4l2_compat_ioctl32    17078  1 videodev
acer_wmi               23771  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17825  0 
i2c_piix4              13303  0 
cfg80211              178528  3 ath9k,mac80211,ath
serio_raw              13166  0 
shpchp                 37297  0 
k10temp                13119  0 
sparse_keymap          13898  1 acer_wmi
parport                46458  3 parport_pc,ppdev,lp
video                  19438  0 
tg3                   141750  0 
ahci                   25951  1 
libahci                26642  1 ahci

``````
lspci -nn | grep 0280
--------------------------

09:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)

``````
iwconfig:
--------------------------

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Comcast"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

``````
rfkill list all:
----------------------

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-threeg: Wireless WAN
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by wildmanne39 on 2011-08-01
Hi, you need to unplug your wired connection then run this command and see if you can connect, if you can we will need to write a config file to make it permanent.  
```
sudo rmmod -f acer-wmi
```
Thank you

---

### Post by Bl00dyMurd3r on 2011-08-01
Ran that and rebooted and unfortunately it didnt work. The wireless indicater at the top of the sreen still stays animated and spends a few minutes trying to establish a connection to my wifi.

Please tell me you have more ideas :cool:

---

### Post by wildmanne39 on 2011-08-01
Hi, disable wireless security for a few minutes and see if you can connect then.
Thank you

---

### Post by nm_geo on 2011-08-01
Okay

```
sudo rmmod -f acer-wmi
```

Is a temporary command do not reboot after running it. instead 
Give us again..

```
rfkill list all
```

```
sudo lshw -C network
```

Wildmanne is looking for a change.. After the temporary command..

---

### Post by Bl00dyMurd3r on 2011-08-01
> **wildmanne39 said:**
> Hi, disable wireless security for a few minutes and see if you can connect then.
Thank you

That didnt work, however i switched my network to wireless G and i was able to connect, even with security on. Is there a way to use 802.11n on ubuntu?

---

### Post by wildmanne39 on 2011-08-01
Hi, with some cards and drivers yes with others no. I will do some research and see if I can find a way.

---

### Post by Bl00dyMurd3r on 2011-08-01
> **wildmanne39 said:**
> Hi, with some cards and drivers yes with others no. I will do some research and see if I can find a way.

Thanks a lot! I really appreciate your help :)

---

### Post by wildmanne39 on 2011-08-01
Hi, I found this link that talks about n speed for your card.
[http://forum.notebookreview.com/networking-wireless/486988-atheros-ar9285-n-mode.html](http://forum.notebookreview.com/networking-wireless/486988-atheros-ar9285-n-mode.html)

Also you may need to update your driver to get n speed,would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

