---
title: "Video drivers"
date: 2006-08-18
forum: Multimedia &amp; Video
---

### Post by selfmade on 2006-08-18
im a n00b. don't rem,ember what i did, but video has been sketchy last few days. lag in games, on websites, etc. i dont know what video card i have, how do i figure that out, how do i update drivers, fix lagging?

ot: also, anyone know where gaim log files are stored? i cant find the logs for past conversations, in some cases cant do by screenname cause they were chats....

much thanks.

---

### Post by tseliot on 2006-08-18
post the output of this command:
```
lspci -v
```

---

### Post by selfmade on 2006-08-20
> **tseliot said:**
> post the output of this command:
```
lspci -v
```
ubuntu@ubuntu:~$ lspci -v
0000:00:00.0 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
        Subsystem: ASUSTeK Computer Inc.: Unknown device 0314
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:00:00.1 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
        Subsystem: ASUSTeK Computer Inc.: Unknown device 1314
        Flags: bus master, medium devsel, latency 0

0000:00:00.2 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
        Subsystem: ASUSTeK Computer Inc.: Unknown device 2314
        Flags: bus master, medium devsel, latency 0

0000:00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
        Flags: bus master, medium devsel, latency 0

0000:00:00.4 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
        Subsystem: ASUSTeK Computer Inc.: Unknown device 4314
        Flags: bus master, medium devsel, latency 0

0000:00:00.7 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
        Subsystem: ASUSTeK Computer Inc.: Unknown device 7314
        Flags: bus master, medium devsel, latency 0

0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: fca00000-feafffff
        Prefetchable memory behind bridge: eff00000-f7efffff
        Secondary status: SERR
        Capabilities: <available only to root>

0000:00:0b.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 86)
        Subsystem: D-Link System Inc: Unknown device 1406
        Flags: bus master, medium devsel, latency 32, IRQ 185
        I/O ports at c400 [size=256]
        Memory at febff400 (32-bit, non-prefetchable) [size=256]
        Expansion ROM at 20000000 [disabled] [size=64K]
        Capabilities: <available only to root>

0000:00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 3149
        Flags: bus master, medium devsel, latency 32, IRQ 169
        I/O ports at d880 [size=8]
        I/O ports at d800 [size=4]
        I/O ports at d480 [size=8]
        I/O ports at d400 [size=4]
        I/O ports at d080 [size=16]
        I/O ports at c800 [size=256]
        Capabilities: <available only to root>

0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 0571
        Flags: bus master, medium devsel, latency 32, IRQ 169
        I/O ports at fc00 [size=16]
        Capabilities: <available only to root>

0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 3038
        Flags: bus master, medium devsel, latency 32, IRQ 177
        I/O ports at dc00 [size=32]
        Capabilities: <available only to root>

0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 3038
        Flags: bus master, medium devsel, latency 32, IRQ 177
        I/O ports at e000 [size=32]
        Capabilities: <available only to root>

0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 3038
        Flags: bus master, medium devsel, latency 32, IRQ 177
        I/O ports at e080 [size=32]
        Capabilities: <available only to root>

0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 3038
        Flags: bus master, medium devsel, latency 32, IRQ 177
        I/O ports at ec00 [size=32]
        Capabilities: <available only to root>

0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 3104
        Flags: bus master, medium devsel, latency 32, IRQ 177
        Memory at febff800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
        Subsystem: ASUSTeK Computer Inc.: Unknown device 3227
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <available only to root>

0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8198
        Flags: medium devsel, IRQ 201
        I/O ports at e400 [size=256]
        Capabilities: <available only to root>

0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 80ff
        Flags: bus master, medium devsel, latency 32, IRQ 193
        I/O ports at e800 [size=256]
        Memory at febffc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:01:00.0 VGA compatible controller: VIA Technologies, Inc.: Unknown device 3344 (rev 01) (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 3344
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 10
        Memory at f0000000 (32-bit, prefetchable) [size=64M]
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Expansion ROM at feaf0000 [disabled] [size=64K]
        Capabilities: <available only to root>

---

### Post by tseliot on 2006-08-21
Your graphic card is a VIA card.

Try this:
```
sudo apt-get install xserver-xorg-driver-via
```

Then configure the Xserver:
```
sudo dpkg-reconfigure xserver-xorg
```

and select the "via" driver. Press ENTER whenever you don't know the answer to a question.

Then log out and press CTRL+ALT+Backspace

---

### Post by selfmade on 2006-08-22
ctrl+alt+backspace = doom. xserver had been disable b/c improperly configured...
on boot: PCMCIA....failed
how do i go back to old config file?

---

### Post by tseliot on 2006-08-22
Try with:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by selfmade on 2006-08-22
no dice. xserver error: no screens

---

### Post by tseliot on 2006-08-22
Have a look at this thread:
[http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)

---

