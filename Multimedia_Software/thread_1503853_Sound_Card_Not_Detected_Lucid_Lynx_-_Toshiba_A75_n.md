---
title: "Sound Card Not Detected Lucid Lynx - Toshiba A75 notebook"
date: 2010-06-07
forum: Multimedia Software
---

### Post by hemantx on 2010-06-07
I've spent the past 2 days attempting to get the sound working on a Toshiba A75 notebook. Here is what i've tried so far:
remove/purge alsa and pulse audio then reinstall
set up/configure OSS
download and compile latest alsa drivers.

lspci -v shows 00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
Subsystem: Toshiba America INfo Systems Device 0001
Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
Memory at d0004400 (32-bit, non-prefetchable) [size=256]
Kernel driver in use: oss-atiaudio
Kernel modules: snd-atiixp

My questions are: is there anyone using this laptop on Lucid with sound? Can anyone provide a new idea how to make this work if it is compatible hardware.

Thanks!
Ben

---

### Post by hemantx on 2010-06-07
FYI - I re-installed Lucid and the system now recognizes the sound card. I do get sound out of the head phone jack, but not through the on board speakers. I will research this now and hopefully get it running 100%.

Thanks,
Ben

---

