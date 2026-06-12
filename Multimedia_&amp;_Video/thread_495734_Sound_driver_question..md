---
title: "Sound driver question."
date: 2007-07-08
forum: Multimedia &amp; Video
---

### Post by Sean K on 2007-07-08
Recently, Ubuntu has stopped being able to play sound all together. I don't understand why, because in 6.10 it worked fine.

Running some commands (can't remember what they were now) tells me I have no detectable sound card, and therefore no sound.

Is there anyone out there nice enough to walk me through getting my sound working? The Comprehensive Sound Guide is useless to me, as is mostly every other thread I have searched through since Feisty was released.

The motherboard is an ASUS A8N-VM CSM, and I am using the onboard sound card.

Any help would be awesome.

---

### Post by Daveth on 2007-07-08
what does alsamixer say when typed into a terminal ? It should have what it recognises as the sound device, with the control options. It might be that something just got turned down/off.

---

### Post by GFC2 on 2007-07-08
Here's a link to a discussion of configuring the sound module to correctly recognize the sound card.  It solved problems similar to yours.

[http://ubuntuforums.org/showthread.php?t=452992](http://ubuntuforums.org/showthread.php?t=452992)

---

### Post by Sean K on 2007-07-09
> **Daveth said:**
> what does alsamixer say when typed into a terminal ? It should have what it recognises as the sound device, with the control options. It might be that something just got turned down/off.

There is no soundcard installed. Nor can it it be installed, apparently. When I try to install the alsa drivers, it fails, giving me some kind of error. This is what 'alsamixer' outputs:

```
sean@AMD2010:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
```

More information:

```
sean@AMD2010:~$ aplay -l
aplay: device_list:222: no soundcards found...
```

When I compile alsa drivers and try and install it, it says it was sucessfull. Then I try some 'modprobe' command and it returns a fatal error. Here it is:

```
sean@AMD2010:~/Desktop/alsa-driver-1.0.14$ sudo modprobe snd-intel8x0FATAL: Error inserting snd (/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.20-16-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_intel8x0 (/lib/modules/2.6.20-16-generic/kernel/sound/pci/snd-intel8x0.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

Any ideas?

---

### Post by Sean K on 2007-07-10
Anyone?

---

### Post by Daveth on 2007-07-15
well, we can now say that your chip is a 5.1-channel Analog Device AD1986A HD audio- have you checked the page GCF2 noted for this?  Alternatively google for it and Linux. 

Whilst you need someone with more mod-probe savvy than me to confirm, I'm wondering if the HD capacities of this chip are alluded to in the fatal errors and "Unknown symbol in module, or unknown parameter" sections. People have played around editing /etc/modprobe.d/alsa-base to get their SoundMAX Integrated HD Audio to work, so that looks like your best avenue of exploration. Sorry not to be of more help.

Your motherboard spec has (unless you have filled them up) 2 PCI slots, so you could fit a separate sound card in if you wanted, though you would have to go out and buy one, of course.

---

### Post by Sean K on 2007-07-16
I remember coming accross that thread before, and I don't remember it working I don't think.. I'll give it another go though, hopefully I'm wrong.

One question I have, is because it's HD, I've been told the driver is the hda-intel driver. But when I use the Comprehensive Sound guide like everyone tells me to, the "sound card matrix" tells me the driver is intel8x0.

Can someone tell me, once and for all, which driver my sound card needs? What information do you need for that?

---

### Post by Sean K on 2007-07-31
Any help? Anyone?

---

