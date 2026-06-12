---
title: "Soundcard I/O ports disabled after the latest edgy update?"
date: 2007-04-11
forum: Multimedia &amp; Video
---

### Post by haku.spejsr on 2007-04-11
hi y'all

I'm sorry to bother you, but this morning I lost my sound :(

this morning I did the latest update on my Edgy Eft. At the end of the update, upgrade wizard demanded a reboot. That smelled fishy, as it never asked me to reboot so far (I'm using ubuntu for maybe a month or so). After the reboot I completely lost sound. I followed the steps on the comprehensive guide, and successfully (at least it seemed that way) installed drivers, but to no avail.

aplay -l gives output:

> aplay: device_list:222: no soundcards found...

and lspci -v spits out:

> (...)

00:0b.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
        Subsystem: TERRATEC Electronic GmbH Aureon 7.1 Space
        Flags: bus master, medium devsel, latency 32, IRQ 255
        I/O ports at 8000 [disabled] [size=32]
        I/O ports at 7800 [disabled] [size=128]
        Capabilities: [80] Power Management version 1

(...)

so, from what I can see, I/O ports have been disabled. How do I enable them? I searched this forum and googled (I can't believe spell check still underlines the word googled) it but no quality results came up. I am a music freak and I will not survive long just on pandora playing from my room8s computer. help!

---

### Post by haku.spejsr on 2007-04-11
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/105518](https://bugs.launchpad.net/ubuntu/+bug/105518) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				i worked it out by reverting to the old kernel. it's not really a solution, more like a workaround but hey whatever makes my box sing ^^

big tnx to the irc-support team. i've just reported the bug.

---

### Post by sirvig on 2007-04-11
Same issue on a HP DV6000 laptop:  Sound does not work immediately after reboot required by latest Edgy update.

aplay -l gives
> aplay: device_list:222: no soundcards found...

lspci -v gives
> 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at de300000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0
        Capabilities: [100] Virtual Channel
        Capabilities: [130] Unknown (5)
Reported the bug.  Reverting to the old kernel works as a work around.

---

### Post by wataboutbob on 2007-04-11
Well, I got nothing about I/O ports being disabled... but the latest Edgy update has broken my sound too. I'm using a Dell XPS M1710.

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Dell Unknown device 01ce
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at efffc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

Guess, its going to be the old kernel till this gets fixed.

---

### Post by shofetim on 2007-04-11
Same problem here, Edgy's latest updates (kernel updates) broke the sound... alsa doesn't know that the sound card is there anymore, though lspci can still see it.
My machine is a laptop, Compaq Presario V6000, Audio is:
Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

For now the above workaround works fine. 
Reboot, at grubs screen where you choose which operating system to boot, choose the older version of the kernel, probably 2.6.17-10-generic. The sound should work again.
I had to re-install ndiswrapper to the latest version (1.41) before my wireless card driver would work again though.

---

