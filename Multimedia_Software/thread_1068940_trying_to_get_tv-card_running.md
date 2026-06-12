---
title: "trying to get tv-card running"
date: 2009-02-13
forum: Multimedia Software
---

### Post by aeltester on 2009-02-13
Hey guys,

I'm trying to get my old pinnacle TV-Card to run.

lspci:
```

$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:01.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
05:01.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
05:01.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
05:02.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)

```

dmesg:
```

$ dmesg | grep bttv
[   13.130170] bttv: driver version 0.9.17 loaded
[   13.130172] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   13.130216] bttv: Bt8xx card found (0).
[   13.130225] bttv 0000:05:02.0: can't derive routing for PCI INT ?
[   13.130226] bttv 0000:05:02.0: PCI INT ?: no GSI
[   13.130235] bttv0: Bt878 (rev 17) at 0000:05:02.0, irq: 255, latency: 32, mmio: 0xe0000000
[   13.130492] bttv0: detected: Pinnacle PCTV [card=39], PCI subsystem ID is 11bd:0012
[   13.130494] bttv0: using: Pinnacle PCTV Studio/Rave [card=39,autodetected]
[   13.130497] bttv0: can't get IRQ 255
[   13.130513] bttv: probe of 0000:05:02.0 failed with error -22

```

zapping says it can't find /dev/video0.
tvtime just doesn't give me any option for the input.

what can I do?

thanks in advance

:P

---

### Post by xzero1 on 2009-02-13
Tvtime has options if run from the  command line.

---

### Post by wolfen69 on 2009-02-13
see [this]("http://www.linuxtv.org/wiki/index.php/Bttv_devices_(bt848%2C_bt878)").

---

### Post by aeltester on 2009-02-13
I added the line

```

options bttv card=39 tuner=33

```

to /etc/modules
and now get this:

```

$ dmesg | grep bttv
[   11.418328] bttv: driver version 0.9.17 loaded
[   11.418330] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   11.419570] bttv: Bt8xx card found (0).
[   11.419579] bttv 0000:05:02.0: can't derive routing for PCI INT ?
[   11.419580] bttv 0000:05:02.0: PCI INT ?: no GSI
[   11.419589] bttv0: Bt878 (rev 17) at 0000:05:02.0, irq: 255, latency: 32, mmio: 0xe0000000
[   11.419597] bttv0: detected: Pinnacle PCTV [card=39], PCI subsystem ID is 11bd:0012
[   11.419599] bttv0: using: Pinnacle PCTV Studio/Rave [card=39,autodetected]
[   11.419601] bttv0: can't get IRQ 255
[   11.419608] bttv: probe of 0000:05:02.0 failed with error -22

```

PS: this tip is from the page that was recommended.
I do not think that it is a problem of tvtime, rather one of the driver.

thanks
:P

---

### Post by cariboo on 2009-02-13
If you don't have the correct card number TVtime won't give you the options to change inputs. See screenshot.

I'm not sure if this will help, but I have to add this script to /etc/modprobe.d to get my tuner card to work:

```
alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 card=17
```

You will have to change the saa7134 to the driver for your card and the card number.

Jim

---

### Post by aeltester on 2009-02-13
> **cariboo907 said:**
> If you don't have the correct card number TVtime won't give you the options to change inputs. See screenshot.

I'm not sure if this will help, but I have to add this script to /etc/modprobe.d to get my tuner card to work:

```
alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 card=17
```

You will have to change the saa7134 to the driver for your card and the card number.

Jim

Hey, thanks for sharing.

how do I find out which char-major-# I have to put in there?

Or is it just
```

alias char-major-81 video0
alias char-major-81-0 Bt878
options Bt878 card=39

```
?

hf
:P

---

### Post by aeltester on 2009-02-17
Ok I put the suggested into /etc/modprobe.d/aliases which didn't change anything.

thanks anyway

---

### Post by cariboo on 2009-02-17
This line:

> alias char-major-81 video0


SHould be 

```
alias char-major-81 videodev

```

as you don't know what the video device will be if you have any other v4l devices, I have a webcam also.

Jim

---

### Post by aeltester on 2009-02-19
still, this is what I get:

```

$ dmesg | grep bttv
[   11.199235] bttv: driver version 0.9.17 loaded
[   11.199237] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   11.199698] bttv: Bt8xx card found (0).
[   11.199707] bttv 0000:05:02.0: can't derive routing for PCI INT ?
[   11.199708] bttv 0000:05:02.0: PCI INT ?: no GSI
[   11.199716] bttv0: Bt878 (rev 17) at 0000:05:02.0, irq: 255, latency: 32, mmio: 0xe0000000
[   11.199724] bttv0: detected: Pinnacle PCTV [card=39], PCI subsystem ID is 11bd:0012
[   11.199726] bttv0: using: Pinnacle PCTV Studio/Rave [card=39,insmod option]
[   11.199727] bttv0: can't get IRQ 255
[   11.199735] bttv: probe of 0000:05:02.0 failed with error -22

```

I don't even understand what it's missing!

thanks for your help again.

hf
:P

---

