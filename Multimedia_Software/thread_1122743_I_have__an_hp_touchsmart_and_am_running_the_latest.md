---
title: "I have  an hp touchsmart and am running the latest ubuntu..NO SOUND"
date: 2009-04-11
forum: Multimedia Software
---

### Post by robinbj on 2009-04-11
Okay, so im running the HP Touchsmart tx2 with no availl as to sound with the latest ubuntu.
I havce tried many things on this website including things from the wikis, but nothing to any avail

[**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0]
Is what i have for sound, but yet I cant seem to get anything to go.

help

brad

---

### Post by Favux on 2009-04-11
Hi Brad,

This thread should be helpful in general but for sound check posts #53 and #72 here:  [http://ubuntuforums.org/showthread.php?t=1038898&highlight=tx2*&page=6](http://ubuntuforums.org/showthread.php?t=1038898&highlight=tx2*&page=6)

I hope this is helpful.

---

### Post by robinbj on 2009-04-15
Okay so I did that and all the code i get has worked and gone thru however there is one area that says
```
 model=toshiba
```

should I change that? should I not? what should I do. I posted another forum thread about this.

---

### Post by Favux on 2009-04-15
Hi robinbj,

Go ahead and use it.  The model= refers to the configuration and if it works it doesn't matter what the name is.  I know it doesn't make much sense on its face but you'd have to read a bunch of stuff to get the feel for it and it isn't worth bothering.  This file:  [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)  is actually on your hard drive someplace.  It's the sound chip that counts, not the laptop brand name.  And then to complicate things the south bridge name can get in there too.  And you can always remove the line if you need to.

---

