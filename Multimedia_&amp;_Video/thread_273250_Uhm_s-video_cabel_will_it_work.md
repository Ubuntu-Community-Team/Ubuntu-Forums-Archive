---
title: "Uhm s-video cabel will it work?"
date: 2006-10-07
forum: Multimedia &amp; Video
---

### Post by haxer on 2006-10-07
Hello i have an theoretical question sorry for bad english but if i would plug in an s-video cabel in my graphic card s-video connection and run it trough scart cable to my tv will it work or do i have to compile? Donnu why im asking maybe becouse we are moving and i wants it to work when i try it later :)

---

### Post by Jose Catre-Vandis on 2006-10-07
This all depends on your graphics card and its capabilities, and assumes the Svideo port is "OUT" and not "IN" :D

Check through these howto threads to see if they shed any light on the subject for you

[http://www.ubuntuforums.org/showthread.php?t=85769&highlight=howto+twinview](http://www.ubuntuforums.org/showthread.php?t=85769&highlight=howto+twinview)

[http://www.ubuntuforums.org/showthread.php?t=23628&highlight=howto+nvidia](http://www.ubuntuforums.org/showthread.php?t=23628&highlight=howto+nvidia)

[http://www.ubuntuforums.org/showthread.php?t=29510&highlight=howto+nvidia](http://www.ubuntuforums.org/showthread.php?t=29510&highlight=howto+nvidia)

[http://www.ubuntuforums.org/showthread.php?t=215763&highlight=howto+tv+out](http://www.ubuntuforums.org/showthread.php?t=215763&highlight=howto+tv+out)

[http://www.ubuntuforums.org/showthread.php?t=98456&highlight=nvidia](http://www.ubuntuforums.org/showthread.php?t=98456&highlight=nvidia)

---

### Post by haxer on 2006-10-07
Hmm. my card supports the most i figured out but some guy told me that i would work perfectly but will it really do that and what would happend if it deosnt but he sayd that if it deosnt work ill have to restart my computer with the s-video cable inserted in graphic card and then it would wotk fine S: ?

---

### Post by Jose Catre-Vandis on 2006-10-08
I'll need a bit more help than this. What is your graphics card and what ports do you have on the back

```
 lspci -v
```

should give you some info about it

---

### Post by haxer on 2006-10-08
I get this out put and i got an N6600le silencer graphic card :)


0000:00:00.0 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8199
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <available only to root>

0000:00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8199
        Flags: bus master, medium devsel, latency 0

0000:00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8199
        Flags: bus master, medium devsel, latency 0

0000:00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
        Flags: bus master, medium devsel, latency 0

0000:00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8199
        Flags: bus master, medium devsel, latency 0

0000:00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller (prog-if 20 [IO(X)-APIC])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8199
        Flags: bus master, fast devsel, latency 0

0000:00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8199
        Flags: bus master, medium devsel, latency 0

0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Capabilities: <available only to root>

0000:00:02.0 PCI bridge: VIA Technologies, Inc. PT890 PCI to PCI Bridge Controller (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: d5e00000-dfefffff
        Prefetchable memory behind bridge: b5d00000-d5cfffff
        Capabilities: <available only to root>

0000:00:0d.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 80ee
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 193
        Memory at dffc0000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at dc00 [size=64]
        Capabilities: <available only to root>

0000:00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 80e9
        Flags: bus master, medium devsel, latency 64, IRQ 193
        I/O ports at ec00 [size=8]
        I/O ports at e880 [size=4]
        I/O ports at e800 [size=8]
        I/O ports at e480 [size=4]
        I/O ports at e400 [size=16]
        I/O ports at e000 [size=256]
        Capabilities: <available only to root>

0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 80e9
        Flags: bus master, medium devsel, latency 32, IRQ 193
        I/O ports at fc00 [size=16]
        Capabilities: <available only to root>

0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 64, IRQ 201
        I/O ports at d880 [size=32]
        Capabilities: <available only to root>

0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 64, IRQ 201
        I/O ports at d800 [size=32]
        Capabilities: <available only to root>

0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 64, IRQ 201
        I/O ports at d480 [size=32]
        Capabilities: <available only to root>

0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 64, IRQ 201
        I/O ports at d400 [size=32]
        Capabilities: <available only to root>

0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
        Subsystem: VIA Technologies, Inc. USB 2.0
        Flags: bus master, medium devsel, latency 64, IRQ 201
        Memory at dffff800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
        Subsystem: VIA Technologies, Inc. DFI KT600-AL Motherboard
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <available only to root>

0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 810d
        Flags: medium devsel, IRQ 217
        I/O ports at d000 [size=256]
        Capabilities: <available only to root>

0000:02:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0142 (rev a2) (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 81dc
        Flags: bus master, fast devsel, latency 0, IRQ 209
        Memory at d8000000 (32-bit, non-prefetchable) [size=64M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at de000000 (64-bit, non-prefetchable) [size=16M]
        Expansion ROM at dfee0000 [disabled] [size=128K]
        Capabilities: <available only to root>

and on root i get this 

root@haxer:/home/oem# 0000:00:00.0 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
bash: 0000:00:00.0: command not found
troller
        Flags: bus master, medium devsel, latency 64, IRQ 2root@haxer:/home/oem#199      Subsystem: ASUSTeK Computer Inc.: Unknown device 8
bash: Subsystem:: command not found
01
        I/O ports at d480 [size=32]
root@haxer:/home/oem#         Flags: bus master, 66MHz, medium devsel, latency 8bash: Flags:: command not found
available only to root>

0000:00:10.3 USB Controller: VIA Troot@haxer:/home/oem#         Memory at f000008M](32-bit, prefetchable) [size=12
bash: syntax error near unexpected token `('
echnologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (
root@haxer:/home/oem#         Capabilities: <available only to root>
bash: syntax error near unexpected token `newline'
        Subsystem: VIA Technologies, Inc. VT82
root@haxer:/home/oem#

root@haxer:/home/oem# 0000:00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
bash: 0000:00:00.1: command not found
        I/O ports at d400 [size=32]
        Capabilities: <availabroot@haxer:/home/oem#         Subsystem: ASUSTeK C199uter Inc.: Unknown device 8
bash: Subsystem:: command not found
le only to root>

0000:00:10.4 USB Controller: VIA Technologieroot@haxer:/home/oem#         Flags: bus master, medium devsel, latency 0
bash: Flags:: command not found
s, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
       root@haxer:/home/oem#

root@haxer:/home/oem# 0000:00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
bash: 0000:00:00.2: command not found
        Flags: bus master, medium devsel, latency 64, IRQ 201
    root@haxer:/home/oem#         Subsystem: ASUSTeK Computer Inc.: Unknown devi1998
bash: Subsystem:: command not found
    Memory at dffff800 (32-bit, non-prefetchable) [size=256]
 root@haxer:/home/oem#         Flags: bus master, medium devsel, latency 0
bash: Flags:: command not found
       Capabilities: <available only to root>

0000:root@haxer:/home/oem#
0
root@haxer:/home/oem# 0000:00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
bash: 0000:00:00.3: command not found
        Subsystem: VIA Technologies, Inc. DFI KT600-AL Motherboard
root@haxer:/home/oem#         Flags: bus master, medium devsel, latency 0
bash: Flags:: command not found
        Flags: bus master, stepping, medium devsel,
root@haxer:/home/oem#

root@haxer:/home/oem# 0000:00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
bash: 0000:00:00.4: command not found

0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. root@haxer:/hom199em#         Subsystem: ASUSTeK Computer Inc.: Unknown device 8
bash: Subsystem:: command not found
VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
        Subsroot@haxer:/home/oem#         Flags: bus master, medium devsel, latency 0
bash: Flags:: command not found
ystem: ASUSTeK Computer Inc.: Unknown device 810d
  root@haxer:/home/oem#

root@haxer:/home/oem# 0000:00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller (prog-if 20 [IO(X)-APIC])
bash: syntax error near unexpected token `('
        I/O ports at d000 [size=256]
        Capabilities: <available only to root>

0000:02:00.0 VGA root@haxer:/home/oem#         Subsystem: ASUSTeK Computer Inc.:199known device 8
bash: Subsystem:: command not found
compatible controller: nVidia Corporation: Unknown device 0142
root@haxer:/home/oem#         Flags: bus master, fast devsel, latency 0
bash: Flags:: command not found
        Subsystem: ASUSTeK Computer Inc.: Unknown
root@haxer:/home/oem#

root@haxer:/home/oem# 0000:00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
bash: 0000:00:00.7: command not found
        Memory at d8000000 (32-bit, non-prefetchable) [size=64M]
 root@haxer:/home/oem#         Subsystem: ASUSTeK Computer Inc.: Unknown device 199
bash: Subsystem:: command not found
       Memory at c0000000 (64-bit, prefetchable) [size=256M]
 root@haxer:/home/oem#         Flags: bus master, medium devsel, latency 0
bash: Flags:: command not found
       Memory at de000000 (64-bit, non-prefetchable)
root@haxer:/home/oem#

root@haxer:/home/oem# 0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
bash: syntax error near unexpected token `('
        Capabilities: <available only to root>
root@haxer:/home/oem#         Flags: bus master, 66MHz, medium devsel, latency 0bash: Flags:: command not found
root@haxer:/home/oem#         Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
bash: Bus:: command not found
root@haxer:/home/oem#         Capabilities: <available only to root>
bash: syntax error near unexpected token `newline'
root@haxer:/home/oem#
root@haxer:/home/oem# 0000:00:02.0 PCI bridge: VIA Technologies, Inc. PT890 PCI to PCI Bridge Controller (prog-if 00 [Normal decode])
bash: syntax error near unexpected token `('
root@haxer:/home/oem#         Flags: bus master, fast devsel, latency 0
bash: Flags:: command not found
root@haxer:/home/oem#         Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
bash: Bus:: command not found
root@haxer:/home/oem#         Memory behind bridge: d5e00000-dfefffff
bash: Memory: command not found
root@haxer:/home/oem#         Prefetchable memory behind bridge: b5d00000-d5cfffff
bash: Prefetchable: command not found
root@haxer:/home/oem#         Capabilities: <available only to root>
bash: syntax error near unexpected token `newline'
root@haxer:/home/oem#
root@haxer:/home/oem# 0000:00:0d.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
bash: syntax error near unexpected token `('
root@haxer:/home/oem#         Subsystem: ASUSTeK Computer Inc.: Unknown device 80ee
bash: Subsystem:: command not found
root@haxer:/home/oem#         Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 193
bash: Flags:: command not found
root@haxer:/home/oem#         Memory at dffc0000 (32-bit, non-prefetchable) [size=128K]
bash: syntax error near unexpected token `('
root@haxer:/home/oem#         I/O ports at dc00 [size=64]
bash: I/O: No such file or directory
root@haxer:/home/oem#         Capabilities: <available only to root>
bash: syntax error near unexpected token `newline'
root@haxer:/home/oem#
root@haxer:/home/oem# 0000:00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
bash: syntax error near unexpected token `('
root@haxer:/home/oem#         Subsystem: ASUSTeK Computer Inc.: Unknown device 80e9
bash: Subsystem:: command not found
root@haxer:/home/oem#         Flags: bus master, medium devsel, latency 64, IRQ 193
bash: Flags:: command not found
root@haxer:/home/oem#         I/O ports at ec00 [size=8]
bash: I/O: No such file or directory
root@haxer:/home/oem#         I/O ports at e880 [size=4]
bash: I/O: No such file or directory
root@haxer:/home/oem#         I/O ports at e800 [size=8]
bash: I/O: No such file or directory
root@haxer:/home/oem#         I/O ports at e480 [size=4]
bash: I/O: No such file or directory
root@haxer:/home/oem#         I/O ports at e400 [size=16]
bash: I/O: No such file or directory
root@haxer:/home/oem#         I/O ports at e000 [size=256]
bash: I/O: No such file or directory
root@haxer:/home/oem#         Capabilities: <available only to root>
bash: syntax error near unexpected token `newline'
root@haxer:/home/oem#
root@haxer:/home/oem# 0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
bash: syntax error near unexpected token `('
root@haxer:/home/oem#         Subsystem: ASUSTeK Computer Inc.: Unknown device 80e9
bash: Subsystem:: command not found
root@haxer:/home/oem#         Flags: bus master, medium devsel, latency 32, IRQ 193
bash: Flags:: command not found
root@haxer:/home/oem#         I/O ports at fc00 [size=16]
bash: I/O: No such file or directory
root@haxer:/home/oem#         Capabilities: <available only to root>
bash: syntax error near unexpected token `newline'
root@haxer:/home/oem#
root@haxer:/home/oem# 0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
bash: syntax error near unexpected token `('
root@haxer:/home/oem#         Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
bash: Subsystem:: command not found
root@haxer:/home/oem#         Flags: bus master, medium devsel, latency 64, IRQ 201
bash: Flags:: command not found
root@haxer:/home/oem#         I/O ports at d880 [size=32]
bash: I/O: No such file or directory
root@haxer:/home/oem#         Capabilities: <available only to root>
bash: syntax error near unexpected token `newline'
root@haxer:/home/oem#
root@haxer:/home/oem# 0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
bash: syntax error near unexpected token `('
root@haxer:/home/oem#         Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
bash: Subsystem:: command not found
root@haxer:/home/oem#         Flags: bus master, medium devsel, latency 64, IRQ 201
bash: Flags:: command not found
root@haxer:/home/oem#         I/O ports at d800 [size=32]
bash: I/O: No such file or directory
root@haxer:/home/oem#         Capabilities: <available only to root>
bash: syntax error near unexpected token `newline'
root@haxer:/home/oem#
root@haxer:/home/oem# 0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
bash: syntax error near unexpected token `('
root@haxer:/home/oem#         Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
bash: Subsystem:: command not found
root@haxer:/home/oem#         Flags: bus master, medium devsel, latency 64, IRQ 201
bash: Flags:: command not found
root@haxer:/home/oem#         I/O ports at d480 [size=32]
bash: I/O: No such file or directory
root@haxer:/home/oem#         Capabilities: <available only to root>
bash: syntax error near unexpected token `newline'
root@haxer:/home/oem#
root@haxer:/home/oem# 0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (
bash: syntax error near unexpected token `('
root@haxer:/home/oem#         Subsystem: VIA Technologies, Inc. VT82
bash: Subsystem:: command not found
root@haxer:/home/oem#
root@haxer:/home/oem#         I/O ports at d400 [size=32]
bash: I/O: No such file or directory
root@haxer:/home/oem#         Capabilities: <available only to root>
bash: syntax error near unexpected token `newline'
root@haxer:/home/oem#
root@haxer:/home/oem# 0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
bash: syntax error near unexpected token `('
root@haxer:/home/oem#
root@haxer:/home/oem#         Flags: bus master, medium devsel, latency 64, IRQ 201
bash: Flags:: command not found
root@haxer:/home/oem#         Memory at dffff800 (32-bit, non-prefetchable) [size=256]
bash: syntax error near unexpected token `('
root@haxer:/home/oem#         Capabilities: <available only to root>
bash: syntax error near unexpected token `newline'
root@haxer:/home/oem#
root@haxer:/home/oem# 0000:0
bash: 0000:0: command not found
root@haxer:/home/oem#         Subsystem: VIA Technologies, Inc. DFI KT600-AL Motherboard
bash: Subsystem:: command not found
root@haxer:/home/oem#         Flags: bus master, stepping, medium devsel,
bash: Flags:: command not found
root@haxer:/home/oem#
root@haxer:/home/oem#
root@haxer:/home/oem# 0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
bash: syntax error near unexpected token `('
root@haxer:/home/oem#         Subsystem: ASUSTeK Computer Inc.: Unknown device 810d
bash: Subsystem:: command not found
root@haxer:/home/oem#
root@haxer:/home/oem#         I/O ports at d000 [size=256]
bash: I/O: No such file or directory
root@haxer:/home/oem#         Capabilities: <available only to root>
bash: syntax error near unexpected token `newline'
root@haxer:/home/oem#
root@haxer:/home/oem# 0000:02:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0142
bash: 0000:02:00.0: command not found
root@haxer:/home/oem#         Subsystem: ASUSTeK Computer Inc.: Unknown
bash: Subsystem:: command not found
root@haxer:/home/oem#
root@haxer:/home/oem#         Memory at d8000000 (32-bit, non-prefetchable) [size=64M]
bash: syntax error near unexpected token `('
root@haxer:/home/oem#         Memory at c0000000 (64-bit, prefetchable) [size=256M]
bash: syntax error near unexpected token `('
root@haxer:/home/oem#         Memory at de000000 (64-bit, non-prefetchable)
bash: syntax error near unexpected token `('
root@haxer:/home/oem#
root@haxer:/home/oem#         Capabilities: <available only to root>
bash: syntax error near unexpected token `newline'

---

### Post by Jose Catre-Vandis on 2006-10-09
0000:02:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0142 (rev a2) (prog-if 00 [VGA])
Subsystem: ASUSTeK Computer Inc.: Unknown device 81dc
Flags: bus master, fast devsel, latency 0, IRQ 209
Memory at d8000000 (32-bit, non-prefetchable) [size=64M]
Memory at c0000000 (64-bit, prefetchable) [size=256M]
Memory at de000000 (64-bit, non-prefetchable) [size=16M]
Expansion ROM at dfee0000 [disabled] [size=128K]
Capabilities: <available only to root>

seems to indicate you have an nvidia card of sorts.

Have you installed the nvidia drivers or are you just working on setup install.

Have a look in your /etc/X11/xorg.conf file and report back ( I would guess you are using the "nv" driver?)

Then search the forum for nvidia drivers installation

---

