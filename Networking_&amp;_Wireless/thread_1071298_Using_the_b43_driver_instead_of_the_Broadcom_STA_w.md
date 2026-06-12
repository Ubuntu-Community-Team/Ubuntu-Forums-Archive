---
title: "Using the b43 driver instead of the Broadcom STA wireless driver &quot;wl&quot;"
date: 2009-02-16
forum: Networking &amp; Wireless
---

### Post by jaxx2kde on 2009-02-16
I am running Ubuntu 8.10 Intrepid Ibex with kernel 2.6.27-7 on a Dell Vostro 1400 with a BCM4311 802.11b/g WLAN (rev 01) wireless card. After performing the install the restricted driver manager showed that a new "wl" driver can be installed, so I went ahead and installed it and my wireless card is working perfectly.

Now I want to install aircrack-ng and I need to have the b43 drivers instead of the proprietary "wl" drivers. This is where the problem starts. I am not able to get my machine to use the b43 drivers instead of the wl. I installed b43-fwcutter but it still shows "wl" as the default drivers in use. I tried blacklisting wl from /etc/modprobe.d but my wireless card doesn't get detected then.

Following is some more information about my system:

```
$ lsmod | grep -e wl -e b43
wl                   1076372  0 
ieee80211_crypt        13572  2 ieee80211_crypt_tkip,wl

```

```
$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:1c:26:55:0d:e3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=141.213.39.115 latency=0 module=wl wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:fe:04:01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 latency=0 module=tg3 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 36:ac:52:9c:fb:3a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

```
$ lspci -nnm
00:00.0 "Host bridge [0600]" "Intel Corporation [8086]" "Mobile PM965/GM965/GL960 Memory Controller Hub [2a00]" -r0c "Dell [1028]" "Device [0227]"
00:01.0 "PCI bridge [0604]" "Intel Corporation [8086]" "Mobile PM965/GM965/GL960 PCI Express Root Port [2a01]" -r0c "" ""
00:1a.0 "USB Controller [0c03]" "Intel Corporation [8086]" "82801H (ICH8 Family) USB UHCI Controller #4 [2834]" -r02 "Dell [1028]" "Device [0227]"
00:1a.1 "USB Controller [0c03]" "Intel Corporation [8086]" "82801H (ICH8 Family) USB UHCI Controller #5 [2835]" -r02 "Dell [1028]" "Device [0227]"
00:1a.7 "USB Controller [0c03]" "Intel Corporation [8086]" "82801H (ICH8 Family) USB2 EHCI Controller #2 [283a]" -r02 -p20 "Dell [1028]" "Device [0227]"
00:1b.0 "Audio device [0403]" "Intel Corporation [8086]" "82801H (ICH8 Family) HD Audio Controller [284b]" -r02 "Dell [1028]" "Device [0227]"
00:1c.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82801H (ICH8 Family) PCI Express Port 1 [283f]" -r02 "" ""
00:1c.1 "PCI bridge [0604]" "Intel Corporation [8086]" "82801H (ICH8 Family) PCI Express Port 2 [2841]" -r02 "" ""
00:1c.3 "PCI bridge [0604]" "Intel Corporation [8086]" "82801H (ICH8 Family) PCI Express Port 4 [2845]" -r02 "" ""
00:1c.5 "PCI bridge [0604]" "Intel Corporation [8086]" "82801H (ICH8 Family) PCI Express Port 6 [2849]" -r02 "" ""
00:1d.0 "USB Controller [0c03]" "Intel Corporation [8086]" "82801H (ICH8 Family) USB UHCI Controller #1 [2830]" -r02 "Dell [1028]" "Device [0227]"
00:1d.1 "USB Controller [0c03]" "Intel Corporation [8086]" "82801H (ICH8 Family) USB UHCI Controller #2 [2831]" -r02 "Dell [1028]" "Device [0227]"
00:1d.2 "USB Controller [0c03]" "Intel Corporation [8086]" "82801H (ICH8 Family) USB UHCI Controller #3 [2832]" -r02 "Dell [1028]" "Device [0227]"
00:1d.7 "USB Controller [0c03]" "Intel Corporation [8086]" "82801H (ICH8 Family) USB2 EHCI Controller #1 [2836]" -r02 -p20 "Dell [1028]" "Device [0227]"
00:1e.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82801 Mobile PCI Bridge [2448]" -rf2 -p01 "" ""
00:1f.0 "ISA bridge [0601]" "Intel Corporation [8086]" "82801HEM (ICH8M) LPC Interface Controller [2815]" -r02 "Dell [1028]" "Device [0227]"
00:1f.1 "IDE interface [0101]" "Intel Corporation [8086]" "82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [2850]" -r02 -p8a "Dell [1028]" "Device [0227]"
00:1f.2 "SATA controller [0106]" "Intel Corporation [8086]" "82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [2829]" -r02 -p01 "Dell [1028]" "Device [0227]"
00:1f.3 "SMBus [0c05]" "Intel Corporation [8086]" "82801H (ICH8 Family) SMBus Controller [283e]" -r02 "Dell [1028]" "Device [0227]"
01:00.0 "VGA compatible controller [0300]" "nVidia Corporation [10de]" "GeForce 8400M GS [0427]" -ra1 "Dell [1028]" "Device [0227]"
03:01.0 "FireWire (IEEE 1394) [0c00]" "Ricoh Co Ltd [1180]" "R5C832 IEEE 1394 Controller [0832]" -r05 -p10 "Dell [1028]" "Device [0227]"
03:01.1 "SD Host controller [0805]" "Ricoh Co Ltd [1180]" "R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [0822]" -r22 -p01 "Dell [1028]" "Device [0227]"
03:01.2 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "R5C592 Memory Stick Bus Host Adapter [0592]" -r12 "Dell [1028]" "Device [0227]"
03:01.3 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "xD-Picture Card Controller [0852]" -r12 "Dell [1028]" "Device [0227]"
09:00.0 "Ethernet controller [0200]" "Broadcom Corporation [14e4]" "NetLink BCM5906M Fast Ethernet PCI Express [1713]" -r02 "Dell [1028]" "Device [0227]"
0c:00.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4311 802.11b/g WLAN [4311]" -r01 "Dell [1028]" "Device [0007]"

