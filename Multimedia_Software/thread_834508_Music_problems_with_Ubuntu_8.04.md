---
title: "Music problems with Ubuntu 8.04"
date: 2008-06-19
forum: Multimedia Software
---

### Post by agasamapetilon on 2008-06-19
I have Ubuntu 8.04 and when I play some music and plug my headphones the sound also plays in the speakers. Which is kind of disrupting for others at the office. Does someone knows how can I solve this problem? I have a VAIO VGN-N250E.

Any helo will be much appreciated :)

---

### Post by xc3RnbFO8P on 2008-06-19
Try this:
[http://ubuntuforums.org/showpost.php?p=4763915&postcount=16]("http://ubuntuforums.org/showpost.php?p=4763915&postcount=16")

---

### Post by agasamapetilon on 2008-06-19
It didn't worked for me mate,

This is the text I have in /etc/modprobe.d/alsa-base, where I added the line you copied:

# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
**options snd-hda-intel model=vaio**

I hope to fix this soon,

---

### Post by xc3RnbFO8P on 2008-06-20
Did you restart?
You can try to turn down **Front** in Alsamixer.

> replace options snd-hda-intel model = vaio
with
options snd-hda-intel model=vaio position_fix=0 

---

### Post by agasamapetilon on 2008-06-21
Yep. actually I restarted my laptop and I have the same prob mate.

---

### Post by agasamapetilon on 2008-06-21
I turned down Front from Alsamixer and got nothing :( I still can listen music from the local speakers and my headphones... I have this info from Alsamiker, maybe this could help:

Card: HDA Intel
Chip: Realtek ALC262

Thanks once again,

---

### Post by DannyW on 2008-06-21
I too suggest messing with the different controls in volume control. My laptop has the same problem: Plugging headphones in doesn't turn the speakers off. However, I can mute the laptops speakers by muting Front and I still hear the headphones.

---

### Post by agasamapetilon on 2008-06-21
I do believe is a VAIO problem. I've installed Ubuntu 8.04 in an DELL laptop and everything is OK. Some friends of mine who have a different VAIO got the very same problem as me. I hope to find an answer soon and I will update this thread.

:)

---

