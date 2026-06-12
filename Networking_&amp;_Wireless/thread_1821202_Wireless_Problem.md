---
title: "Wireless Problem"
date: 2011-08-08
forum: Networking &amp; Wireless
---

### Post by stevenoctopus on 2011-08-08
Hello, I am new to ubuntu and I just recently installed it. The first impression was great and I love everything except I have one major problem that is going to cause me to switch back to windows. My wireless network shows connected and works fine for a while but periodically stops working. It always says it is connected but sometimes stops working to where I have to disconnect and reconnect for it to start back up again. If anybody can help me out, it would be greatly appreciated. Thanks.

---

### Post by wildmanne39 on 2011-08-08
Hi, run these commands in a terminal please:
```
sudo lshw -C network
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
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by stevenoctopus on 2011-08-08
sudo lshw -C network

```
  *-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 78:e4:00:bf:78:71
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.1.107 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:16 memory:fbef0000-fbefffff
  *-network
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 01
       serial: b8:ac:6f:a4:e2:91
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=half firmware=sb v2.05 latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:30 memory:fbff0000-fbffffff

```lspci -nn | grep 0280

```
04:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)

```iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Steel Curtain"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:23:69:6A:13:F0   
          Bit Rate=104 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```rfkill list all

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```lsmod

```
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
hdpvr                  25411  0 
v4l2_common             9566  1 hdpvr
videodev               98796  2 hdpvr,v4l2_common
media                  13760  1 videodev
arc4                    1473  2 
snd_hda_codec_intelhdmi    13090  1 
snd_hda_codec_realtek   279008  1 
snd_hda_intel          25805  2 
snd_hda_codec          85759  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
v4l2_compat_ioctl32     8807  1 videodev
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
ath9k                 329085  0 
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
mac80211              238896  1 ath9k
ath                     9723  1 ath9k
snd_timer              23649  2 snd_pcm,snd_seq
cfg80211              148341  3 ath9k,mac80211,ath
dell_wmi                2177  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
joydev                 11104  0 
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
led_class               3764  1 ath9k
snd                    71283  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                65040  0 
dcdbas                  6886  0 
nvidia              10832442  38 
serio_raw               4918  0 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
intel_agp              29319  0 
lp                      9336  0 
parport                37160  2 ppdev,lp
usb_storage            50377  0 
usbhid                 41116  0 
hid                    83888  1 usbhid
ohci1394               30260  0 
ahci                   38030  2 
tg3                   122382  0 
ieee1394               94771  1 ohci1394

```

---

### Post by wildmanne39 on 2011-08-08
Hi, try this please:
```
sudo rmmod -f dell-laptop
```
do not restart your computer after you run this command,it is a one time command,if it works we will blacklist it to make it persistent.

Please disconnect your wired connection before you run the command. 
Thank you

---

### Post by stevenoctopus on 2011-08-08
I received the following error after that:

ERROR: Removing 'dell_laptop': No such file or directory

---

### Post by wildmanne39 on 2011-08-08
Hi, Is your network set to WPA and WPA2 mixed mode? That often causes problems. If you can, try WPA2 only. You might also try:
```
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
```
again disconnect your wired connection first.
Thank you

---

### Post by stevenoctopus on 2011-08-08
I have no security on my wireless but I tried those and the internet connects fine. I will report back tomorrow or later tonight to say if I am still experiencing disconnecting problems. Thanks for the help thus far though.

---

### Post by wildmanne39 on 2011-08-08
Hi, your welcome! if you is stays working, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by wildmanne39 on 2011-08-08
Hi, To make the driver option persistent, you need to do:
```
sudo gedit /etc/modprobe.d/ath9k.conf
```
Add this line:
```
options ath9k nohwcrypt=1
```
save and close gedit.
Thank you

---

### Post by stevenoctopus on 2011-08-09
This didn't seem to work. I disconnected after about 6-10 hours.

---

### Post by wildmanne39 on 2011-08-09
Hi, when you got disconnected was it after you restarted your computer?

Did you do the procedure to make it stay persistent?
Thank you

---

### Post by stevenoctopus on 2011-08-10
I never restarted my computer or made the changes persistent. I figured I didn't need to make them persistent yet as I didn't restart.

---

