---
title: "Disabled audio devices"
date: 2008-11-24
forum: Multimedia Software
---

### Post by stewartv on 2008-11-24
Hi,

I'm trying to get a logitech usb quickcall speakerphone working. The problem is that although Ubuntu 8.10 and Skype both show the mic and speakers as USB devices in their lists (System/Preferences/Sound) they show as disabled. I think that if I could enable them I'd be able to get the wee beasty working.

Can someone tell me how to do this (I'm afraid that detailed instructions will be necessary as I'm new to this).

Thanks, all help greatly appreciated

Stewart

---

### Post by psyke83 on 2008-11-24
The way to configure Skype is somewhat counter-intuitive, but it's explained here: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Follow the guide itself to ensure you've got PulseAudio configured properly, and look at Appendix C for instructions to configure Skype.

---

### Post by stewartv on 2008-11-24
Thank you psyke83 but I'm afraid that even after following your very clear instructions and changing my Skype configuration it doesn't work.

I think that the first problem is that the two USB audio devices are disabled. As a consequence none of pulseaudio, alsa or skype can actually use them. If I could enable the devices perhaps I could get a bit further.

Let me know if there are configuration details I should post.


Stewart

---

### Post by KaiO on 2009-01-29
I know this is late, but, have a look at:
[http://ozlabs.org/~dgibson/home/quickcall.html](http://ozlabs.org/~dgibson/home/quickcall.html)

And:
Too bad Logitech doesn't give **** about non-Windows users, they make some nice stuff.

---

