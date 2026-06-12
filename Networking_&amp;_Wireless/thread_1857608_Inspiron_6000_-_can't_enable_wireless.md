---
title: "Inspiron 6000 - can't enable wireless"
date: 2011-10-10
forum: Networking &amp; Wireless
---

### Post by roofusthedoofus1 on 2011-10-10
This is driving me bananas, i'm pulling my hair out here.  

All i want to do is enable my recognised wireless.  Thats it. 

I'm using a Dell Inspiron 6000.  I was using xubuntu 11.04 with wireless fully functional and automatically enabled and installed with absolutely no problems.  Then today i reinstalled Ubuntu 11.04 completely.  For some reason the installation is unable to automatically enable WiFi.

So now i've got a PRO/Wireless 2200BG network connection that is disabled.  In the top right hand corner on the panel there is no wireless symbol as before, instead an up arrow and a down arrow.  When i click on this there is nothing referring to wireless.

I tried to use the keyboard to manually turn it on (Fn + F2) but this doesn't work (the wireless symbol/light thingy above the keyboard remains unlit.)

'iwconfig' tells me it is listed as eth1-eth0.

'sudo lshw -C network' returns network:0 as being the wired network, network:1 DISABLED and being the wireless network.

'ip link set eth1-eth0 up' returns 'RTNETLINK answers: Operation not permitted'.  Pouring over many suggestions around the interwebs this came up as a suggestion to enable the wireless adapter.  Didn't work.

I know fair bit about computing but i'm only a month in with Ubuntu so i'm a total beginner with all this terminal stuff.

Thanks in advance for your replies!!!

---

### Post by chili555 on 2011-10-10
> i'm only a month in with Ubuntu so i'm a total beginner with all this terminal stuff.We promise we'll be gentle! Please open a terminal and run and post here:```
rfkill list all
```Thanks.

---

### Post by roofusthedoofus1 on 2011-10-10
hey!

Thanks for such a quick reply chili555!

i get this:

0:  phy0: Wireless LAN
Softblocked: no
hardblocked: no

---

### Post by chili555 on 2011-10-10
Well, that's not what I expected to see; it looks perfect! Nothing to fix there. Let's dig deeper. Please run and post:```
dmesg | grep -e eth1 -e ipw
```The pipe symbol | is on the right side of my US keyboard on the same sey with \. Thanks.

---

### Post by roofusthedoofus1 on 2011-10-10
'dmesg | grep -e eth1 -e ipw' returns: 

dmesg: invalid option -- 'e'

hmm....

---

### Post by collisionystm on 2011-10-10
> **roofusthedoofus1 said:**
> 'dmesg | grep -e eth1 -e ipw' returns: 

dmesg: invalid option -- 'e'

hmm....

```

dmesg | grep -e eth1 -e ipw
```

Works for me...


Just FYI.

---

### Post by chili555 on 2011-10-10
Me, too. Please try again and proofread carefully. Make sure it is -e and not -  e.

---

### Post by roofusthedoofus1 on 2011-10-10
unfortunately still the same, returns:

dmesg: invalid option -- 'e'
Usage: [-c] [-n level] [-r] [-s bufsize]

---

### Post by pdc on 2011-10-11
I wonder if you are able to copy and paste the commands that chili recommends.........from his post into your computer ...........perhaps it would help you

---

### Post by roofusthedoofus1 on 2011-10-11
Hey there again,

Turns out i had a different type of 'pipe' inserted... god knows.    Your patience is appreciated. Anyway here's what returns:

[   23.088989] libipw: 802.11 data/management/control stack, git-1.1.13
[   23.088998] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   23.243532] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   23.243541] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   23.243695] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   23.250012] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   23.632559] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)
[   23.677687] <30>udev[324]: renamed network interface eth1 to eth1-eth0


Thanks again

---

### Post by chili555 on 2011-10-11
That also is not remarkable; nothing wrong. Let's see:```
dmesg | grep eth
sudo lshw -C network
sudo cat /etc/udev/rules.d/70-persistent-net.rules
```Thanks.

---

### Post by roofusthedoofus1 on 2011-10-11
satan@Satan:~$ dmesg | grep eth
[    0.356998] i2c-core: driver [adp5520] using legacy suspend method
[    0.357002] i2c-core: driver [adp5520] using legacy resume method
[    2.112369] b44 ssb0:0: eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:12:3f:e7:9e:ee
[   20.477463] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.482438] <30>udev[308]: renamed network interface eth1 to eth1-eth0
[  127.104070] eth1-eth0: no IPv6 routers present
[ 4463.706673] ADDRCONF(NETDEV_UP): eth1-eth0: link is not ready
satan@Satan:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:e7:9e:ee
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:18 memory:dfdfe000-dfdfffff
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1-eth0
       version: 05
       serial: 00:13:ce:10:19:ac
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:dfdfd000-dfdfdfff
satan@Satan:~$ sudo cat /etc/udev/rules.d/70-persistent-net.rules
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x8086:0x4220 (ipw2200)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:13:ce:10:19:ac", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x170c (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:12:3f:e7:9e:ee", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

---

### Post by chili555 on 2011-10-11
Please do:```
sudo gedit /etc/udev/rules.d/70-persistent-net.rules
```Change the entries as shown:```
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x8086:0x4220 (ipw2200)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:13:ce:10:19:ac", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="[COLOR="Red"]eth1[/COLOR]"

