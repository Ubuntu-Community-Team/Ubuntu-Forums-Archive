---
title: "Broadcom BCM4312: Ubuntu 12.10 is not seeing my wifi"
date: 2013-03-23
forum: Networking &amp; Wireless
---

### Post by huntja on 2013-03-23
I got the Dell inspiron 1012 for my birthday and installed ubuntu 12.10 desktop through the usb method. once it was installed i clicked on the network icon to connect to wifi but it didnt see any wifis. I searched through the forums and found some answers but i dont know many technical terms and stuff for drivers and things. Could someone give me a very noob termed intructions for connecting to wifi? I'm such a noob at this:confused:

---

### Post by huntja on 2013-03-24
If you have questions please feel free to ask. I really need an answer

---

### Post by simon5555 on 2013-03-25
Hi,

you probably need to give a bit more details for the guys here at the forum to help you really.

As a couple of preliminary questions: 
- does the network manager say that networking and wireless are enabled? if you right-click on the icon it will show both and they should have a tick next to them
- is your wifi card switched on? you need to press 'Fn+f2' combination to switch it on

if after these check for your network and if you still cannot see your network pls post the outputs of
```

lspci
lsusb
lsmod

```

---

### Post by huntja on 2013-03-25
network manager says nothing of wireless but networking is enabled.

no response to fn+f2

as for the commands (i assume you mean terminal)
here:hunter@hunter-Inspiron-1012:~$ lspci00:00.0 Host bridge: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation NM10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
07:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
hunter@hunter-Inspiron-1012:~$ lsusb
Bus 001 Device 002: ID 064e:8101 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
hunter@hunter-Inspiron-1012:~$ lsmod
Module                  Size  Used by
joydev                 17161  0 
coretemp               13168  0 
dell_laptop            17161  0 
compal_laptop          19250  0 
dcdbas                 14054  1 dell_laptop
snd_hda_codec_realtek    63356  1 
snd_hda_intel          32515  3 
snd_hda_codec         111547  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  2 snd_hda_intel,snd_hda_codec
microcode              18209  0 
uvcvideo               71277  0 
snd_seq_midi           13132  0 
videobuf2_core         32070  1 uvcvideo
snd_rawmidi            25382  1 snd_seq_midi
videodev               95841  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12756  1 uvcvideo
videobuf2_memops       13184  1 videobuf2_vmalloc
snd_seq_midi_event     14475  1 snd_seq_midi
rfcomm                 37276  0 
parport_pc             31968  0 
bnep                   17707  2 
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
bluetooth             183228  10 rfcomm,bnep
ppdev                  12817  0 
psmouse                84843  0 
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13031  0 
lpc_ich                16925  0 
b43                   347284  0 
snd                    61991  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              461161  1 b43
cfg80211              175375  2 b43,mac80211
bcma                   34483  1 b43
soundcore              14599  1 snd
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
i915                  457161  3 
drm_kms_helper         45271  1 i915
drm                   230463  4 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
mac_hid                13037  0 
video                  18847  1 i915
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
ums_realtek            17669  0 
uas                    17556  0 
usb_storage            39350  1 ums_realtek
ssb                    50087  1 b43
r8169                  55976  0

---

### Post by simon5555 on 2013-03-25
[COLOR=#000000]you have a Broadcom Corporation BCM4312 modem and this is what you need to google for - I am not too familiar with these.  You may want to start at [/COLOR][http://ubuntuforums.org/showthread.php?t=1811184](http://ubuntuforums.org/showthread.php?t=1811184)

---

### Post by huntja on 2013-03-28
After many hours searching the internet i dcided that it would be easier if I did a fresh install. Now, it sees the driver in the additional drivers page, but when i click "use this driver" it only half loads then stops and never moves again. Any fixes to this anyone?

---

### Post by Hadaka on 2013-03-28
Hi, lets see if we can make that birthday present
work like its is suppose to for you.
please COPY and paste the following commands.

```
lspci -nn | egrep '0200|0280"
lsmod
rfkill list all
```
please post the results
thanks.

---

### Post by huntja on 2013-04-07
sorry for the delay on the response haven't had a minute to do it forever. Anyway, when i pasted the commands into the terminal nothing was displayed. i typed [COLOR=#000000][FONT=Ubuntu Mono]lspci -nn | egrep '0200|0280" and it showed a > 
same for the rest sorry if this wasnt what you were looking for.[/FONT][/COLOR]

---

### Post by huntja on 2013-06-22
After many months of searching I found these terminal commands once connected to the internet wired style entering these in the terminal gets the wifi to work!! so happy can't wait to start using linux to it's full potential.:D

sudo apt-get install linux-headers-generic 
sudo apt-get install --reinstall bcmwl-kernel-source 
sudo modprobe wl

---

