---
title: "Modprober ndiswrapper hang"
date: 2012-05-13
forum: Networking &amp; Wireless
---

### Post by pedrok1664 on 2012-05-13
I been through all the threads i can find but cant figure out why i cant load ndiswrapper module, it just hangs my comp. iv blacklisted the orinoco_cs driver which is the driver showing as my wireless driver and followed all the other instructions but still no joy, can anyone help

*-network               
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:00:39:08:d3:8d
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.0.6 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:11 memory:f7df7000-f7df7fff ioport:dec0(size=64)

oot@peter-T8200:/home/peter# ndiswrapper -l
wlanuzg : driver installed
    device (0803:4410) present

root@peter-T8200:/home/peter# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@peter-T8200:/home/peter# 

root@peter-T8200:/home/peter# lsmod
Module                  Size  Used by
vesafb                 13516  1 
snd_ymfpci             30174  3 
gameport               15060  1 snd_ymfpci
snd_ac97_codec        106082  1 snd_ymfpci
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_ymfpci,snd_ac97_codec
snd_opl3_lib           18863  1 snd_ymfpci
snd_hwdep              13276  1 snd_opl3_lib
snd_page_alloc         14115  2 snd_ymfpci,snd_pcm
snd_mpu401_uart        13865  1 snd_ymfpci
snd_seq_midi           13132  0 
snd_rawmidi            25424  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                87213  0 
serio_raw              13027  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39791  0 
snd_timer              28931  4 snd_ymfpci,snd_pcm,snd_opl3_lib,snd_seq
irda                  185517  0 
yenta_socket           27428  0 
snd_seq_device         14172  4 snd_opl3_lib,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
video                  19068  0 
crc_ccitt              12595  1 irda
snd                    62064  16 snd_ymfpci,snd_ac97_codec,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             32114  1 
soundcore              14635  1 snd
ppdev                  12849  0 
rfcomm                 38139  4 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
toshiba_acpi           18158  0 
sparse_keymap          13658  1 toshiba_acpi
wmi                    18744  1 toshiba_acpi
mac_hid                13077  0 
shpchp                 32325  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
e100                   36289  0 
floppy                 60310  0

---

### Post by nothingspecial on 2012-05-14
*Thread moved to **Networking & Wireless**.*

---

