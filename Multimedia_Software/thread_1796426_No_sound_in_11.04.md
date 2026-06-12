---
title: "No sound in 11.04"
date: 2011-07-03
forum: Multimedia Software
---

### Post by UkuleleLenny on 2011-07-03
I used an HDMI cable to display my computer through the television, and ever since the sound doesn't work through HDMI or without it. Can't get sound at all now. Here is my output for lspci -v | less 

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
        Subsystem: Toshiba America Info Systems Device ff1e
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00007000-00007fff
        Memory behind bridge: d2000000-d30fffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000d1ffffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Device ff1e
        Flags: bus master, medium devsel, latency 0, IRQ 16

```Here is a screen of my sound preferences Hardware selection, none work. 

[IMG]http://imgur.com/7gCnZ[/IMG][IMG]http://i.imgur.com/7gCnZ.png[/IMG]

Only Dummy Output (Stereo) is available on the Output tab. Please let me know if there is any other info needed. I checked through the Sound Troubleshooting and nothing helped. Thank you to whoever can help me out, this only started after upgrading to Natty.

EDIT: Forgot to say, I tried a complete reinstall with 11.04 and then 10.10 and it still didn't work.

---

### Post by UkuleleLenny on 2011-07-04
Up, still no good.

---

### Post by UkuleleLenny on 2011-07-05
up

---

### Post by lidex on 2011-07-06
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by UkuleleLenny on 2011-07-06
[http://www.alsa-project.org/db/?f=d22b0d6e7767cd492e49c41fee1a709afaf4437e](http://www.alsa-project.org/db/?f=d22b0d6e7767cd492e49c41fee1a709afaf4437e)

Thanks

---

### Post by lidex on 2011-07-06
Remove the ~/.asoundrc file, reboot and run the info script again please.

---

### Post by UkuleleLenny on 2011-07-06
[http://www.alsa-project.org/db/?f=5b03d873f03d52c984eb1404afdd0730fc031e10](http://www.alsa-project.org/db/?f=5b03d873f03d52c984eb1404afdd0730fc031e10)

Thanks

---

### Post by lidex on 2011-07-06
> **UkuleleLenny said:**
> [http://www.alsa-project.org/db/?f=5b03d873f03d52c984eb1404afdd0730fc031e10](http://www.alsa-project.org/db/?f=5b03d873f03d52c984eb1404afdd0730fc031e10)

Thanks
Something weird here, did you reboot?
How about trying a different kernel?

---

