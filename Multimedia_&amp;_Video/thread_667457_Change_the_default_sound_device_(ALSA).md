---
title: "Change the default sound device (ALSA)"
date: 2008-01-14
forum: Multimedia &amp; Video
---

### Post by ema on 2008-01-14
How do I change the default sound device with ALSA?
I want to set an USB Logitech headphones + microphone as default device...
When I plug the USB everything works, but still I can only use applications where I can actually set the ALSA device (like Skype, WoW, Ekiga) but I'm not able to use it with application like TeamSpeak or FireFox (I'm using aoss with it).

How can I solve this?

Thanks,
Ema.

Ps. waiting for alsa 1.0.15...

---

### Post by kvonb on 2008-01-14
_**-**_[u][b][size=3]
[/size][/b][/u]

---

### Post by ema on 2008-01-14
Even if the device is a USB device?

Thanks,
Ema.

---

### Post by ema on 2008-01-14
> **kvonb said:**
> Follow the section:

[U][B][SIZE=3]Configuring default soundcards / stopping multiple soundcards from switching

here:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
[/SIZE][/B][/U]

Hello, I tried this but doesn't work.

I have this file:

```

...
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
...

```

If I change these lines

```

...
options snd-usb-audio index=0
options snd-usb-usx2y index=0
options snd-usb-caiaq index=0
...

```

USB headphones + microphone don't get detected from Ubuntu...

Then I put back the -2 values on everything and added 
```

options snd_usb_audio index=0

```
At very end of file. The USB device now is detected, but when I launch an MP3 with mplayer still is heard from the notebook audiocard (HDA Intel) and not from the USB headset...

Where am I wrong?

Thanks in advance,
Ema.

---

### Post by ema on 2008-01-14
Isn't there a way to do so?
I read about alsaconf but isn't present on Ubuntu... :*(

Any suggestions?

Ema...

---

### Post by vizualbod on 2008-05-14
> **ema said:**
> Isn't there a way to do so?
I read about alsaconf but isn't present on Ubuntu... :*(

Any suggestions?

Ema...

I have the same problem, have you found any solutions?

---

### Post by nickishappy on 2008-06-12
> **vizualbod said:**
> I have the same problem, have you found any solutions?

You can create the files and alsa will automatically see that they are there and use them (may require reboot)

---

