---
title: "No sound  - really desperate!"
date: 2013-10-14
forum: Multimedia Software
---

### Post by M7CPn4b on 2013-10-14
Hey there,

I'm putting together an old computer to serve as a htpc, and so far everything was able to get everything working but sound.

I really don't understand it, the card is installed and recognized, in the pulse audio diaolag you even see the bar peeking when there is sound - from my point, everything is as supposed to be, other than there is no sound at all. here are a couple outputs:

sudo aplay -l
```

**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: IXP [ATI IXP], Gerät 0: ATI IXP AC97 [ATI IXP AC97]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 0: IXP [ATI IXP], Gerät 1: ATI IXP IEC958 [ATI IXP IEC958 (AC97)]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0

```


cat /proc/asound/cards 
```

 0 [IXP            ]: ATIIXP - ATI IXP
                      ATI IXP rev 2 with ALC655 at 0xfe02a000, irq 17
 1 [SAA7134        ]: SAA7134 - SAA7134
                      saa7133[0] at 0xfdeff000 irq 20

```


aplay /usr/share/sounds/alsa/Front_Center.wav 
```

Wiedergabe: WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate: 48000 Hz, mono

```


any help is greatly appreciated!

-Emily

---

### Post by Yellow Pasque on 2013-10-14
Are you trying to use analog or digital output?
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by M7CPn4b on 2013-10-14
wow, that is a cool usefull link!

I'm trying to get analog output working.

her's teh link:

 [http://www.alsa-project.org/db/?f=da68a3d1f78d0ce71d57bb4c18943258449f6604](http://www.alsa-project.org/db/?f=da68a3d1f78d0ce71d57bb4c18943258449f6604)

Thank you so much!

---

### Post by Yellow Pasque on 2013-10-14
```
	iface MIXER
		name 'IEC958 Playback Switch'
		value true
```

Run alsamixer and mute the Digital/IEC958 output (press 'm' key to mute it):

```
alsamixer
```

---

### Post by M7CPn4b on 2013-10-15
Thank you very much! (I think) I turned it off - at least on the new report it says "false":

[http://www.alsa-project.org/db/?f=1f30ea8818a3e043ff6c1737d363d4bd59432e45](http://www.alsa-project.org/db/?f=1f30ea8818a3e043ff6c1737d363d4bd59432e45)

But unfortunately, I still have no sound :(

---

### Post by Yellow Pasque on 2013-10-17
The next thing I would try is turning up surround volume. It could be swapped with Master volume.

```
Module snd-intel8x0
  -------------------

    ac97_clock	  - AC'97 codec clock base (0 = auto-detect)
    ac97_quirk    - AC'97 workaround for strange hardware
		    See "AC97 Quirk Option" section below.
    buggy_irq     - Enable workaround for buggy interrupts on some
                    motherboards (default yes on nForce chips,
		    otherwise off)
    buggy_semaphore - Enable workaround for hardwares with buggy
		    semaphores (e.g. on some ASUS laptops)
		    (default off)
    spdif_aclink  - Use S/PDIF over AC-link instead of direct connection
		    from the controller chip
		    (0 = off, 1 = on, -1 = default)


AC97 Quirk Option
=================

The ac97_quirk option is used to enable/override the workaround for
specific devices on drivers for on-board AC'97 controllers like
snd-intel8x0.  Some hardware have swapped output pins between Master
and Headphone, or Surround (thanks to confusion of AC'97
specifications from version to version :-)

The driver provides the auto-detection of known problematic devices,
but some might be unknown or wrongly detected.  In such a case, pass
the proper value with this option.

The following strings are accepted:
    - default	Don't override the default setting
    - none	Disable the quirk
    - hp_only	Bind Master and Headphone controls as a single control
    - swap_hp	Swap headphone and master controls
    - swap_surround  Swap master and surround controls
    - ad_sharing  For AD1985, turn on OMS bit and use headphone
    - alc_jack	For ALC65x, turn on the jack sense mode
    - inv_eapd	Inverted EAPD implementation
    - mute_led	Bind EAPD bit for turning on/off mute LED

For backward compatibility, the corresponding integer value -1, 0,
... are  accepted, too.

For example, if "Master" volume control has no effect on your device
but only "Headphone" does, pass ac97_quirk=hp_only module option.
```

---

### Post by M7CPn4b on 2013-10-17
> **Temüjin said:**
> The next thing I would try is turning up surround volume. It could be swapped with Master volume.

Thank you so much for looking into this. in the meantime, I'm at the point that I think there might be a hardware error. Also under Windows XP there is no sound. Windows also likes to believe that there is, but nothing is coming out of the speakers.
I tried to remove all PCI(e) cards in case of an IRQ mixup, but that didn't help either.

A freind of mine actually has the same board, I think I might try to connect the drive to his board and see if it works there.

What I still think it is strange, is that there is no sound on the back nor front panel connector. And really strange is, that when I plug into the front connector, that back panel connector gets some kind of static, but no sound.

Anyway thank you very much for your help. I'll leave it like this, until I can try the other board, but that might be a couple of weeks until I see him again.

-Emily

---

### Post by M7CPn4b on 2013-10-17
There is actually one more thing, that is a bit strange :)

The original case (HP DX5150 MT) has a strange connector for power switch and LEDs (The mainboard in question is a MSI MS 7050 v1.3 / v2.0):

[IMG]http://i43.tinypic.com/2ajvreg.jpg[/IMG]

the original case doesn't have a reset switch.

In my case now there's no such Plug, and I just connect power reset and the LEDs.

However the red markings in the picture show how these pins are connected within the plug of the original case. It's just a wire connecting one pin with the other.

Could that be the reason the sound isn't working? Because right now these Pins are not connected.

-Emily

---

