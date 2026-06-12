---
title: "Cannot connect with wireless"
date: 2013-01-07
forum: Networking &amp; Wireless
---

### Post by russellswords on 2013-01-07
Hi

I'm new to Ubuntu and have recently installed 12.10 on my old laptop. The problem I am having is that I cannot connect to a wireless as it appears that the driver is disabled although I have no problem connecting over a wired connection. The laptop does have a wireless button which now isn't working working

If anyone can help, please dumb it down a little as I'm only new to Ubuntu. :p

This is all the information I have been able to find so far:
alan@alan-LM1WN:~$ sudo lshw -C network
  *-network:0 DISABLED    
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth1
       version: 05
       serial: 00:16:6f:a1:45:29
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:b0008000-b0008fff
  *-network:1
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:06:09.0
       logical name: eth0
       version: 02
       serial: 00:40:ca:03:e0:f6
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.21 latency=32 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:18 memory:b0006000-b0007fff memory:44000000-4401ffff


alan@alan-LM1WN:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

alan@alan-LM1WN:~$ sudo lshw -C network^C
alan@alan-LM1WN:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
Linux alan-LM1WN 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686 i686 i686 GNU/Linux

alan@alan-LM1WN:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

alan@alan-LM1WN:~$ lsmod
Module                  Size  Used by
arc4                   12473  0 
rt2800usb              22285  0 
rt2800lib              57144  1 rt2800usb
crc_ccitt              12595  1 rt2800lib
rt2x00usb              19941  1 rt2800usb
rt2x00lib              48562  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              461161  3 rt2800lib,rt2x00usb,rt2x00lib
isofs                  39210  1 
bnep                   17707  2 
rfcomm                 37276  0 
bluetooth             183228  8 bnep,rfcomm
parport_pc             31968  0 
ppdev                  12817  0 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek    63356  1 
snd_hda_intel          32515  3 
snd_hda_codec         111547  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ipw2200               140513  0 
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
joydev                 17161  0 
i915                  457161  3 
libipw                 46357  1 ipw2200
tifm_7xx1              12898  0 
snd_timer              24411  2 snd_pcm,snd_seq
pcmcia                 39509  0 
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
tifm_core              15068  1 tifm_7xx1
drm_kms_helper         45271  1 i915
cfg80211              175375  4 rt2x00lib,mac80211,ipw2200,libipw
yenta_socket           27095  0 
drm                   230463  4 i915,drm_kms_helper
pcmcia_rsrc            18191  1 yenta_socket
lib80211               14040  2 ipw2200,libipw
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
lpc_ich                16925  0 
snd                    61991  16 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14599  1 snd
psmouse                84843  0 
microcode              18209  0 
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
serio_raw              13031  0 
i2c_algo_bit           13197  1 i915
mac_hid                13037  0 
video                  18847  1 i915
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
firewire_ohci          35521  0 
sdhci_pci              18155  0 
sdhci                  27830  1 sdhci_pci
b44                    31326  0 
ssb                    50087  1 b44
firewire_core          57492  1 firewire_ohci
crc_itu_t              12627  1 firewire_core


If anyone can help, please dumb it down a little as I'm only new to Ubuntu. :razz:
Hope thats enough info. 
Thanks in advance.

---

### Post by russellswords on 2013-01-08
Does anyone have any idea? Would hopefully like to get this working before before my college exams. :confused:

---

### Post by steeldriver on 2013-01-08
Not an expert but I don't see anything particularly wrong with your lshw driver / firmware status - the problem seems to be the hard block:

> **russellswords said:**
> 
```
alan@alan-LM1WN:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
[COLOR=Red]    Hard blocked: yes[/COLOR]

```

You can try

```
sudo rfkill unblock 0
```however if it's a true hard block (i.e. a hardware button) you may need to get that working properly - try searching for info based on the particular laptop manufacturer / model

---

### Post by russellswords on 2013-01-08
Thanks for the reply.

Dont seem to get any response when I type: alan@alan-LM1WN:~$ sudo rfkill unblock 0 

I did manage to find the help file and I am assuming that the identifier is 0?

Commands:
    help
    event
    list [IDENTIFIER]
    block IDENTIFIER
    unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
    <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm

---

### Post by MSPdwalt on 2013-01-08
I had a similar problem with an old Dell latitude.  Sometimes Linux doesn't play nice with wireless switches.  Update to the latest BIOS (might have to make a freeDOS flash drive).  Go into the BIOS, disable the wireless card & Bluetooth, boot up, shutdown, go into BIOS, re-enable, boot up, ????? profit.

---

### Post by amahi on 2013-01-08
Hi 

> 

alan@alan-LM1WN:~$ sudo lshw -C network
*-network:0 [COLOR="Red"]DISABLED [/COLOR]
description: Wireless interface
product: PRO/Wireless 2200BG [Calexico2] Network Connection
vendor: Intel Corporation
physical id: 1
bus info: pci@0000:06:01.0
logical name: eth1
version: 05
serial: 00:16:6f:a1:45:29
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical wireless



1-
```
sudo gedit  /etc/NetworkManager/NetworkManager.conf 
```

at the last line changes false to [COLOR="Green"]true[/COLOR].

2-let's lock the NetworkManager.conf

```
chattr +i /etc/NetworkManager/NetworkManager.conf
```


(  to go back to normal Status use -i option:
[COLOR="SeaGreen"]chattr -i /etc/NetworkManager/NetworkManager.conf[/COLOR]
 )

3-
```
sudo /etc/init.d/network-manager  restart 
```

---

### Post by poltr1 on 2013-10-12
Amati: Thank you.  I just installed Xubuntu 12.04 on a Dell Latitude D500 which had the Intel Calexico2 wireless card, and these instructions worked flawlessly.

---

