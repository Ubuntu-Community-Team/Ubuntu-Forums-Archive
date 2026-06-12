---
title: "Audio Problems in Karmic"
date: 2009-11-01
forum: Multimedia Software
---

### Post by IronOxide on 2009-11-01
After updating to Karmic, there's no longer any sound.

I don't see anything under the 'hardware' tab in sound preferences (but that's new so I'm not sure what exactly is going there).

here's the soundcard info.
[B]00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
	Subsystem: Hewlett-Packard Company Device 30d6
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	Memory at fc480000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

It's an nVidia card, but it seems to be using the intel drivers? Could this be the problem?

---

### Post by Odemia on 2009-11-01
I have an integrated AMD/ATI chipset that uses snd-hda-intel.  It is possible it is the wrong driver but so many cards use that driver that it is probably correct.

I usually find that the problem is an alsa mixer issue.  If you have a gui-alsa-mixer open it up otherwise install 'alsamixer' using "sudo apt-get install alsamixer" in a terminal and then open it up using "alsamixer" in a terminal.  Use the arrows to set all of the levels and use "m" to toggle the mute on the appropriate channels.  Muted channels will have "MM" under them.

If it is not as simple as a mute or level problem try:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
for a complete sound debugging guide.

---

### Post by IronOxide on 2009-11-01
I've run through the whole troubleshooting guide, it's definitely right, the alsamixer was all up, et cetera.

I'll send in a bug report, as I've seen the issue here a couple times already.

---

### Post by michaelzap on 2009-11-01
If there is a proprietary driver for your internal modem (which in my case is a sub-element of my Intel sound card) listed in System -> Hardware Drivers try removing it. I did this and suddenly I had sound and the device is visible in the Sound Control Panel. I still have other problems, but at least I have sound.

---

### Post by D.horse on 2009-11-01
> **michaelzap said:**
> If there is a proprietary driver for your internal modem (which in my case is a sub-element of my Intel sound card) listed in System -> Hardware Drivers try removing it. I did this and suddenly I had sound and the device is visible in the Sound Control Panel. I still have other problems, but at least I have sound.

Thank you for this.  I did what you said and it magically works again!

---

### Post by IronOxide on 2009-11-01
Problem solved with the installation of Alsa 1.0.21.

---

### Post by ZarathustraDK on 2009-11-02
Didn't have any sound either.

Problem for me was that alsamixer had gone and muted a lot of my channels. I unmuted those channels, then noticed that the volume-applet-thingy now suddenly showed "muted", I unmuted that one and then I got sound.

And no, the applet wasn't muted all along, I'm quite sure of that. I did a full reinstall beforehand, and it came like that by default (unmuted), it first changed when I fiddled around with alsamixer, unmuting all the channels.

---

### Post by siliconmeadow on 2009-11-08
> **michaelzap said:**
> If there is a proprietary driver for your internal modem (which in my case is a sub-element of my Intel sound card) listed in System -> Hardware Drivers try removing it. I did this and suddenly I had sound and the device is visible in the Sound Control Panel. I still have other problems, but at least I have sound.

Thanks! That fixed my problem - I never use the modem anyway.
:D

---

