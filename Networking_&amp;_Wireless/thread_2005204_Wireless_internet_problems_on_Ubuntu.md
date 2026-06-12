---
title: "Wireless internet problems on Ubuntu"
date: 2012-06-17
forum: Networking &amp; Wireless
---

### Post by chippy_250 on 2012-06-17
I have the latest version of Ubuntu and I am connected via a wireless router. I never have trouble connecting to my network on any other device or when I was using Windows. But when I'm using the Internet on Ubuntu; downloads and web pages freeze. It says cannot find server error, even though my connection is fine. This has been going on for about a week now. What could be wrong?

---

### Post by wildmanne39 on 2012-06-17
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by chippy_250 on 2012-06-18
> **wildmanne39 said:**
> Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```by clicking on new reply and click # then paste the information between the brackets.
Thank you

Ok but is this safe? 
I'm fairly new to Linux and I don't know what I'm doing (Don't want to give out my PC's  connection/password details out etc)

---

### Post by wildmanne39 on 2012-06-18
Hi, yes it is safe, you can look at all the info before you post it and if you do not want to post it you do not have to but I am not good enough to be able to help without the information.
Thanks

---

### Post by chippy_250 on 2012-06-18
james@james-desktop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux james-desktop 3.2.0-25-generic #40-Ubuntu SMP Wed May 23 20:33:05 UTC 2012 i686 athlon i386 GNU/Linux
james@james-desktop:~$ lspci -nnk | grep -iA2 net
00:0a.0 Bridge [0680]: NVIDIA Corporation CK804 Ethernet Controller [10de:0057] (rev a3)
    Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard [1458:e000]
    Kernel driver in use: forcedeth
james@james-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 050d:815c Belkin Components F5D8053 N Wireless USB Adapter v3000 [Ralink RT2870]
Bus 002 Device 002: ID 062a:0102 Creative Labs Wireless Keyboard/Mouse Combo [MK1152WC]
james@james-desktop:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"HomeNetwork"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:DF:ED:60:93   
          Bit Rate=65 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1114  Invalid misc:60   Missed beacon:0

eth0      no wireless extensions.

james@james-desktop:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
james@james-desktop:~$ lsmod
Module                  Size  Used by
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
arc4                   12473  2 
binfmt_misc            17292  1 
radeon                729591  3 
rt2800usb              22300  0 
rt2800lib              53264  1 rt2800usb
crc_ccitt              12595  1 rt2800lib
rt2x00usb              20061  1 rt2800usb
snd_intel8x0           33455  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
rt2x00lib              48858  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              436455  3 rt2800lib,rt2x00usb,rt2x00lib
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
drm                   197692  5 radeon,ttm,drm_kms_helper
cfg80211              178679  2 rt2x00lib,mac80211
serio_raw              13027  0 
snd_seq_midi           13132  0 
i2c_algo_bit           13199  1 radeon
k8temp                 12905  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17393  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13077  0 
parport_pc             32114  1 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
firewire_ohci          40180  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
forcedeth              58096  0 
sata_nv                23360  0 
pata_amd               13750  2 
floppy                 60310  0 
james@james-desktop:~$

---

### Post by wildmanne39 on 2012-06-18
Hi, please copy and paste the following:
```
gksudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default powermanagement behavior) and enter the following: 
```
#!/bin/sh

/sbin/iwconfig wlan0 power off
```

above exit0, then save gedit and close.
Then:
```
gksudo gedit /etc/modprobe.d/rt2800usb.conf
```

Add one line:

```
options rt2800usb nohwcrypt=1
```

Proofread carefully, save and close gedit. Reboot.
Thanks

---

### Post by chippy_250 on 2012-06-19
> **wildmanne39 said:**
> Hi, please copy and paste the following:
```
gksudo gedit /etc/pm/power.d/wireless
```(this will create or edit a configuration file that will override the default powermanagement behavior) and enter the following: 
```
#!/bin/sh

/sbin/iwconfig wlan0 power off
```above exit0, then save gedit and close.
Then:
```
gksudo gedit /etc/modprobe.d/rt2800usb.conf
```Add one line:

```
options rt2800usb nohwcrypt=1
```Proofread carefully, save and close gedit. Reboot.
Thanks

OK so i've done what you said. It seems to be working better now (touch wood). Can I just ask what I've amended exactly here though?

---

### Post by wildmanne39 on 2012-06-19
Hi, we turned power management off on your wireless because it does not work very well in cases and we changed encryption from hardware to software and you do not need to worry it is all safe.

Please use thread tools at the top of the page to mark the thread solved.
Thanks

---

