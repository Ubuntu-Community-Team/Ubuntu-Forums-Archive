---
title: "Broadcom driver and DKMS problem"
date: 2013-06-09
forum: Networking &amp; Wireless
---

### Post by MicoTheMailman on 2013-06-09
I am a relatively new Ubuntu user using Wubi on Microsoft XP on a Gateway netbook.
The wifi hasn't worked since I installed it (version 12.04). I have followed many "solutions" although none have worked yet.
I had given up and used only a wired connection to update occasionally but today after I updated a message informed me that the missing driver could now be installed. I clicked, entered the root password but it was unable to install due to package errors.
After trying to manually install it I found the problem, DKMS wasnt installed properly. I sudo installed that as well but needed "patch".

Any advice or help would be useful as the only other DKMS problems I have found are for VMBox, which coincidentally doesn't install either.

Thank you
Muchas Gracias
Danke
Dziekuje

---

### Post by Hadaka on 2013-06-09
Hi, lets take a look at what you have going on there..
please post the output of..
```
lspci -nnk | grep -iA3 net
lsmod
rfkill list
cat /etc/modules
```
thanks.

---

### Post by MicoTheMailman on 2013-06-10
here are my responses. One or two has been trimmed to what I thought was the important part but I can do it again if needed.
```

01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

Subsystem: Foxconn International, Inc. T77H106.00 Wireless Half-size Mini PCIe Card [105b:e01b]
Kernel driver in use: b43-pci-bridge
Kernel modules: ssb
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8132 Fast Ethernet [1969:1062] (rev c0)
Subsystem: Acer Incorporated [ALI] Device [1025:0241}
Kernel driver in use: atl1c
Kernel modules: atl1c


Module    size    Used by
ssb    50691    1 b43
 atl1c    36718    0

0:
phy
0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

1: acer-wireless: Wireless LAN
    Soft blocked: yes
 Hard blocked: no

```

Hope this helps you and thank you for helping me :)

---

### Post by Hadaka on 2013-06-10
Hi, yes I would like to see the full
printout of the commands i posted
and please put each output in its own
code tag.
thanks.

---

### Post by MicoTheMailman on 2013-06-15
Sorry about the delay; here we go.

lspci -nnk | grep -iA3 net
```

01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHy
  [14r4:4315] (rev 01)
            Subsystem: Foxconn International, Inc. T77H106.00 Wireless Half-size Mini PCIe Card [105b:e01b]
            Kernel driver in use: b43-pci-bridge
            Kernel modules: ssb
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8132 Fast Ethernet [1969:1062] (rev c0)
            Subsystem: Acer Incorporated [ALI] Device [1025:0241]
            Kernel driver in use: atl1c
            Kernel modules: atl1c

```

lsmod
```

Module                         Size   Used by
joydev                        17393   0
acer_wmi                    23612   0
sparse_keymap            13658   1 acer_wmi
snd_hda_codec_realtek 174313 1
snd_hda_intel              32719   3
snd_hda_codec          109562   2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep                 13276   1 snd_hda_codec
snd_pcm                    80916   2 snd_hda_intel,snd_hda_codec
psmouse                    86520   0
uvcvideo                    67203   0
videodev                    86588   1 uvcvideo
snd_seq_midi              13132   0
serio_raw                   13027   0
snd_rawmidi                25424  1 snd_seq_midi
acr4                          12473  2
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                     51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer                   28931  2 snd_pcm,snd_seq
snd_seq_device           14172  3 snd_seq_midi,snd_rawmidi,snd_seq
b43                          342758  0
mac80211                 436493  1 b43
i915                         428014  3
cfg80211                  178877  2 b43,mac80211
snd                           62218  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bcma                        25651   1 b43
drm_kms_helper          45466   1 i915
drm                         197641   2 i915,drm_kms_helper
rfcomm                      38139  0
i2c_algo_bit                13199  1 i915
bnep                         17830  2
bluetooth                 158479  10 rfcomm,bnep
parport_pc                 32114  0
ppdev                       12849  0
wmi                          18744  1 acer_wmi
soundcore                 14635  1  snd
snd_page_alloc           14108  2 snd_hda_intel,snd_pcm
mac_hid                    13077  0
video                        19115  1 i915
lp                             17455  0
parport                     40930   3 parport_pc,ppdev,lp
ssb                          50691  1 b43 

```

rfkill list
```

0: phy0: Wireless LAN
          Soft blocked: no
          Hard blocked: no
1: Acer-wireless: Wireless LAN
          Soft blocked: no
          Hard blocked: no

```

cat /etc/modules
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at book time, one per line. Lines beginning with '#' are ignored.

lp

```

Hope this is more helpful than the previous one. :)

---

### Post by Hadaka on 2013-06-15
Hi, thanks for the additional information.
 Please open a terminal then Copy and paste the following
one line at a time.
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -rfv b43
sudo modprobe -v b43
```
then post the output of..
```
dmesg | grep b43
```
Hopefully your wireless should be working.
thanks.

---

### Post by MicoTheMailman on 2013-06-15
Oh my goodness it worked!!!
:KS Thank you so much :D

and as you requested: the code output.
```

dmesg | grep b43

[    2.439877] b43-pci-bridge 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.439901] b43-pci-bridge 0000:01:00.0: setting latency timer to 64
[   24.361141] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   24.546782] Registered led device: b43-phy0::tx
[   24.546873] Registered led device: b43-phy0::rx
[   24.546972] Registered led device: b43-phy0::radio
[ 3729.458243] b43-pci-bridge 0000:01:00.0: PCI INT A disabled
[ 3729.872851] b43-pci-bridge 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 5121.068417] b43-pci-bridge 0000:01:00.0: PCI INT A disabled
[ 5136.850386] b43-pci-bridge 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 5136.850423] b43-pci-bridge 0000:01:00.0: setting latency timer to 64
[ 5137.236184] b43-phy1: Broadcom 4312 WLAN found (core revision 15)
[ 5137.308450] Registered led device: b43-phy1::tx
[ 5137.308557] Registered led device: b43-phy1::rx
[ 5137.308660] Registered led device: b43-phy1::radio
[ 5151.420192] b43-phy1: Loading firmware version 666.2 (2011-02-23 01:15:07)

```

also if it is not too much trouble, what was wrong with the wifi and how did you fix it?

---

### Post by Hadaka on 2013-06-15
Hey !...Glad it worked !
your wireless card
Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315]

behaves differently depending on the type of computer you have,your kernel,your ubuntu flavor
and i swear some times on the moon phase...alot of variables. but..always the b43 driver
so..you loaded..
1.  b43-fwcutter firmware-b43-installer...i think----  you also could have loaded..
2.  firmware-b43-lpphy-installer..but i have found more often than not since Ubuntu 12.04
3.  linux-firmware-nonfree...
all are b43 drivers..with different options,nonfree seems to have the best mix of options.

use this link to mark this thread SOLVED -> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
*Note edit your FIRST post of this thread to mark solved.
thanks.

---

