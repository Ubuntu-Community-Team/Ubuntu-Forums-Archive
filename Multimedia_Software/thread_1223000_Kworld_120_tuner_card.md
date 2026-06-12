---
title: "Kworld 120 tuner card"
date: 2009-07-25
forum: Multimedia Software
---

### Post by eidoslinux on 2009-07-25
i am having some problems getting this card to run. i have went though 3 different forms linux4tv, mythtv, and cant remember the other but i still have a no go. 

Now i am running Ubuntu 9.04 64 bit on AMD Phenom 9950 quad-core with kernel 2.6.28-13 generic and nvidia videocard. i have install the firmware as instructed and loaded blacklist-misc and rc.local and still mythtv can not runit. show code below.

```

$ lsmod | grep cx88
cx88_alsa              21128  1 
cx88_dvb               31748  1 
cx88_vp3054_i2c        11264  1 cx88_dvb
cx8802                 26116  1 cx88_dvb
videobuf_dvb           16388  1 cx88_dvb
cx88xx                 93228  3 cx88_alsa,cx88_dvb,cx8802
ir_common              61060  1 cx88xx
i2c_algo_bit           15364  2 cx88_vp3054_i2c,cx88xx
videobuf_dma_sg        22660  4 cx88_alsa,cx88_dvb,cx8802,cx88xx
videobuf_core          29572  4 cx8802,videobuf_dvb,cx88xx,videobuf_dma_sg
v4l2_common            29056  2 tuner,cx88xx
btcx_risc              13960  3 cx88_alsa,cx8802,cx88xx
tveeprom               23556  1 cx88xx
dvb_core              111792  2 cx88_dvb,videobuf_dvb
snd_pcm                99336  4 cx88_alsa,snd_hda_intel,snd_pcm_oss,snd_usb_audio
snd                    78792  22 cx88_alsa,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_usb_audio,snd_hwdep,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               50464  4 tuner,cx88xx,v4l2_common,pwc

```

```

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
modprobe cx88_dvb
modprobe cx88_alsa

exit 0

```

```
 
 GNU nano 2.0.9       File: /etc/modprobe.d/blacklist-misc                     

blacklist cx8800
blacklist cx8802
blacklist cx88_alsa
blacklist cx88_dvb

```

Anyway mythtv see the atsc 120 with samsung in the card list, but nothing shows with i do a bcast channel search or anything. Help would be great.

---

### Post by eidoslinux on 2009-07-25
oh if it means anything i also have a logitech webcam usb on the system to!

---

### Post by HappyFeet on 2009-07-25
Show us the output of 
```
lspci
```

---

### Post by eidoslinux on 2009-07-26
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
[   29.019493] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[   29.019496] cx88/2: registering cx8802 driver, type: dvb access: shared
[   29.019500] cx88[0]/2: cx2388x based DVB/ATSC card
[   29.306601] DVB: registering new adapter (cx88[0])
[   29.306604] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...

```

---

### Post by eidoslinux on 2009-07-26
i uploaded it i think i now have everything i can think of listed

---

### Post by eidoslinux on 2009-07-26
ok. i installed mythtv and it works on it. but still it does not work on tvtime or another software, so something is still not right! And as far as it running, it is at full screen on mythtv! i dont like to use that all the time.  with  mythtv how do i get it to see the svideo connector part.

---

