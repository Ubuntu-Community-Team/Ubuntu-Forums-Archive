---
title: "Belkin Wireless G Desktop Card, worked... then didn't."
date: 2011-07-25
forum: Networking &amp; Wireless
---

### Post by boreen on 2011-07-25
Hi there,

I installed a wireless card: Belkin G Version 7021 into my computer. It didn't work immediately, but upon rebooting the system it showed up and ran great.

Unfortunately, now the network shows up, but I can't connect my computer to it. I don't understand why it won't work when it did before.

I can see the linksys network on the wireless area, but when I click on it, it just tries to connect to it eventually saying disconnected.

I did download the NAVIDA driver for my graphic card when it was running and it brought me through to the "new" looking GUI. Would that have reset something? can going back to the old interface be a way of solving this? I kind of like the old one more.

Any insight would be great... and a fix would be amazing.

---

### Post by wildmanne39 on 2011-07-25
Hi, run these commands in a terminal please.
```
lsmod
```
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
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by boreen on 2011-07-26
```
jon@jon-MS-7599:~$ lsmod
Module                  Size  Used by
vesafb                 13449  1 
parport_pc             32111  0 
ppdev                  12849  0 
binfmt_misc            13213  1 
snd_hda_codec_hdmi     27535  4 
nvidia               9766978  38 
arc4                   12473  2 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
rtl8180                35687  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
mac80211              257001  1 rtl8180
snd_timer              28659  2 snd_pcm,snd_seq
eeprom_93cx6           12653  1 rtl8180
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              156212  2 rtl8180,mac80211
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
k10temp                12951  0 
serio_raw              12990  0 
lp                     13349  0 
sp5100_tco             13456  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
parport                36746  3 parport_pc,ppdev,lp
i2c_piix4              13095  0 
ati_agp                13202  0 
usbhid                 41704  0 
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
hid                    77084  1 usbhid
r8169                  42534  0 
pata_jmicron           12651  0 
crc_itu_t              12627  1 firewire_core
pata_atiixp            12968  0 
ahci                   21591  2 
xhci_hcd               68062  0 
libahci                25548  1 ahci
jon@jon-MS-7599:~$ sudo -nn | grep -0280
Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.
usage: sudo -h | -K | -k | -L | -V
usage: sudo -v [-AknS] [-g groupname|#gid] [-p prompt] [-u user name|#uid]
usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U user name] [-u user name|#uid] [-g groupname|#gid]
            [command]
usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u user name|#uid] [-g groupname|#gid] [VAR=value]
            [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u user name|#uid] file ...
jon@jon-MS-7599:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
jon@jon-MS-7599:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```


Thanks for your help with this issue. I was resetting and loggin in and out last night and it worked once... but same deal this morning when I logged in. Wireless is visible, but cannot connect.

---

### Post by wildmanne39 on 2011-07-26
Hi, can you run this command again please it did not work the first time.
```
lspci -nn | grep 0280
```
Thank you

---

### Post by boreen on 2011-07-26
Typing that command does nothing... it just comes back with another command prompt.

---

### Post by westie457 on 2011-07-26
> **boreen said:**
> Typing that command does nothing... it just comes back with another command prompt.

Try running 'wildmanne39's command again without the ' | grep 0280' 

The reason it did not run properly was because of a typo. And the reason it went straight to the command prompt is you do not have the required info (read: driver) installed.

---

### Post by boreen on 2011-07-26
```
jon@jon-MS-7599:~$ lspci -nn |
> lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RX780/RX790 Chipset Host Bridge [1002:5957]
00:02.0 PCI bridge [0604]: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A) [1002:5978]
00:0a.0 PCI bridge [0604]: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F) [1002:597f]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] [1002:4390] (rev 40)
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 42)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c] (rev 40)
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
00:15.0 PCI bridge [0604]: ATI Technologies Inc Device [1002:43a0]
00:15.1 PCI bridge [0604]: ATI Technologies Inc Device [1002:43a1]
00:16.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:16.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
01:00.0 VGA compatible controller [0300]: nVidia Corporation GF108 [GeForce GT 430] [10de:0de1] (rev a1)
01:00.1 Audio device [0403]: nVidia Corporation GF108 High Definition Audio Controller [10de:0bea] (rev a1)
02:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 03)
03:06.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW322/323 [11c1:5811] (rev 61)
03:07.0 Ethernet controller [0200]: Belkin F5D7000 v7000 Wireless G Desktop Card [Realtek RTL8185] [1799:700f] (rev 20)
04:00.0 IDE interface [0101]: JMicron Technology Corp. JMB368 IDE controller [197b:2368]
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
jon@jon-MS-7599:~$ 

```

---

### Post by wildmanne39 on 2011-07-26
Hi, try these commands and see if it comes on.
```
rfkill unblock wifi
```
```
sudo ifconfig wlan0 down
```
```
sudo ifconfig wlan0 up
```

---

### Post by boreen on 2011-07-26
Thanks for the advice.

Just another question about this stuff as I'm new to Ubuntu. Would I just  fire these into the command prompt? Then see what happens? Would it save it automatically or would I have to do it everytime I login?

Thanks again!

-Jon

---

### Post by wildmanne39 on 2011-07-26
Hi, yes just paste them into a terminal and see if it works if not post the output here.

Hopefully if it turns on then the next time you boot it will stay on.

---

### Post by nm_geo on 2011-07-26
Wireless has a driver installed and modinfo checks out.

~$ modinfo rtl8180
filename:       /lib/modules/2.6.32-32-generic/kernel/drivers/net/wireless/rtl818x/rtl8180.ko
license:        GPL
description:    RTL8180 / RTL8185 PCI wireless driver
author:         Andrea Merello <andreamrl@tiscali.it>
author:         Michael Wu <flamingice@sourmilk.net>
srcversion:     ADF1CC74E82DC7AC0ACB656
alias:          pci:v00001186d00003300sv*sd*bc*sc*i*
alias:          pci:v00001799d00006020sv*sd*bc*sc*i*
alias:          pci:v00001799d00006001sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008180sv*sd*bc*sc*i*
alias:          pci:v00001799d0000701Fsv*sd*bc*sc*i*
alias:          pci:v0000[COLOR=Red]1799[/COLOR]d0000[COLOR=Red]700F[/COLOR]sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008185sv*sd*bc*sc*i*
depends:        mac80211,eeprom_93cx6,cfg80211


copy and paste in terminal

```
sudo iwlist scan
```

---

### Post by boreen on 2011-08-08
Hi,

I will try this tomorrow and post back with the information.

Thanks for the help!

-Jon

---