# PCI device 0x14e4:0x170c (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:12:3f:e7:9e:ee", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="[COLOR="red"]eth0[/COLOR]"
```Proofread, save and close gedit. Reboot and give us your report.

My suspicion is that Network Manager is having trouble managing eth1-eth0.

---

### Post by praseodym on 2011-10-11
Strange, normally eth0 is wired [COLOR="Red"](Edit: see chili555's changes)[/COLOR], but anyway: This driver is no longer developed, therefore it makes problems with the new kernel and sometimes with the network-manager.
Does the router work on channel 12 or 13 (if possible)? This device doesnt work on these channels.


Alternatively: Try Wicd instead:


```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service network-manager stop
sudo service wicd restart
```
Deactivate the networkmanager in "autostart", choose "eth0" as wireless interface [COLOR="Red"](Edit: or eth1 if changed) [/COLOR]and "wext" as driver. Check:

```
iwconfig
sudo iwlist scan
dmesg | grep ipw
lsmod
iwlist chan
```

---

### Post by roofusthedoofus1 on 2011-10-11
Ok i connected to the internet for the first time there using ethernet, it did a buttload of updates, i rebooted and wireless internet is now up and running.  

Thanks for everyones help, its great theres forums like this to help you !!

---

### Post by PsychicNut on 2011-11-08
Hi Praseodym,
I was reading this thread and have the same problem with my Intel Pro/wireless 2200BG

```

You wrote:
Deactivate the networkmanager in "autostart", choose "eth0" as wireless interface (Edit: or eth1 if changed) and "wext" as driver. Check:
```

I am trying to follow your instructions and am stuck at "autostart"

How do I find that or open that file?
Thanks
Psychic

---

### Post by praseodym on 2011-11-09
Start it from terminal with

```
gnome-session-properties
```

---

### Post by benhanby on 2012-08-17
Hey , i am having similar problems with an inspiron 1501. 
I am running Xubuntu on a partition with windows xp , when on xp wireless works perfectly but when i switch to xubuntu it doesn't. The wifi light doesn't light up and the fn key doesn't work , so i am not able to turn it on. Any help is greatly appreciated. 
Regards 
Ben.

---

### Post by praseodym on 2012-08-17
Tried to reset the BIOS to default? Please show:
```

