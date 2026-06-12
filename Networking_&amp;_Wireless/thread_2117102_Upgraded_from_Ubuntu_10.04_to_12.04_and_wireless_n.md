---
title: "Upgraded from Ubuntu 10.04 to 12.04 and wireless networking stopped working"
date: 2013-02-17
forum: Networking &amp; Wireless
---

### Post by mpinegrove on 2013-02-17
[INDENT][/INDENT]Hello, last night I made the upgrade from 10.04 to 12.04 on my personal computer and the networking failed.  I had tried several things but cannot seem to get it to work.  When it boots it says "Waiting for network configuration..." Then "waiting up to 60 more seconds for network configuration..."
When it does boot there is no network symbol in the menu bar.  If I go to system settings and network it says "The system network services are not compatible with this version"???
I have a 686 Intel in a T43IBM Thinkpad, the internal wireless is set to hidden in the BIOS and I am using a TP-Link USB wireless adapter for greater range and speed model TL-WN822N. 
Everything worked fine on the old 10.04 operating system, I need some guidance and I can only contact this forum through my smart phone as the computer has no Internet.
I have done a couple of upgrades over time so I am familiar with how to get commands to work but I am not very literate beyond that in Ubuntu.
Thanks,
Mark

---

### Post by tevans555 on 2013-02-17
I have been having a similar problem. However, I have a 2008 macbook pro 4,1. Check out this website. It might help you. I haven't been able to get it to work for me, but it seems like it has worked for others.

[http://askubuntu.com/questions/205670/wifi-problem-after-ubuntu-12-10-update](http://askubuntu.com/questions/205670/wifi-problem-after-ubuntu-12-10-update)

---

### Post by mpinegrove on 2013-02-17
Thanks, I looked through the page, but it seems like all my networking might be disabled.  When I run sudo lshw -C networking the following is what I get.  Also the light on my USB wireless usually comes on right away and now it doesn't as if it is not talking, USB port does operate other devices like mouse.

```
family@family-laptop:~$ sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 11
       serial: 00:15:58:29:de:2c
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 firmware=5751m-v3.46a latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:b0200000-b020ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       bus info: usb@3:2.2
       logical name: eth1
       serial: c2:9f:42:dd:a9:63
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ipheth link=no multicast=yes
```

---

### Post by praseodym on 2013-02-18
Open the following file:
```

gksu gedit /etc/network/interfaces
```
remove anything except```

auto lo
iface lo inet loopback
```
Save, close the editor and reboot.

---

### Post by mpinegrove on 2013-02-18
Thanks that moves things forward slightly.  I now have a network button on the menu bar  but I have only wired as an option.  I can also use my smartphone as a wired connection so I can now connect to the internet.  How can I get it enable and recognize my USB wireless adapter?
Thanks,
Mark

---

### Post by praseodym on 2013-02-19
Please show
```

lsusb
rfkill list
lsmod
iwconfig
```

---

### Post by mpinegrove on 2013-02-19
family@family-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0cf3:7015 Atheros Communications, Inc. TP-Link TL-WN821N v3 802.11n [Atheros AR7010+AR9287]
Bus 003 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 004 Device 002: ID 0a5c:201e Broadcom Corp. IBM Integrated Bluetooth IV
Bus 003 Device 003: ID 046d:c510 Logitech, Inc. Cordless Mouse
Bus 003 Device 004: ID 05ac:12a0 Apple, Inc. 
family@family-laptop:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
family@family-laptop:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39553  1 
dm_crypt               22528  0 
ipheth                 13278  0 
joydev                 17393  0 
pcmcia                 39826  0 
thinkpad_acpi          73942  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_intel8x0           33455  2 
snd_ac97_codec        110213  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_intel8x0,snd_ac97_codec
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_seq,snd_pcm
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                96718  0 
serio_raw              13027  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
snd                    62218  12 thinkpad_acpi,snd_rawmidi,snd_intel8x0,snd_ac97_codec,snd_seq,snd_pcm,snd_timer,snd_seq_device
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
btusb                  17948  2 
nsc_ircc               23240  0 
irda                  185517  1 nsc_ircc
soundcore              14635  1 snd
nvram                  14029  1 thinkpad_acpi
rfcomm                 38139  12 
bnep                   17830  2 
ppdev                  12849  0 
crc_ccitt              12627  1 irda
parport_pc             32114  1 
bluetooth             158479  23 btusb,rfcomm,bnep
binfmt_misc            17292  1 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41937  0 
hid                    77428  1 usbhid
radeon                733824  3 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197641  5 radeon,ttm,drm_kms_helper
tg3                   137273  0 
i2c_algo_bit           13199  1 radeon
video                  19068  0 
floppy                 60184  0 
family@family-laptop:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.

---

### Post by praseodym on 2013-02-19
I am using the same stick, module "ath9k_htc":
```

sudo modprobe ath9k_htc
```
Replug the stick

---

### Post by mpinegrove on 2013-02-19
Thank you so much.
Such an easy solution when you know it, I didn't even have to replug the stick, it just started to work immediately and connected.
Thanks again
Mark

---

