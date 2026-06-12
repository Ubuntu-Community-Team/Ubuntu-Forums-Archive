---
title: "Terratec DMX 6Fire USB Audio not detected"
date: 2013-02-03
forum: Multimedia Software
---

### Post by chuzzlewit69 on 2013-02-03
Hi!

I'm relatively new to all this so apologies if I'm not making any sense!
I recently got hold of a Terratec soundcard and attempted to get it to work with my Ubuntu 12.10 set-up. I've successfully installed it on my Win XP system so I know the card is working.

I may have jumped the gun a little and started following instructions here:[http://www.alsa-project.org/main/index.php/Matrix:Module-usb-6fire](http://www.alsa-project.org/main/index.php/Matrix:Module-usb-6fire)

I inadvertently broke ALSA whilst trying to follow these instructions - now fixed though.


I have downloaded and compiled the dmx6 fire module ([https://sourceforge.net/projects/sixfireusb/](https://sourceforge.net/projects/sixfireusb/)) and firmware as instructed but when I try and insert into my kernel with modprobe, but get this error:

```
FATAL: Error inserting snd_usb_6fire (/lib/modules/3.5.0-23-generic/extra/snd-usb-6fire.ko): Invalid argument
```dmesg returns a bunch of errors for this module which all begin with unknown symbol... (see attached .txt file)


[   15.290950] snd_usb_6fire: Unknown symbol snd_rawmidi_receive (err 0)
[   15.290969] snd_usb_6fire: Unknown symbol snd_rawmidi_transmit (err 0)
[   15.290977] snd_usb_6fire: disagrees about version of symbol snd_ctl_add
[   15.290980] snd_usb_6fire: Unknown symbol snd_ctl_add (err -22)
[   15.290985] snd_usb_6fire: disagrees about version of symbol snd_pcm_new
[   15.290987] snd_usb_6fire: Unknown symbol snd_pcm_new (err -22)
[   15.290995] snd_usb_6fire: disagrees about version of symbol snd_card_register
[   15.290996] snd_usb_6fire: Unknown symbol snd_card_register (err -22)
[   15.291004] snd_usb_6fire: disagrees about version of symbol snd_card_free
[   15.291006] snd_usb_6fire: Unknown symbol snd_card_free (err -22)
[   15.291011] snd_usb_6fire: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all

....etc...etc

I'm not entirely sure what do from here as having read around the subject a little soe people are saying this card should work automatically with Ubuntu 12.10???

Any help would be greatly received!!

---

### Post by Yellow Pasque on 2013-02-03
> I inadvertently broke ALSA whilst trying to follow these instructions - now fixed though.
So how did you break it and how did you "fix" it? (Usually, version errors indicate that you're not using the original repo ALSA, so I'm a bit skeptical that you completely "fixed" it and reset it to how it would be on a fresh install, even if your onboard sound works.)

---