lsmod
rfkill list
```

---

### Post by benhanby on 2012-08-19
The results i got for lsmod 

Module                 size  used by 
joydev                17393  0
snd_hda_codec_idt     60251  1
snd_hda_intel         32765  4
snd_hda_codec        109562  2  snd_hda_codec_idt,snd_hda_intel
snd_hwdep             13276  1  snd_hda_codec
snd_pcm               80845  2  snd_hda_intel,snd_hda_codec
snd_seq_midi          13132  0
snd_rawmidi           25323  1  snd_seq_midi
dell_laptop           17767  0
dcdbas                14098  1  dell_laptop 
b44                   31412  0
radeon               733867  2
snd_seq_midi_event    14475  1  snd_seq_midi
ssb                   50691  1  b44
snd_seq               51567  2  snd_seq_midi,snd_seq_midi_event
wl                  2646601  0
psmouse               87213  0
snd_timer             28931  2  snd_pcm,snd_seq
snd_seq_devices       14172  3  snd_seq_midi,snd_rawmidi,snd_seq
ttm                   65344  1  radeon
snd                   62064  17 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper        45466  1  radeon
serio_raw             13027  0
drm                  197692  4  radeon,ttm,drm_kms_helper
soundcore             14635  1  snd 
sp5100_tco            13459  0
k8temp                12905  0
snd_page_alloc        14115  2  snd_hda_intel,snd_pcm
parport_pc            13093  0
i2c_piix4             13093  0
rfcomm                38139  4
ppdev                 12849  0
bnep                  17830  2
bluetooth            158438  10 rfcomm,bnep
i2c_algo_bit          13199  1  radeon 
lib80211              14040  1  wl 
ati_agp               13242  0
shpchp                32325  0
mac_hid               13077  0
lp                    17455  0 
parport               40930  3  parport_pc,ppdev,lp
usbhid                41906  0
hid                   77367  1  usbhid
sdhci_pci             18324  0
sdhci                 28241  1  sdhci_pci
pata_atiixp           12999  0 


Here are the results for rfkill list 

0: dell-wifi: wireless LAN
        soft blocked: no
        hard blocked: no 

Sorry about the long reply ,
thanks for your time !
Regards,
Ben.

---

### Post by benhanby on 2012-08-19
Sorry about the previous post if you click quote then it appears in the correct formatting.

---

### Post by praseodym on 2012-08-19
The module "dell_laptop" is buggy and was replaced by "dell_wmi":

```
sudo modprobe -rf dell_laptop
echo "options dell_wmi wireless=1" | sudo tee /ect/modprobe.d/dell_wmi.conf 
sudo modprobe dell_wmi
```

---

### Post by benhanby on 2012-08-19
Hi thanks for your help and patient but i am afraid that when i enter the second line i get the response as follows :

tee: /ect/modprobe.d/dell_wmi.conf: No such file or directory
options dell_wmi wireless=1

Any help would be appreciated greatly 
Regards 
Ben.

---

### Post by danmanmj on 2012-08-19
Ok litterally just installed Ubuntu today first time user. I've tried all of the code above but can't seem to get anything to work. I'm using an Inspiron 6000 and I have a PRO/Wireless 2200BG [Calexico2] wireless card. 
Would really appreciate some expert advice to get this old beast wireless!

Thanks

---

### Post by benhanby on 2012-08-19
I'm pretty new at this also but it you post some of the results of the commands you have tried that may help out someone who is better placed to help you :) 
Regards
Ben.

---

### Post by praseodym on 2012-08-19
@benhanby: Sorry, typo:

```
sudo modprobe -rf dell_laptop
echo "options dell_wmi wireless=1" | sudo tee /[COLOR="Red"]etc[/COLOR]/modprobe.d/dell_wmi.conf 
sudo modprobe dell_wmi
```

@danmanmj:

Please show the outputs of:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by danmanmj on 2012-08-20
Thanks for your help, here you go!

dan@ubuntu:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Inspiron 6000 laptop [1028:0188]
    Kernel driver in use: b44
--
03:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
    Subsystem: Intel Corporation Dell Latitude D600 [8086:2722]
    Kernel driver in use: ipw2200
dan@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 3538:0901 Power Quotient International Co., Ltd 
Bus 005 Device 002: ID 046d:c526 Logitech, Inc. Nano Receiver
dan@ubuntu:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  0 
ppdev                  12849  0 
bluetooth             158438  10 rfcomm,bnep
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
snd_intel8x0           33455  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
dell_laptop            13671  0 
dcdbas                 14098  1 dell_laptop
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ipw2200               146207  0 
pcmcia                 39791  0 
libipw                 46701  1 ipw2200
psmouse                72846  0 
snd                    62064  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              178679  2 ipw2200,libipw
i915                  414603  3 
serio_raw              13027  0 
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
soundcore              14635  1 snd
lib80211               14040  2 ipw2200,libipw
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc         14108  2 snd_intel8x0,snd_pcm
joydev                 17393  0 
mac_hid                13077  0 
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
usbhid                 41906  0 
hid                    77367  1 usbhid
firewire_ohci          40172  0 
sdhci_pci              18324  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
b44                    31364  0 
ssb                    50691  1 b44
sdhci                  28241  1 sdhci_pci
usb_storage            39646  1 
dan@ubuntu:~$ iwconfig
eth3      IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth2      no wireless extensions.

---

### Post by benhanby on 2012-08-20
Hi, thanks for your help. When i enter the third command i get the response as follows:

:~$ sudo modprobe dell_wmi
FATAL: Error inserting dell_wmi (/lib/modules/3.2.0-29-generic/kernel/drivers/platform/x86/dell-wmi.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Sorry to keep bothering you , thanks for the help :)
Regards 
Ben.

---