```

```
$ modinfo b43
filename:       /lib/modules/2.6.27-7-generic/updates/drivers/net/wireless/b43/b43.ko
firmware:       FW13
license:        GPL
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     51072B8364ED8E0FC51639B
alias:          pcmcia:m02D0c0448f*fn*pfn*pa*pb*pc*pd*
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        pcmcia,mac80211,ssb,input-polldev,pcmcia_core,led-class,rfkill,cfg80211
vermagic:       2.6.27-7-generic SMP mod_unload modversions 586 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistance (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
```

```

$ modinfo wl
filename:       /lib/modules/2.6.27-7-generic/volatile/wl.ko
alias:          pci:v000014E4d0000432Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004313sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
depends:        ieee80211_crypt
vermagic:       2.6.27-7-generic SMP mod_unload modversions 586 
license:        MIXED/Proprietary
parm:           oneonly:int
parm:           piomode:int
parm:           nompc:int
parm:           name:string
```



To summarize  my problem, I am using the "wl" drivers for Broadcom and I wish to use the b43 drivers instead.

Thanks for the help.

---

### Post by kevdog on 2009-02-16
Hopefully b43 is compatible with your chipset (I have not verified this info).

Wouldn't it be as simple as

sudo ifconfig wlan0 down
sudo rmmod wl
sudo modprobe b43
sudo ifconfig wlan0 up

And check with
lshw -C network

---

### Post by Ayuthia on 2009-02-16
The 4311 rev 01 card is compatible with the b43 module.  kevdog's info should be able to get your card up and running.  Those are the commands that I use when I am switching wireless modules and I have a 4311 rev 01 card.

If it does not work, please post the lsmod and lshw results again after using kevdog's suggests along with:
```
dmesg|grep b43
```

---

### Post by jaxx2kde on 2009-02-16
It works! Sweet! :D
I was able to successfully go into monitor mode. Thanks a lot guys. 

Gave these commands to go into monitor mode:

sudo ifconfig wlan0 down
sudo rmmod wl
sudo modprobe b43
sudo iwconfig wlan0 mode Monitor
sudo ifconfig wlan0 up
sudo airodump-ng wlan0

How to get out of the monitor mode without having to restart every time?

I don't know if I should be bothered about this, but the Hardware Driver manager still shows Broadcom STA river in use though. I don't have the b43 drivers listed there.

Thanks a lot! I have editing these posts a lot, sorry for the inconvenience caused if any.

---

### Post by jaxx2kde on 2009-02-17
Any idea why I get an error after the first command?

```
$ sudo ifconfig wlan0 down
wlan0: ERROR while getting interface flags: No such device
```

btw

```
$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:1c:26:55:0d:e3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=141.213.39.115 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:fe:04:01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 latency=0 module=tg3 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: d2:d6:f6:dc:01:cd
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

```
$ lsmod
Module                  Size  Used by
ipv6                  263972  10 
af_packet              25728  4 
binfmt_misc            16904  1 
rfcomm                 44432  2 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  16 rfcomm,bnep
ppdev                  15620  0 
acpi_cpufreq           15500  1 
cpufreq_ondemand       14988  1 
cpufreq_stats          13188  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace      11396  0 
cpufreq_powersave       9856  0 
cpufreq_conservative    14600  0 
container              11520  0 
pci_slot               12552  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
uvcvideo               62728  0 
compat_ioctl32          9344  1 uvcvideo
videodev               41344  1 uvcvideo
dcdbas                 15008  0 
v4l1_compat            22404  2 uvcvideo,videodev
snd_hda_intel         381488  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  2 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
sdhci_pci              15360  0 
sdhci                  23940  1 sdhci_pci
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
pcspkr                 10624  0 
snd_rawmidi            29824  1 snd_seq_midi
evdev                  17696  18 
serio_raw              13444  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
ieee80211_crypt_tkip    17024  0 
psmouse                45200  0 
btusb                  19736  3 
wl                   1076372  0 
ieee80211_crypt        13572  2 ieee80211_crypt_tkip,wl
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
bluetooth              61924  11 rfcomm,sco,bnep,l2cap,btusb
mmc_core               58268  1 sdhci
nvidia               6909268  38 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_core               31892  1 nvidia
video                  25104  10 
output                 11008  1 video
snd                    63268  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ac                     12292  0 
wmi                    14504  0 
battery                18436  0 
soundcore              15328  2 snd
button                 14224  0 
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
intel_agp              33724  0 
agpgart                42184  2 nvidia,intel_agp
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
ext3                  133256  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
usbhid                 35840  0 
hid                    50560  1 usbhid
sr_mod                 22212  0 
sd_mod                 42264  3 
cdrom                  43168  1 sr_mod
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
pata_acpi              12160  0 
ata_generic            12932  0 
ahci                   37132  2 
ata_piix               24580  0 
libata                177312  4 pata_acpi,ata_generic,ahci,ata_piix
scsi_mod              155212  5 sbp2,sr_mod,sd_mod,sg,libata
ohci1394               37936  0 
dock                   16656  1 libata
tg3                   129924  0 
libphy                 27392  1 tg3
ieee1394               96324  2 sbp2,ohci1394
ehci_hcd               43276  0 
uhci_hcd               30736  0 
usbcore               148848  6 uvcvideo,btusb,usbhid,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3
```

There's no output for dmesg | grep b43

---

### Post by jaxx2kde on 2009-02-17
Also, I was wondering if I still need to patch the drivers. I was told on the IRC that I need to patch these:
b43-injection-2.6.24.4.patch
mac80211_2.6.24.4_frag.patch

I was following the tutorial here to patch:
[http://forums.nubuntu.org/archive/index.php/thread-261.html](http://forums.nubuntu.org/archive/index.php/thread-261.html)

---

### Post by kevdog on 2009-02-17
Hold on a second.  The instructions you are following are for Hardy's kernel, but previously you stated you were using 8.10 or Intrepid.

Could you post your kernel version with:
uname -r

In more recent kernels, b43 does not need to be patched, only the mac80211 module (and this patch is only for speed, but by all means not a necessity).

Also the patches you want to apply are for the Hardy kernel -- which I believe you do not have!

---

### Post by SkizZ0 on 2009-03-16
Hi all! i've the same issue described into this topic, i wish to activate the monitor mode on my BCM4311 Wifi adapter...

i have a problem with the first command:

```

skizzo@skizzo-linux:~$ sudo ifconfig wlan0 down
wlan0: ERRORE leggendo i flag dell'interfaccia: Nessun device

```

but, as in my config, if i type:

*skizzo@skizzo-linux:~$ sudo ifconfig eth1 down*

i can proceed with the procedure, and i stops at:
*sudo ifconfig wlan0 up*

where i should write (as before)
*sudo ifconfig eth1 up*

but doesn't work.... no device error :(
At this point, if i open Drivers Hardware, i see the STA broadcomm drivers and the B43 drivers. If i try to activate them, after a while it gives me an error dialog box with nothing writed, just an OK...
I've not installed/copiedanything, just typed the commands suggested before into the topic.

Also i've noticed that my driver is "wl0" and not "wl" ?


Please help me, i'm using Ubuntu 8.10

```

skizzo@skizzo-linux:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:73:2f:5f:0d
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.27.12 ip=192.168.1.102 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 16:33:56:66:4a:4f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

:::::::::::::::.EdiT::::::::::::::.

I have installed the b43 fwcutter:
*sudo apt-get install b43-fwcutter*
after this, i have enabled the b43 driver into the Driver Hardware menu item, enabled the monitor mode and all works.

The only thing is, i cannot go out from monitor mode typing:
*sudo iwconfig wlan0 mode Managed*

then, i cannot navigate, until i reboot....
the 
*sudo iwconfig wlan0 mode Managed *
doesn't work

Now my question is:
**Can i switch easily between the two modes/ drivers, with few commands and without reboot??**


...this is my last "configuration", but when i switch in monitor mode, i can't revert:

```

skizzo@skizzo-linux:~$ sudo lshw -C network
[sudo] password for skizzo: 
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:2f:5f:0d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.102 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 66:d6:d8:22:45:d5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


```

---

### Post by kevdog on 2009-03-17
Just a word of advice when going into monitor mode using b43.  Its best to first create a virtual interface -- and use the virtual interface to go into monitor mode.  This leaves wlan0 in normal managed mode.  

This can be done by the following:
Another way of setting the card in monitor mode: (Recommended)

This way, you can monitor on mon0 while still being associated on wlan0.
- libnl1 and libnl-dev is needed for iw,

To install from the Ubuntu Repository, you can run:
Code:
sudo apt-get install libnl-dev


- Install iw, for info go here [http://www.aircrack-ng.org/doku.php?id=](http://www.aircrack-ng.org/doku.php?id=) ... talling_iw
Code:
sudo mkdir iw
cd iw
sudo wget [http://dl.aircrack-ng.org/iw.tar.bz2](http://dl.aircrack-ng.org/iw.tar.bz2)
sudo tar xjf iw.tar.bz2
sudo make
sudo make install

- Instead of setting monitor mode on wlan0, create mon0 using
Code:
sudo airmon-ng start wlan0
and you can go here for more information [http://www.aircrack-ng.org/doku.php?id=airmon-ng](http://www.aircrack-ng.org/doku.php?id=airmon-ng)
- Test
Code:
sudo aireplay-ng -9 mon0
and see if injection works.

Edit /etc/modprobe.d/options, by
Code:
sudo gedit /etc/modprobe.d/options

and add a new line containing "options b43 nohwcrypt=1" This ensures that the encryption on wlan0 doesn't interfere with monitoring. This should be only enabled when aircracking with mon0, as it increases the softmac overhead. Remove it from your options list when not using aircrack for a longer time.
This is a workaround for a known bug in b43.

After that, use "mon0' for all moninjection tasks.

---

### Post by SkizZ0 on 2009-03-17
Many Many thanks man!! ... you're THE MAN :D

Sorry for the "noobing", but which reals problems gives the "increasing of the softmac overhead" mentioned in your previous post, when mon0 is not used?

---

### Post by kevdog on 2009-03-17
Im not exactly sure, I personally don't find any slowdown if I have the line enabled all the time.

---

### Post by garbara on 2009-03-26
I am thankful for this post. I want to do exactly what Jaxx2kde wanted to do and I have a similar set of hardware. I have the broadcom wl driver working fine. I would like to install the b43 driver to run aircrack-ng also.

First of all some information. I am running ubuntu 8.10. I have used the system->administration->harware drivers menu option to install the STA driver then the b43 driver. the b43 driver did not work so I disabled it and re-installed the STA driver all form the menu mentioned above.

```
root@lappy:~# uname -r
2.6.27-11-generic

root@lappy:~# lsmod | grep -e wl -e b43
wl                   1080212  0 
ieee80211_crypt        13572  2 ieee80211_crypt_tkip,wl

root@lappy:~# lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:16:cf:c9:17:49
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.27.12 ip=192.168.0.3 latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:5c:0a:f1
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.3 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: e6:0e:1c:51:35:e4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```
```
root@lappy:~# lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01)

```

A couple of differences I have a 4328 chipset and I don't have a wlan0 device only eth0 for my ethernet and eth1 for the wireless connection. When I run the commands suggested by kevdog. I get these results

```
root@lappy:~# rmmod wl
root@lappy:~# modprobe b43
root@lappy:~# ifconfig eth1 up
eth1: ERROR while getting interface flags: No such device
```

I think the problem may be related to the fact that I have not installed firmware after I installed b43-fwcutter. I tried but failed. I have a dual boot system so I have my windows drivers I copied bcmwl5.sys to a temporary directory and ran

```
b43-fwcutter  bcmwl5.sys
Sorry, the input file is either wrong or not supported by b43-fwcutter.
This file has an unknown MD5sum b89bcf0a25aeb3b47030ac83287f894a.
```

I can restore the wireless connection by 
rmmod b43
modprobe wl

I am sorry that I am such a noobie I have only used linux for 4 years. If I need to install firmware where would I get it? If that is not what I need to do where did I go wrong? Thank you in advance

---

### Post by garbara on 2009-03-28
I have some additional information,

Using the menu under System->Administration->hardware drives, I uninstalled the STA driver and installed the B43 driver then rebooted my computer. My wireless device in not recognized. Here are the results of three commands.

```
root@lappy:~# lsmod | grep b43
b43                   131356  0 
rfkill                 17176  1 b43
mac80211              216820  1 b43
led_class              12164  1 b43
input_polldev          11912  1 b43
ssb                    40580  2 b43,b44

root@lappy:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:5c:0a:f1  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe5c:af1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4625 (4.6 KB)  TX bytes:5372 (5.3 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)


root@lappy:~# dmesg | grep b43
[    2.665845] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.665859] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[   10.715056] b43-phy0: Broadcom 4321 WLAN found
[   10.761163] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 5, Type 4, Revision 1)
[   10.761193] b43: probe of ssb0:0 failed with error -95

