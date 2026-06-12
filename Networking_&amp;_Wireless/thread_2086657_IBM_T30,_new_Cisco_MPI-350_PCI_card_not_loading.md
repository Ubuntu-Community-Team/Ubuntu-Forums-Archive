---
title: "IBM T30, new Cisco MPI-350 PCI card not loading"
date: 2012-11-21
forum: Networking &amp; Wireless
---

### Post by dstke on 2012-11-21
I installed a new Cisco MPI-350 PCI card into an IBM T30 Laptop.  Unfortunately the card is not responding.  

From the below queries it appears that the system sees the card but is not able to address it.  

Appreciate any assistance offered.


doug@doug-laptop:~$ lsb_release -d
Description:	Ubuntu 12.04.1 LTS

doug@doug-laptop:~$ uname -mr
3.2.0-32-generic-pae i686

doug@doug-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV200 [Mobility Radeon 7500]
02:00.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:02.0 Network controller: Cisco Aironet Wireless Communications Cisco Aironet Wireless 802.11b
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)

doug@doug-laptop:~$ lspci -nn | grep 'Cisco'
02:02.0 Network controller [0280]: Cisco Aironet Wireless Communications Cisco Aironet Wireless 802.11b [14b9:a504]

doug@doug-laptop:~$ iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.

doug@doug-laptop:~$ lsmod
Module                  Size  Used by
joydev                 17393  0 
thinkpad_acpi          73942  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
pcmcia                 39791  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_intel8x0           33455  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
psmouse                86486  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              28931  2 snd_seq,snd_pcm
radeon                737891  2 
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
airo                   77500  0 
serio_raw              13027  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd                    62064  12 thinkpad_acpi,snd_rawmidi,snd_intel8x0,snd_ac97_codec,snd_seq,snd_pcm,snd_seq_device,snd_timer
snd_page_alloc         14108  2 snd_intel8x0,snd_pcm
shpchp                 32325  0 
soundcore              14635  1 snd
nvram                  14029  1 thinkpad_acpi
bnep                   17830  2 
nsc_ircc               23240  0 
irda                  185517  1 nsc_ircc
bluetooth             158438  7 bnep
ppdev                  12849  0 
video                  19068  0 
ttm                    65344  1 radeon
crc_ccitt              12595  1 irda
parport_pc             32114  1 
drm_kms_helper         45466  1 radeon
drm                   197599  4 radeon,ttm,drm_kms_helper
mac_hid                13077  0 
i2c_algo_bit           13199  1 radeon
ndiswrapper           192268  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
e100                   36289  0 
floppy                 60310  0 

It appears from above that both the airo and ndiswrapper modules are installed.  Is this a problem?  I installed the ndiswapper to get a USB wireless adapter to work but was unable to get it working reliably.

doug@doug-laptop:~$ dmesg | grep 'airo'
[   27.788306] airo(): Probing for PCI adapters
[   28.452527] airo 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   28.452573] airo(): Found an MPI350 card
[   36.789776] airo(): Max tries exceeded when issuing command
[   36.789790] airo(): Couldn't allocate RX FID
[   36.789884] airo(): Could not map memory
[   36.789923] airo 0000:02:02.0: PCI INT A disabled
[   36.801643] airo(): Finished probing for PCI adapters

doug@doug-laptop:~$ sudo lshw -C network
[sudo] password for doug: 
  *-network:0 UNCLAIMED   
       description: Network controller
       product: Cisco Aironet Wireless 802.11b
       vendor: Cisco Aironet Wireless Communications
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd cap_list
       configuration: latency=64 maxlatency=4 mingnt=4
       resources: ioport:8000(size=256) memory:d0200000-d0203fff memory:d0400000

doug@doug-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

doug@doug-laptop:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ]

---

### Post by wildmanne39 on 2012-11-21
Hi, yes you need to remove ndiswrapper.
```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a

```
Thanks

---

### Post by dstke on 2012-11-21
Tried to remove ndiswrapper using the commands listed below however after reboot it appears that ndiswrapper is still installed.

here are the responses from the same queries made after reboot.

doug@doug-laptop:~$ iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.

doug@doug-laptop:~$ lsmod
Module                  Size  Used by
joydev                 17393  0 
pcmcia                 39791  0 
radeon                737891  2 
thinkpad_acpi          73942  0 
snd_seq_midi           13132  0 
snd_intel8x0           33455  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_rawmidi            25424  1 snd_seq_midi
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                86486  0 
drm                   197599  4 radeon,ttm,drm_kms_helper
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
airo                   77500  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              13027  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_page_alloc         14108  2 snd_intel8x0,snd_pcm
i2c_algo_bit           13199  1 radeon
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
shpchp                 32325  0 
snd                    62064  12 thinkpad_acpi,snd_intel8x0,snd_ac97_codec,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
bnep                   17830  2 
nsc_ircc               23240  0 
video                  19068  0 
irda                  185517  1 nsc_ircc
bluetooth             158438  7 bnep
ppdev                  12849  0 
nvram                  14029  1 thinkpad_acpi
parport_pc             32114  1 
crc_ccitt              12595  1 irda
mac_hid                13077  0 
ndiswrapper           192268  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
e100                   36289  0 
floppy                 60310  0 
doug@doug-laptop:~$ dmesg | grep 'airo'
[   26.383902] airo(): Probing for PCI adapters
[   26.976258] airo 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   26.976307] airo(): Found an MPI350 card
[   33.020040] airo(): Max tries exceeded when issuing command
[   33.020053] airo(): Couldn't allocate RX FID
[   33.020146] airo(): Could not map memory
[   33.020184] airo 0000:02:02.0: PCI INT A disabled
[   33.029462] airo(): Finished probing for PCI adapters
doug@doug-laptop:~$ sudo lshw -C network
[sudo] password for doug: 
  *-network:0 UNCLAIMED   
       description: Network controller
       product: Cisco Aironet Wireless 802.11b
       vendor: Cisco Aironet Wireless Communications
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd cap_list
       configuration: latency=64 maxlatency=4 mingnt=4
       resources: ioport:8000(size=256) memory:d0200000-d0203fff memory:d0400000-d07fffff memory:f0000000-f01fffff
  *-network:1
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:09:6b:10:16:fa
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.2.122 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:11 memory:d0204000-d0204fff ioport:8400(size=64)
doug@doug-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

doug@doug-laptop:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ]

---

### Post by dstke on 2012-11-21
Ran the uninstall commands again and it appears here that ndiswrapper is uninstalled.

doug@doug-laptop:~$ sudo modprobe -rf ndiswrapper
[sudo] password for doug: 

doug@doug-laptop:~$ sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ndisgtk is not installed, so not removed
Package ndiswrapper-common is not installed, so not removed
Package ndiswrapper-utils-1.9 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 66 not upgraded.

doug@doug-laptop:~$ sudo rm /etc/modprobe.d/ndiswrapper.conf
rm: cannot remove `/etc/modprobe.d/ndiswrapper.conf': No such file or directory

doug@doug-laptop:~$ sudo rm -r /etc/ndiswrapper/* 
rm: cannot remove `/etc/ndiswrapper/*': No such file or directory

doug@doug-laptop:~$ sudo depmod -a

---

