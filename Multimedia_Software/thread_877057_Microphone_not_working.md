---
title: "Microphone not working"
date: 2008-08-01
forum: Multimedia Software
---

### Post by SupaRice on 2008-08-01
So, everything on my new system (8.04) works good from an audio perspective except my microphone.  I've browsed through the audio troubleshooting guides, and nothing seems to apply.  I get audio playback just fine, even from multiple sources at the same time.

Here is some output from my system:
```

# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


# lspci -v
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
        Subsystem: Dell Unknown device 020d
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at fdff4000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0


```

As a side note, I've noticed when trying to test that gnome sound recorder will not work, because it doesn't have any options under the "record as".
[IMG]http://i6.photobucket.com/albums/y213/suparice/sr.png[/IMG]

And I've also tried adjusting the levels for the mic, and have tried both inputs front and back of the machine.
[IMG]http://i6.photobucket.com/albums/y213/suparice/mixer.png[/IMG]

Any help is appreciated!

---

### Post by SupaRice on 2008-08-01
*bump*

---

### Post by SupaRice on 2008-08-04
* b u m p *

Anybody?

---

### Post by Loaded.len on 2008-08-05
I have the same issue, except I have a slightly older chipset revision. (and mine is a Gigabyte board, not Dell)

```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Giga-byte Technology Unknown device a002
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at e6000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0
```

Everything except the mic works fine.

---

### Post by SupaRice on 2008-08-05
I'd really like to figure this out, as it's one of the things holding me back from going to 8.04 on my laptop.  I've got to have Skype working first so that I can work.

---

### Post by Loaded.len on 2008-08-06
Skype is another problem entirely. I have another desktop with a Creative SB Live in it and it works just fine as long as Skype isn't running.  The capture volume in Skype is either terribly low and distorted, or I get blasted with feedback. There doesn't seem to be a happy medium. If memory serves, I had similar problems in Feisty. My current problem with this box and Hardy is specific to Intel HDA. I've followed various guides and tips but none seem to work. I'm looking for a definitive fix for this issue. I'll deal with Skype later.

---

### Post by SupaRice on 2008-08-06
Skype works just fine for me in 7.1, but on my 8.04 machine the MIC isn't working so nobody can hear me.

---

