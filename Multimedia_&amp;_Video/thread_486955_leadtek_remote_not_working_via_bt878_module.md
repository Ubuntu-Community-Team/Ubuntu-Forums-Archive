---
title: "leadtek remote not working via bt878 module?"
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by deadcabbit on 2007-06-28
I have a **Leadtek Winfast TV 2000 XP RM** card, which seems to be working, but the remote is dead silent (cat /dev/input/eventX). Could anyone make this remote work without extreme efforts (like recompiling the kernel?).

**lspci | grep Brook**
```
01:08.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:08.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
```

**in /etc/modules:**
```
options bttv card=34 tuner=38
```

**dmesg | grep bttv**
```
[ 6035.924000] bttv: driver version 0.9.16 loaded
[ 6035.924000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[ 6035.924000] bttv: Bt8xx card found (0).
[ 6035.924000] bttv0: Bt878 (rev 17) at 0000:01:08.0, irq: 20, latency: 32, mmio: 0xbffff000
[ 6035.924000] bttv0: detected: Leadtek TV 2000 XP [card=34], PCI subsystem ID is 107d:6609
[ 6035.924000] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,insmod option]
[ 6035.924000] bttv0: gpio: en=00000000, out=00000000 in=003ff102 [init]
[ 6035.932000] bttv0: using tuner=38
[ 6035.932000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[ 6035.932000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[ 6035.932000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[ 6035.932000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[ 6035.964000] bttv0: registered device video0
[ 6035.964000] bttv0: registered device vbi0
[ 6035.964000] bttv0: registered device radio0
[ 6035.968000] bttv0: PLL: 28636363 => 35468950 . ok
[ 6036.012000] input: bttv IR (card=34) as /class/input/input8
```

**cat /proc/bus/input/devices**
```
I: Bus=0001 Vendor=107d Product=6609 Version=0001
N: Name="bttv IR (card=34)"
P: Phys=pci-0000:01:08.0/ir0
S: Sysfs=/class/input/input8
H: Handlers=kbd event2 
B: EV=100003
B: KEY=10afc336 2150a48 0 0 0 404 80010000 190 4801 1e0000 4400 100000 10000ffc
```

**cat /dev/input/event2**
NOTHING :(

Am I missing something here? Shouldn't I see something by catting the device node? Last time I did something similar was on Gentoo, but now I don't want to compile everything, especially with the new bttv module handling ir events.

---

### Post by mvfpoa on 2007-07-04
same problem on cx8800. Used to work on edgy. :(
xev doesn't show anything.

dmesg
```
input: cx88 IR (PixelView PlayTV Ultra as /class/input/input2
```

cat /proc/bus/input/devices
```
I: Bus=0001 Vendor=14f1 Product=8800 Version=0001
N: Name="cx88 IR (PixelView PlayTV Ultra"
P: Phys=pci-0000:00:0b.0/ir0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2 
B: EV=100003
B: KEY=2c0814 100004 0 0 0 4 2008000 2090 2001 1e0000 4400 0 ffc

```

---

