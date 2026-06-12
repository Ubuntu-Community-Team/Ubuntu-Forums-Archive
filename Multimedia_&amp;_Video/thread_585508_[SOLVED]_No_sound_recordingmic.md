---
title: "[SOLVED] No sound recording/mic"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by yang on 2007-10-21
I can't record any sound in gnome-sound-recorder. Tried each of the four input types (digital, adcmux, inmux, invol). Audio plays, and things work fine in Win. Using Gutsy 64 on a Dell XPS 410. Thanks for any hints.

```

$ lspci -v
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
        Subsystem: Dell Unknown device 01db
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: dc000000-dfefffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
        Capabilities: <access denied>

00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
        Subsystem: Dell Unknown device 01db
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at dffe0000 (32-bit, non-prefetchable) [size=128K]
        Memory at dffdb000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at ecc0 [size=32]
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01db
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at ff20 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01db
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at ff00 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 01db
        Flags: bus master, medium devsel, latency 0, IRQ 22
        Memory at dffdac00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Dell Unknown device 01db
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at dffdc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: dbf00000-dbffffff
        Capabilities: <access denied>

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01db
        Flags: bus master, medium devsel, latency 0, IRQ 23
        I/O ports at ff80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01db
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at ff60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01db
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at ff40 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 01db
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at ff980800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
        Subsystem: Dell Unknown device 01db
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
        I/O ports at fe00 [size=8]
        I/O ports at fe10 [size=4]
        I/O ports at fe20 [size=8]
        I/O ports at fe30 [size=4]
        I/O ports at fec0 [size=32]
        Memory at ff970000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
        Subsystem: Dell Unknown device 01db
        Flags: medium devsel, IRQ 10
        Memory at dffdab00 (32-bit, non-prefetchable) [size=256]
        I/O ports at ece0 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8300 GS (rev a1) (prog-if 00 [VGA])
        Subsystem: nVidia Corporation Unknown device 0494
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at de000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at dc000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at dc80 [size=128]
        [virtual] Expansion ROM at dfe00000 [disabled] [size=128K]
        Capabilities: <access denied>

```

---

### Post by yang on 2007-11-03
bump

---

### Post by Jonecm on 2007-11-07
I am experiencing the same problem on my dell vostro 1500 with HDA intel audio card running gusty gibben 7.10.
after installing gusty gibbin 7.10 the audio did not work at all so I installed the latest version of alsa (1.0.15) and my audio OUT works  but sadly no audio in :(
Any help would be greatly! appreciated.

---

### Post by csat on 2007-11-07
Well, this link have hints for microphone and skype.  Maybe it can help you out with Alsa.

[http://geekybits.blogspot.com/2007/06/microphones-skype-on-ubuntu.html](http://geekybits.blogspot.com/2007/06/microphones-skype-on-ubuntu.html)

Good luck
Csat

---

### Post by yang on 2007-11-07
The linked page assumes I can see Microphone, Mic boost, and Capture, but I don't (see attachments).

---

### Post by macabro22 on 2008-02-12
bump!

---

### Post by Dandeloreon on 2008-02-13
if your on gnome you need to run the following command.

gnome-volume-control

once in that, you can modify your mic, and a few other things, it should not be very hard, and on a side note, i'd recommend configuring an asynchronous default sound interface with dsnoop and dmixer, if your using alsa.

---

### Post by yang on 2008-04-07
Hi, Dandeloreon: I knew about gnome-volume-control (same as double-clicking on the volume icon) - I just didn't know what to do in there.

At last, I solved it - at least for myself, though hopefully this can be of help to others!

[LIST=1]
[*]In the volume control, go to Edit > Preferences, and enable everything. (This just displays all sliders. I think all you really need, though, are Digital, InMux, and InVol, because that's all I see on the Recording tab next.)
[*]Go to the Recording tab, click the buttons along the bottom until nothing is crossed out, and move all the sliders to around 50%. (If you move them too high, the mic will pick up major noise. Too low, and you won't hear anything. For some reason, at least two of these work together, perhaps all three - it's not just a matter of moving a single slider.)
[*]Test it out in the Sound Recorder app. Select InVol as the input source. Make sure you've closed the volume control and that your playback volume is up.
[/LIST]

---

