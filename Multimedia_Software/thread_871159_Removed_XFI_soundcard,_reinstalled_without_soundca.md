---
title: "Removed XFI soundcard, reinstalled without soundcard. Still no sound, please help."
date: 2008-07-26
forum: Multimedia Software
---

### Post by msmr on 2008-07-26
I removed my Creative X-FI card from my dell XPS last night (which also happened to remove all the rear panel for all the soundjacks too) which also happened to have a bypass cable going to it from the card to the front panel which I removed. Now today, I hook back up my computer and boot it on, restart, and reinstall Ubuntu without the soundcard in. 

I am really really stumped on this one.

I removed my soundcard, and enabled my integrated audio via the bios. in the alsa gui mixer everything is unmuted.

In the command line alsa mixer everything is unmuted.

The only thing that is different is that I took the soundcard out of a PCI-E slot and reinstalled linux without it in it.

Here is the pastebin for all the devices on my machine (dude to size I don't want to paste it as a giant blob of text)
[http://pastebin.com/m7b2c0bdd](http://pastebin.com/m7b2c0bdd) I don't know what it is, like I am assuming the unknown devices are basically empty PCI-E slots.

And here is what aplay -l gives me
```
msmr@crapbox:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Thanks.

---

