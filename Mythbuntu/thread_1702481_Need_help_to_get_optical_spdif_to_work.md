---
title: "Need help to get optical spdif to work"
date: 2011-03-07
forum: Mythbuntu
---

### Post by ubnewbie2 on 2011-03-07
My mythtv system died, so I transplanted the hard disk drives to a new system. All is working now, except the sound output.  

The new m'board has optical spdif whereas the old one had coax.  The new one also has hdmi which I am not using. The sound settings from the old setup, i.e. sound to ALSA:spdif and passthrough to the IEC device, no longer seem to work.

I have managed to get some analog sound by configuring mythtv to use /dev/dsp,  but I also had to fire up a mixer as all the sound controls were set to zero.  I mention all that, because I am wondering if there isn't a mixer setting or switch, to allow the optical output to work.

I am suffering without my good mythtv sound, so please help  :)

---

### Post by newlinux on 2011-03-08
Does your optical work outside of myth? Have you checked your alsamixer settings to make sure it's not muted? what does aplay -l return?

---

### Post by laffinet on 2011-03-08
Which model is your motherboard ?

I recently tried to connect my motherboard (Asus M2N68-VM) via optical to my receiver. After lots of headaches and googling I found out that the connector is actually an input (at least when using linux).

Bought one of [these ]("http://cgi.ebay.com.au/ASUS-Motherboard-SPDIF-Out-Coaxial-Audio-Bracket-Cable-/230545836157?pt=UK_Computing_ComputerComponents_SoundCards&hash=item35ad9a487d")cheap on ebay, hooked it up to the internal connector of the motherboard and everything worked like a charm.

---

### Post by ubnewbie2 on 2011-03-09
> **laffinet said:**
> Which model is your motherboard ?

I recently tried to connect my motherboard (Asus M2N68-VM) via optical to my receiver. After lots of headaches and googling I found out that the connector is actually an input (at least when using linux).

Bought one of [these ]("http://cgi.ebay.com.au/ASUS-Motherboard-SPDIF-Out-Coaxial-Audio-Bracket-Cable-/230545836157?pt=UK_Computing_ComputerComponents_SoundCards&hash=item35ad9a487d")cheap on ebay, hooked it up to the internal connector of the motherboard and everything worked like a charm.

By coincidence, that's the same m'board as mine :(   Will try your solution, thanks

---

### Post by ubnewbie2 on 2011-03-09
> **newlinux said:**
> Does your optical work outside of myth? Have you checked your alsamixer settings to make sure it's not muted? what does aplay -l return?

I ran alsa-mixer in a terminal window.  Not muting anything, but nothing specific in there for digital.

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

There's another post in this thread that says it's an input, not an output.  Seems using the internal spdif i/o connecter might work.

---

### Post by laffinet on 2011-03-09
> **ubnewbie2 said:**
> There's another post in this thread that says it's an input, not an output.  Seems using the internal spdif i/o connecter might work.

It certainly did on mine. If you want to read a bit more about it try [here]("http://ubuntuforums.org/showthread.php?t=983458&page=2") and [here]("http://www.spinics.net/linux/fedora/alsa-user/msg09280.html").

Be aware that you can't use the internal connector without the proper bracket that provides the proper optical and/or coax connections (like the one I linked in my earlier post).

Once I got the bracket and had it all connected it was working as expected.

---

### Post by ubnewbie2 on 2011-03-09
> **laffinet said:**
> It certainly did on mine. If you want to read a bit more about it try [here]("http://ubuntuforums.org/showthread.php?t=983458&page=2") and [here]("http://www.spinics.net/linux/fedora/alsa-user/msg09280.html").

Be aware that you can't use the internal connector without the proper bracket that provides the proper optical and/or coax connections (like the one I linked in my earlier post).

Once I got the bracket and had it all connected it was working as expected.

Already ordered the bracket.  Thanks again for your help.

---

