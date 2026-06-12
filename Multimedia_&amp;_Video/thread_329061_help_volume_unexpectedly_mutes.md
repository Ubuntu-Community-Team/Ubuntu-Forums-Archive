---
title: "help: volume unexpectedly mutes"
date: 2006-12-31
forum: Multimedia &amp; Video
---

### Post by stevecrozz on 2006-12-31
When ubuntu first boots, I can hear the startup sound, then I can load some of my music with rhthmbox and play it. It works wonderfully and I can adjust the volume inside the software. But if I use the master volume controls, including the keyboard hotkeys, it instantly mutes the sound. When I visit the alsa mixer, everything is still unmuted and I have the volume on every channel turned all the way up. Every channel is visible because they've all been checked in preferences. 

When I CTRL+ALT+BACKSPACE and login again, the volume is still missing. When I restart the machine entirely it comes back unless I dare adjust the volume. Any ideas? I'm going to play with it some more and I'll report if I find anything further.

BTW, I have an ASUS 8AF laptop

Here's the output from aplay -l"

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
stevecrozz@steve-laptop:~$ cat /proc/asound/modules
 0 snd_hda_intel

Here's the applicable portion of lspci -v:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1443
        Flags: bus master, fast devsel, latency 0, IRQ 66
        Memory at feb3c000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0




--Stephen

---

### Post by stevecrozz on 2006-12-31
Solution:  [http://ubuntuforums.org/showthread.php?t=260352](http://ubuntuforums.org/showthread.php?t=260352)

Thanks so much!

---

