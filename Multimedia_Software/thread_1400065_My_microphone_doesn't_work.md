---
title: "My microphone doesn't work"
date: 2010-02-06
forum: Multimedia Software
---

### Post by TonyPursell on 2010-02-06
I just cannot get my microphone to work. OK, I did once get it sort of working so I know its not a problem with the mic itself, but today there is nothing.  I've done all the obvious things, like checking in alsamixer that it is not muted. 

Here is what aplay -l says about the sound card

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

And the relevant bit from lspci -v

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
	Subsystem: Hewlett-Packard Company Device 2a3d
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at fe9f8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

I have worked through 

[https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems](https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems)

and put a model (3stack-6ch-dig) in alsa-base.conf

My computer is a HP Pavilion desktop and I'm running Ubuntu 9.10 (Karmic).

I'd be grateful for any help on this.

Tony

---

### Post by dabrowsa on 2010-02-06
I've had similar problems.  I eventually removed pulseaudio from my system and updated alsa; for the latter a script is available:

[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

Not sure whether both of those steps were necessary, or whether one or the other on its own would suffice.

---

### Post by ukbobby55 on 2010-02-06
Not sure if this applies to all, but I have just installed Easy Peasy on my Asus Eeepc 900.
Same problem with mic not working.
I uninstalled Skype and replaced it with version 1.4 from Old Skype versions. The mic is now working.

---

### Post by TonyPursell on 2010-02-06
Dabrowsa:

I followed the instructions to install the latest ALSA. Now I get what I've had before.  That is the mic seems to be there for a few minutes (as evidenced by the Input sound level in Sound Preferences) then it stops working.

Have you got any more suggestions?

Tony

---

