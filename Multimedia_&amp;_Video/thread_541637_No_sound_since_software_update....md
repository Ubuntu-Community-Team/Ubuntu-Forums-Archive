---
title: "No sound since software update..."
date: 2007-09-03
forum: Multimedia &amp; Video
---

### Post by Tribble on 2007-09-03
I updated yesterday, and since I rebooted the system after the update, I haven't had any sound. I *just* got my sound on here working last week, so to have it down again is rather frustrating! When I try to open alsamixer, it tells me "function snd_ctl_open failed for default: no such device." If I try to open volume control, it tells me "No volume control GStreamer plugins and/or devices found." Help, please! :confused:

I got this from lspci -v:

00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, slow devsel, latency 64, IRQ 11
        Memory at c0400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>


Sorry...I'm pretty new to Linux, so I'm not really sure what I'm doing...

Edit: I got this when I tried aplay -l: "aplay: device_list:204: no soundcards found..."

I'm going through [this thread]("http://ubuntuforums.org/showthread.php?t=205449") right now, but this problem didn't start until I downloaded those updates...

---

### Post by Tribble on 2007-09-03
I compiled and installed alsa, and it works again! :KS

---

### Post by zir0n on 2007-09-04
recompiling worked for me

---

