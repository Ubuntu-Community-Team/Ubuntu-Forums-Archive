---
title: "Can't get sound to work"
date: 2010-05-17
forum: Multimedia Software
---

### Post by quindraco on 2010-05-17
I get no output from speaker-test, nor any other program I run to try and produce sound.  Some info:

lspci -v:
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
    Subsystem: Dell Device 0400
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel modules: snd-hda-intel

aplay -l:
aplay: device_list:223: no soundcards found...

alsamixer:
cannot open mixer: No such file or directory

cat /proc/asound/cards:
--- no soundcards ---

uname -a:
Linux rweinber-desktop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

Apt-get reports that I am as up to date as it is possible to be.  Anyone have any idea what I should try next?

---

### Post by lidex on 2010-05-17
Your alsa install is borked. Upgrade it using the alsa-upgrade link in my sig.

---

### Post by quindraco on 2010-05-18
Thanks for the help!

I can't upgrade my alsa.  Firstly, the final output of the script says this, which has me concerned:

chmod: cannot access `/dev/dsp': No such file or directory
chmod: cannot access `/dev/mixer': No such file or directory
chmod: cannot access `/dev/midi': No such file or directory

Secondly, after rebooting:
cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on May 17 2010 for kernel 2.6.32-22-generic (SMP).

I.e. the out of date version, compiled yesterday, apparently.

---

### Post by mikeiw on 2010-05-18
I have exactly the same issue, with only the details of my card being different, as follows:

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Contr$
        Subsystem: ASUSTeK Computer Inc. Device 812a
        Flags: 66MHz, fast devsel, IRQ 22
        I/O ports at dc00 [size=256]
        I/O ports at e000 [size=256]
        Memory at d3103000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel modules: snd-intel8x0
aplay: device_list:223: no soundcards found...

Not an easy position to be in, as I'm a total Ubuntu newb, and can't seem to make head-nor-tail of any of the existing help threads on here.  Whether it's old age or my CFS clouding my mind, I don't know :(

Any help would be appreciated :)

---

### Post by lidex on 2010-05-18
*quindraco*,
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get install --reinstall alsa-utils alsa-oss alsa-base libasound2 libasound2-plugins linux-sound-base gstreamer0.10-alsa
```

---

