---
title: "1000HE RT2860 problem"
date: 2011-09-03
forum: Networking &amp; Wireless
---

### Post by Bedlore on 2011-09-03
Please help me in getting the wifi to work on my brothers netbook.  Below is some in details that may help:

I originally compiled as per [http://ubuntuforums.org/showthread.php?t=1476007](http://ubuntuforums.org/showthread.php?t=1476007) but it didn't help.


```
 
$ lspci -nn | grep 0280
01:00.0 Network controller [0280]: Ralink corp. RT2860 [1814:0781]

$ sudo lsmod | grep rt2
rt2860sta             494649  1 
crc_ccitt              12595  1 rt2860sta

$ tail -n2 /etc/modprobe.d/blacklist.conf
blacklist amd76x_edac
blacklist rt2800pci

$ modinfo rt2860sta
filename:       /lib/modules/2.6.38-11-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
version:        2.1.0.0
alias:          rt3090sta
license:        GPL
description:    RT2860/RT3090 Wireless Lan Linux Driver
author:         Jett Chen <jett_chen@ralinktech.com>
firmware:       rt3090.bin
firmware:       rt2860.bin
srcversion:     C22EE7282F9A519D7E9A764
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
 alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        crc-ccitt
staging:        Y
vermagic:       2.6.38-11-generic SMP mod_unload modversions 686 
parm:           mac:rt28xx: wireless mac addr (charp)
darren@darren-1000HE:~$ 
darren@darren-1000HE:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-78 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

darren@darren-1000HE:~$ dmesg | grep rt2
[   15.436630] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[   15.488928] rt2860 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   15.488999] rt2860 0000:01:00.0: setting latency timer to 64
[   17.556895] <==== rt28xx_init, Status=0
[   17.647456] <==== rt28xx_init, Status=0
[  289.582147] <==== rt28xx_init, Status=0
[  433.042045] <==== rt28xx_init, Status=0

$ locate rt2860
/lib/firmware/rt2860.bin
/lib/modules/2.6.38-11-generic/kernel/drivers/staging/rt2860
/lib/modules/2.6.38-11-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
/lib/modules/2.6.38-11-generic/kernel/drivers/staging/rt2860/rt2860sta.ko.dist
/lib/modules/2.6.38-8-generic/kernel/drivers/staging/rt2860
/lib/modules/2.6.38-8-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
/usr/src/linux-headers-2.6.38-11/drivers/staging/rt2860
/usr/src/linux-headers-2.6.38-11/drivers/staging/rt2860/Kconfig
/usr/src/linux-headers-2.6.38-11/drivers/staging/rt2860/Makefile
/usr/src/linux-headers-2.6.38-11-generic/include/config/rt2860.h


 
```

---