```

I suspect that the firmware is not loaded but the directories /lib/firmware/b43 and /lib/firmware/b43legacy exist and contain files.

I appreciate your advice.

---

### Post by wynneth on 2009-04-08
> **garbara said:**
> 

A couple of differences I have a 4328 chipset and I don't have a wlan0 device only eth0 for my ethernet and eth1 for the wireless connection. When I run the commands suggested by kevdog. I get these results

```
root@lappy:~# rmmod wl
root@lappy:~# modprobe b43
root@lappy:~# ifconfig eth1 up
eth1: ERROR while getting interface flags: No such device
```

I think the problem may be related to the fact that I have not installed firmware after I installed b43-fwcutter. I tried but failed. I have a dual boot system so I have my windows drivers I copied bcmwl5.sys to a temporary directory and ran

```
b43-fwcutter  bcmwl5.sys
Sorry, the input file is either wrong or not supported by b43-fwcutter.
This file has an unknown MD5sum b89bcf0a25aeb3b47030ac83287f894a.
```

I can restore the wireless connection by 
rmmod b43
modprobe wl

I am sorry that I am such a noobie I have only used linux for 4 years. If I need to install firmware where would I get it? If that is not what I need to do where did I go wrong? Thank you in advance

Actually, I believe a part of your problem is the differences in these two drivers themselves. With the wl driver, ubuntu sets your wifi card as eth1, however the b43 driver will register the card as wlan0. Go back to after you have switched, and use wlan0 from that point on instead of eth1. (This is the case with mine, I'm on 2.6.27-11 with a Broadcom 4311.) A personal note: I got fed up with the fact that the default Ubuntu gnome installation has this crappy nm-applet wherein you cannot selectively Disconnect from a network, you have to disable the whole interface. I have since switched to knetworkmanager (from kde). AFAIK it has all the features the gnome nm-applet has, but it actually has an option to disconnect particular network connections. I was actually here puttering around to see about the mac80211 fragmentation patch and have successfully installed it as well. The instructions everywhere seem to leave out a few things I found out on my own that are important. 1)When doing a patch, make sure you are in the src directory for your kernel, i.e. /usr/src/linux-source-2.6.27 2)Make sure to run it as sudo or sudo -s to start with 3)Make sure to have the patch in the kernel source directory or use the correct path, i.e. if for some reason you don't want to copy the patch into the source directory: ```
root@yourpc$ patch -p1 /home/billyjoebob/downloads/mac80211-whateverkernel_frag.patch
```

---

### Post by Ayuthia on 2009-04-08
Actually, the 4328 card is not supported by the b43 module at this point.

---

### Post by Sureshot324 on 2009-09-21
I have the same problem as garbara.  When I use the wl driver, by wireless card shows up as eth1.  If I do this:

```

