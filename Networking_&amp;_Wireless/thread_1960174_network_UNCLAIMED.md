---
title: "network UNCLAIMED"
date: 2012-04-16
forum: Networking &amp; Wireless
---

### Post by unregisted on 2012-04-16
hi !
i'm in use Ubuntu 11.04 and my wireless network card have some problem
i search over google and do manything but can't fix
please give me the way to fix it, tried :(
and there some information :

  *-network UNCLAIMED
       description: Network controller
       product: AR9485 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0100000-f017ffff memory:f0400000-f040ffff
@ubuntu:~$ lspci -nn | grep 0280
06:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)

netathr : driver installed
    device (168C:0032) present (alternate driver: ath9k)

@ubuntu:~$ lsmod
Module                  Size  Used by
ndiswrapper           183882  0 
nls_utf8               12493  0 
isofs                  39571  0 
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_intel          24113  2 
snd_hda_codec          90901  1 snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17322  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
fglrx                2434640  111 
snd                    55295  12 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               66851  0 
soundcore              12600  1 snd
videodev               75143  1 uvcvideo
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
sp5100_tco             13456  0 
video                  18951  0 
i2c_piix4              13095  0 
psmouse                73312  0 
k10temp                12951  0 
serio_raw              12990  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  1 
atl1c                  35753  0 
libahci                25548  1 ahci

thanks

---

### Post by chili555 on 2012-04-17
> my wireless network card have some problemYes, indeed! The native driver ath9k wouldn't drive your card so you installed the Windows driver with ndiswrapper. It refuses to drive your card, too! Let's see if we can figure out why. Please run and post:```
rfkill list all
dmesg | grep -i ath
dmesg | grep 06:00
```Thanks.

---

### Post by unregisted on 2012-04-17
now i switch to AMD64 ubuntu but nothing new 

sudo lshw -C network
[sudo] password for smash: 
  *-network               
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c1
       serial: 04:7d:7b:53:64:dd
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.1.113 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:40 memory:f0200000-f023ffff ioport:2000(size=128)

lspci -nn | grep 0280
06:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev ff)


rfkill list all ==> nothing happen


dmesg | grep ath
[    1.532901] device-mapper: multipath: version 1.2.0 loaded
[    1.532911] device-mapper: multipath round-robin: version 1.0.0 loaded
[    9.981857] ath9k 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.981878] ath9k 0000:06:00.0: setting latency timer to 64
[   10.034839] ath: address test failed addr: 0x00008000 - wr:0x00000000 != rd:0xffffffff
[   10.034896] ath: Unable to initialize hardware; initialization status: -19
[   10.034948] ath9k 0000:06:00.0: Failed to initialize device
[   10.035324] ath9k 0000:06:00.0: PCI INT A disabled

thanks !

---

### Post by chili555 on 2012-04-17
> [ 10.034839] ath: address test failed addr: 0x00008000 - wr:0x00000000 != rd:0xffffffff
[ 10.034896] ath: [COLOR="Red"]Unable to initialize hardware[/COLOR]; initialization status: -19
[ 10.034948] ath9k 0000:06:00.0: Failed to initialize deviceThat sort of sounds like the card is broken. I am Googling it now. 

Are you dual-booting? Does it work in Windows?

---

### Post by unregisted on 2012-04-17
yes ! it worked in Windows 7
i try i install driver in my Driver Disk but noluck

---

### Post by chili555 on 2012-04-17
What is your kernel version?```
uname -r
```When you open Synaptic Package manager, do you see linux-backport-modules-[COLOR="Red"]cw[/COLOR]? That is the Ubuntu version of the compat-wireless suite. If so, please install the generic version and reboot.

---

### Post by unregisted on 2012-04-17
my kernel version

2.6.38-8-generic

ya ! i see package linux-backports-modules-cw-........... is not installed
installing, hope ^^

---

### Post by unregisted on 2012-04-17
installed but noluck :(

---

### Post by chili555 on 2012-04-17
> **unregisted said:**
> installed but noluck :(Any clues here?```
dmesg | grep -i ath
```

---

### Post by unregisted on 2012-04-17
dmesg | grep -i ath
[    1.541651] device-mapper: multipath: version 1.2.0 loaded
[    1.541662] device-mapper: multipath round-robin: version 1.0.0 loaded
[   20.637432] ath9k 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.637453] ath9k 0000:06:00.0: setting latency timer to 64
[   20.690541] ath: address test failed addr: 0x00008000 - wr:0x00000000 != rd:0xffffffff
[   20.690597] ath: Unable to initialize hardware; initialization status: -19
[   20.690650] ath9k 0000:06:00.0: Failed to initialize device
[   20.693701] ath9k 0000:06:00.0: PCI INT A disabled

---

### Post by chili555 on 2012-04-17
The only further thing I can suggest is to download Ubuntu 12.04 and run the CD live and see if the device initializes. If so, I'd install it. If not, I am out of ideas. Sorry.

---

### Post by unregisted on 2012-04-18
thank you &#9829;

---

### Post by Lipunio on 2012-09-29
I have the same problem.  I have Ubuntu 12.04. Has anybody solution?


Edit:Try this, my wifi card started working after that.
sudo apt-get update; sudo apt-get install hwinfo grep rfkill; sudo lshw -C network; rfkill list; sudo iwlist scanning; cat /etc/network/interfaces; cat /etc/lsb-release; lspci -nn; lsusb; sudo lshw -short; uname -a; dmesg | egrep 'acx|at76|ath|b43|bcm|brcm|CX|eth|ipw|ireless|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|ound|p54|prism|rtl|rt2|rt3|rt5|rt6|rt7|usb|witch|wl';sudo dmidecode|egrep 'anufact|roduct|erial|elease'; iwconfig; cat /etc/modprobe.d/* | egrep 'acx|at76|ath|b43|bcm|brcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|wmi|witch|wl'; cat /var/lib/NetworkManager/NetworkManager.state; sudo hwinfo --netcard ; ps -aux|egrep 'wpa|icd|etwork'; sudo lsmod

---

