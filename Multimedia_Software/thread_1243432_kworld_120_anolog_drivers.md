---
title: "kworld 120 anolog drivers"
date: 2009-08-18
forum: Multimedia Software
---

### Post by eidoslinux on 2009-08-18
I am trying to get the analog drivers to work with the card but i am not having any luck, when i switch over the rc.local to list only cx8800 and cx88-alsa and restart ubuntu and then start mythtv for the card config, it says there was a error reading the card data.

Now i have no problems getting the card to run in digital, but i really need to have the svideo/composite port working and from my understanding it can only be used in anolog and not in digital. any help would be great.

System is Ubuntu 9.04 64bit , running nvidia vcard, amd x4 processor and 4gb of ram.
Here is my data with the digital drivers running.

```

$ lsmod | grep cx88
cx88_dvb               32772  0 
cx88_vp3054_i2c        11264  1 cx88_dvb
cx8802                 27012  1 cx88_dvb
cx88xx                 88104  2 cx88_dvb,cx8802
ir_common              56068  1 cx88xx
i2c_algo_bit           15364  2 cx88_vp3054_i2c,cx88xx
tveeprom               23428  1 cx88xx
btcx_risc              13960  2 cx8802,cx88xx
videobuf_dvb           16516  3 cx88_dvb,cx8802,cx88xx
videobuf_dma_sg        22660  3 cx88_dvb,cx8802,cx88xx
videobuf_core          29828  4 cx8802,cx88xx,videobuf_dvb,videobuf_dma_sg
dvb_core              106924  2 cx88_dvb,videobuf_dvb
videodev               45184  4 tuner,cx88xx,pwc,compat_ioctl32

```

```

GNU nano 2.0.9             File: /etc/rc.local                                

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
mv /etc/modprobe.d/blacklist-misc /root
modprobe cx88_dvb

cp /root/blacklist-misc /etc/modprobe.d


exit 0

```

```

GNU nano 2.0.9       File: /etc/modprobe.d/blacklist-misc                     

blacklist cx8800
blacklist cx8802
blacklist cx88_alsa
blacklist cx88_dvb


```

```
$ lspci
00:00.0 Host bridge: ATI Technologies Inc RD790 Northbridge only dual slot PCI-e_GFX and HT3 K8 part
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:09.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port E)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
03:06.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
03:06.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
03:06.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)

```

```

$ dmesg | grep -i dvb
[   33.782727] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   33.782730] cx88/2: registering cx8802 driver, type: dvb access: shared
[   33.782735] cx88[0]/2: cx2388x based DVB/ATSC card
[   33.964033] DVB: registering new adapter (cx88[0])
[   33.964035] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...

```

anyway like i said i have it working with the digital, but when i change it to try and geting it working on the anolog it does not happen! Help would be very nice!

---

