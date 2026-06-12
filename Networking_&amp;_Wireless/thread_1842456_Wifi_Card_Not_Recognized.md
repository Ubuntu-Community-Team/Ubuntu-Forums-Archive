---
title: "Wifi Card Not Recognized"
date: 2011-09-11
forum: Networking &amp; Wireless
---

### Post by LiteDrive on 2011-09-11
My wifi card drivers aren't recognized by my Ubuntu Server system. Is there anything specific I can do to configure them? The lspci | grep Network command brings up absolutely nothing.

I've looked at some of the documentation, and it hasn't been able to help me because a few of the commands don't display the information their supposed to. Iwconfig, for example, hasn't helped much either.

Thanks in advance to those who can help.

---

### Post by wildmanne39 on 2011-09-11
Hi, run these commands please and post the results here:
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
lsusb
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
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by LiteDrive on 2011-09-11
```
DISTRIB_ID = ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
```

```
Bus 001 Device 004 ID 050d:905b Belkin Components F5D9050 Wireless G+ MIMO Network Adapter v3000 [Ralink RT2573] 
```

```

lo no wireless extensions.
eth0 no wireless extensions.
wlan0 IEE 802.11bg ESSID:off/any
Mode:Managed Access Point:Not-Assocated tx-power=0 dBm
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:on

```

```

0:phy0: Wireless LAN
Soft blocked:no
Hard blocked:no

```

```

Module          Size     Used by
sha25_generic   20911     2
cryptd          19801     0
aes_i586        16956     8
aes_generic     38023     1 aes_i586
dm_crypt        22463     1
arc4            12473     3
rt73usb         26854     0
crc_itu_t       12627     1 rt73usb
rt20x00usb      19693     1 rt73usb
rt2x00lib       39075     2 rt73usb, rt2x00usb
snd_wavefront   34696     0
snd_intel18x0   33213     0
mac80211        257001    2 rt2x00usbm rt2x00lib
snd_cs4236      29291     0
snd_wss_lib     30006     2 snd_wavefront, snd_cs4236
ac97_bus        12642     1 sndP_ac97_codec
snd_op13_lib    18760     2 snd_wavefront,snd_c4236
snd_hwdep       13274     2 sdn_wavefront, snd_op13_lib
ppdev           12849     0
snd_pcm         80244     4 snd_intel18x0, snd_cs4236, snd_wss_lib, snd_ac97_codec
ac97_bus        12642     1 snd_ac97_codec

```

I have to copy all of this by hand, so let me know if you need any more info. Thanks much for your help - I really appreciate it. Also, if there's a way you can post results to a text file via command line and save it to a usb flash drive, please let me know.

---

### Post by praseodym on 2011-09-11
Try to shut off the power management:

```
sudo iwconfig wlan0 power off
sudo rfkill unblock all
sudo service network-manager restart
```

> tx-power=0 dBm
shows that there is some button/switch/etc. The card is "off".

You may reset your BIOS to manufacturer default settings and/or check if wireless can be enabled there.

---

### Post by wildmanne39 on 2011-09-11
Hi, did you manually edit your driver for this card?

Please post the results of these commands here:
```
sudo lshw -C network
```
```
nm-tool
```
```
sudo iwlist scan
```
```
dmesg | egrep 'rt7|firm'
```
Thank you

---