ifconfig eth1 down
rmmod wl
modprobe b43

```

the module seems to load fine and shows up if I do lsmod, but if I run ifconfig, there is no wireless device at all.  'ifconfig wlan0 up' or 'ifconfig eth1 up' it fails with this error:

wlan0: ERROR while getting interface flags: No such device

Do I need to load the firmware first?  I have a bcm4312

---

### Post by Ayuthia on 2009-09-21
> **Sureshot324 said:**
> I have the same problem as garbara.  When I use the wl driver, by wireless card shows up as eth1.  If I do this:

```

ifconfig eth1 down
rmmod wl
modprobe b43

```

the module seems to load fine and shows up if I do lsmod, but if I run ifconfig, there is no wireless device at all.  'ifconfig wlan0 up' or 'ifconfig eth1 up' it fails with this error:

wlan0: ERROR while getting interface flags: No such device

Do I need to load the firmware first?  I have a bcm4312

If you want to use the b43 module instead of the Broadcom STA version (wl), you will need to load the firmware first.  However, you say that you have the 4312 card.  You will need to make sure that it does not have the 14e4:4315 chipset:
```
lspci -nn
```
If it does, the b43 module does not support it until 2.6.32.  This means that the b43 module will not be automatically supporting it until Ubuntu 10.04 comes out.  There are manual ways to install it, but you will need some Linux experience to do it because it could be frustrating if you get stuck somewhere.  Here is the link:
[http://ubuntuforums.org/showthread.php?t=1266620](http://ubuntuforums.org/showthread.php?t=1266620)

However if you don't have the 4315 chipset, you will need to install the firmware and make sure that the Broadcom STA module is not activated or else it will cause conflicts.

---

### Post by Sureshot324 on 2009-09-22
I installed b43-fwcutter with apt-get.  The installation automatically downloads the broadcom drivers, extracts the firmware, and installs it.  So unless there are some extra steps, the firmware should be installed, but I still have the same problem.

My card is a bcm4312, which according to the b43 site is supported but 802.11g only.  (not 802.11a)

---

### Post by Ayuthia on 2009-09-22
> **Sureshot324 said:**
> I installed b43-fwcutter with apt-get.  The installation automatically downloads the broadcom drivers, extracts the firmware, and installs it.  So unless there are some extra steps, the firmware should be installed, but I still have the same problem.

My card is a bcm4312, which according to the b43 site is supported but 802.11g only.  (not 802.11a)

The 4312 card comes in different versions.  There is the 4312 rev 01 (14e4:4312), the rev 02 (14e4:4312), and the 4312 rev 01 (14e4:4315).  So if the results of lspci -nn shows that you have a 14e4:4312 chipset (not the model number), then please try the following:
```
sudo modprobe -r b43 ssb wl ndiswrapper
sudo modprobe b43
sudo iwlist scan
dmesg|grep b43
```
Please post the results of the last command.  It might help us see why the card is not starting up.

---

### Post by Sureshot324 on 2009-09-22
It is in fact a 14e4:4315.  I'm taking a look at your link now.

---

### Post by kutulu10 on 2009-11-16
> **Ayuthia said:**
> The 4312 card comes in different versions.  There is the 4312 rev 01 (14e4:4312), the rev 02 (14e4:4312), and the 4312 rev 01 (14e4:4315).  So if the results of lspci -nn shows that you have a 14e4:4312 chipset (not the model number), then please try the following:
```
sudo modprobe -r b43 ssb wl ndiswrapper
sudo modprobe b43
sudo iwlist scan
dmesg|grep b43
```Please post the results of the last command.  It might help us see why the card is not starting up.


Hi all, I'm facing the same problem here. I'm posting the results of the commands explain in the post in order.

lspci -nn | grep Broadcom
**03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)**

sudo modprobe -r b43 ssb wl ndiswrapper

[B]WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a futurerelease.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a futurerelease.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a futurerelease.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a futurerelease.[/B]


sudo modprobe b43
[B]WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a futurerelease.[/B]

sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: XX:XX:XX:XX:XX:XX
                    ESSID:" XXXXXX"           
                    Protocol:IEEE 802.11g     
                    Mode:Managed              
                    Frequency:2.462 GHz (Channel 11)
                    Quality:100/100  Signal level:-31 dBm  Noise level:-96 dBm
                    Encryption key:on                                         
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s        
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s     
                              48 Mb/s; 54 Mb/s                                
                    Extra:bcn_int=100                                         
                    Extra:atim=0                                              
          Cell 02 - Address: XX:XX:XX:XX:XX:XX                               
                    ESSID:"XXXXXX"                                       
                    Protocol:IEEE 802.11g                                     
                    Mode:Managed                                              
                    Frequency:2.462 GHz (Channel 11)                          
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm 
                    Encryption key:on                                         
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s       
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s      
                              48 Mb/s; 54 Mb/s                                
                    Extra:bcn_int=100                                         
                    Extra:atim=0                                              
                    IE: WPA Version 1                                         
                        Group Cipher : TKIP                                   
                        Pairwise Ciphers (1) : TKIP                           
                        Authentication Suites (1) : PSK                       
          Cell 03 - Address: XX:XX:XX:XX:XX:XX                               
                    ESSID:"XXXXXX"                                             
                    Protocol:IEEE 802.11g                                     
                    Mode:Managed                                              
                    Frequency:2.462 GHz (Channel 11)                          
                    Quality:54/100  Signal level:-61 dBm  Noise level:-96 dBm 
                    Encryption key:on                                         
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s       
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s      
                              48 Mb/s; 54 Mb/s                                
                    Extra:bcn_int=100                                         
                    Extra:atim=0                                              
                    IE: WPA Version 1                                         
                        Group Cipher : TKIP                                   
                        Pairwise Ciphers (1) : TKIP                           
                        Authentication Suites (1) : PSK  

Sorry for the XXXX's, but I have  to protect the victims identity ;)

dmesg | grep b43
Nothing here

And when I start sudo airmon-ng the result is

[B]Interface       Chipset         Driver

wlan0           Unknown         ndiswrapper[/B]

I think the chipset must be identified and the driver must be b43 instead ndiswrapper. 

I want to work with the aircrack-ng suite but it seems I don't have the aproppriate driver working right now.

Any help with this?

Thank you very much for your time

---

