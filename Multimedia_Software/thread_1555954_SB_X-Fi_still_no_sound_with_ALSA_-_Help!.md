---
title: "SB X-Fi still no sound with ALSA - Help!"
date: 2010-08-18
forum: Multimedia Software
---

### Post by polmak on 2010-08-18
I have been using Ubuntu since 8.04 on a dual boot and also VM and am still loathe to swap as primary OS due to the fact that cannot get  this sound card to work.

Have tried most fixes and even though ALSA is supposed to now work "out of the box" with the SB X-Fi , still no joy.

I am using 10.04 64bit the sound card is recognised as show...

```

03:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG
	Subsystem: Creative Labs Device 0018
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at f9ffc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

[IMG]http://polmak.co.uk/ss1.png[/IMG]

Any help in finally getting this to work would be greatly appreciated

---

### Post by cchhrriiss121212 on 2010-08-18
Does it show up in aplay -l?

---

### Post by lidex on 2010-08-19
I'll second that request from chris. Also run this command:
```
ubuntu-bug audio
```

---

### Post by polmak on 2010-08-20
Will run a aplay -l and submit a launchpad bug later from home PC, thanks for reply guys.

---

### Post by polmak on 2010-08-22
aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 0: CA0110 Analog [CA0110 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Generic [HD-Audio Generic], device 1: CA0110 Digital [CA0110 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

and bug #622144

---

### Post by keithjr on 2011-01-23
I appear to have made the mistake of purchasing the same sound card as polmak, the Sound Blaster X-Fi Xtreme Audio PCIe.  I'm running Ubuntu 10.04 and although the audio device appears correctly in most listing, and applications do attempt to play sound, no sound is produced, and input does not work.  

Here is the *aplay -l* output (ignore the ATI one, that's the onboard).

```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 0: CA0110 Analog [CA0110 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 1: CA0110 Digital [CA0110 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Also, here are the *lspci* lines for it:

```

02:00.0 PCI bridge: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG PCI to PCIe Bridge
03:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG

```

I ran *ubuntu-bug audio* and followed the debugging steps there (set pulse to plain Analog Duplex, max out alsamixer settings), and the tones did not play.  The program didn't send me to the launchpad correctly so I did not file a bug on this yet, but I imagine it would be quite redundant with polmak.

Most of the posts I've found show ALSA no having support for CA0110-IBG, but they are also two years old.  Has there been any development here?  Thanks.

ps - I'm in the enviable position to return this hardware if I can't get this resolved shortly.  However, this is the second sound card I've purchased in an increasingly frustrating battle to get 5.1 output.

---

### Post by akuda on 2011-02-27
Hi,

According to [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)
the device you mention is still not supported. I go the same problem.

Regards,
akuda

---

### Post by Yellow Pasque on 2011-02-27
Do a little research next time. Most of the money you paid is for the "Creative Labs" name, which doesn't have positive value to anyone running Linux. A card with an HD codec on it isn't much of an upgrade over onboard audio.
If you're in the market for a good, cheap sound card: [http://www.newegg.com/Product/Product.aspx?Item=N82E16829132020&nm_mc=AFC-Techreport&cm_mmc=AFC-Techreport-_-NA-_-NA-_-NA](http://www.newegg.com/Product/Product.aspx?Item=N82E16829132020&nm_mc=AFC-Techreport&cm_mmc=AFC-Techreport-_-NA-_-NA-_-NA)

---

