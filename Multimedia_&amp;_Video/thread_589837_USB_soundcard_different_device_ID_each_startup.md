---
title: "USB soundcard different device ID each startup"
date: 2007-10-24
forum: Multimedia &amp; Video
---

### Post by 7marius on 2007-10-24
Hi,

I have an external sound card connected at bootup. Sometimes it is detected as card 1, sometimes as card 2, so every other time I start a music player, I first have to change the settings to the correct card.
Is there a way to tell alsa to always use the USB card as card 1?

Thanks
Marius

---

### Post by 7marius on 2007-11-09
OK, for everyone having this issue, I found a solution:

First you find out which modules you need. (I used lspci and lsmod)
Then you blacklist them for udev, this is done in

/etc/modprobe.d/blacklist

For my setup it looks like this:

blacklist snd_emu10k1
blacklist snd_usb_audio

Now you want to load the modules at bootup in a predefined order, which is done by putting an entry in /etc/modules:

snd-emu10k1
snd-usb-audio

That's it, enjoy!

---

