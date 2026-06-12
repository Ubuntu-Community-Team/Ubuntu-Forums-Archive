---
title: "Annoying Speaker Buzz"
date: 2007-11-17
forum: Multimedia &amp; Video
---

### Post by SomeYahoo on 2007-11-17
I've searched and searched, but can't find the solution.  I have a low pitch buzz or hum out of the speakers all the time in Gutsy, but not in Windoze.  I have run the script from [this]("http://ubuntuforums.org/showthread.php?t=614773") thread, but it didn't help.  I'm new to Linux, so maybe it's something easy, but I can't figure it out.  I assumed it was hardware, but I moved my sound card away from my vid card (bottom slot) and nothing... that and it doesn't do it in Windoze.

Output from lspci:
```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
02:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
02:02.0 Communication controller: Conexant Unknown device 2702 (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)
02:0c.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
02:0c.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
```
Output from cat /proc/asound/cards
```
 0 [Live           ]: EMU10K1 - SBLive! Value [CT4780]
                      SBLive! Value [CT4780] (rev.10, serial:0x80221102) at 0xcc40, irq 22

```
Output from cat /proc/asound/version
```
Advanced Linux Sound Architecture Driver Version 1.0.14.
Compiled on Nov 17 2007 for kernel 2.6.22-14-generic (SMP).

```

I have everything muted in Alsa Mixer except PCM and Master (muted: Synth, Line-in, CD, Microphone, Phone, PC Speaker, and Aux).  The SB Live Analog/Digital Output Jack switch is off.

Any ideas???

---

### Post by Brautigam on 2007-11-17
you need a better speaker cable or make sure its not touching any other metal near the wires. also if you have any adapters try going without them. :)

---

### Post by SomeYahoo on 2007-11-17
Wouldn't the cable cause the same issue in windows?

---

### Post by SomeYahoo on 2007-11-17
FIXED... but why???

Just decided to hit random switches in the Alsa mixer, and turning Phone Capture ON stopped the buzz.

Weird.

---

### Post by OutlawTX on 2007-11-18
I'm having the same issue. I'm certain its not the cable.

---

### Post by SomeYahoo on 2007-11-18
Did you try the phone capture button?  I'm guessing it has something to do with internal wiring and an open-ended connection, and clicking that on helps the system cope.

...or something.

---

