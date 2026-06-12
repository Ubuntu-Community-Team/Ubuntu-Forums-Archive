---
title: "no sound from USB speakers"
date: 2011-06-09
forum: Multimedia Software
---

### Post by engine on 2011-06-09
My headset is doing a fine job, using the standard audio connections, but I'd like to be able to use speakers as well. Someone's given me a very basic "soundball" &#8210; only visible identification, the word 'goobay' &#8210; that's been doing well on another O/S. When I plug it in, it's on speaking terms with the USB port as far as drawing power goes: but doesn't play anything. 

The options from Sound preferences don't include anything as obvious as "use USB port/ use audio connectors". Is there an easy answer?

---

### Post by syoung27 on 2011-06-09
Hey i have the same essential topic already started..Logitech USB Audiohub.

Do you have any Alsa or Pulse apps? that should get you started with sound

---

### Post by webofunni on 2011-06-09
what 

```

sudo lsusb -v
aplay -l

```

says ?

---

### Post by syoung27 on 2011-06-09
did that, but it spat out like 8 pages of info..

lsusb does recognize my logitech audiohub.
my biggest issue is having volume control through hotkeys or the volume icon.
but gmusicplayer stopped playing through the hub now too.
c-rap

---

### Post by webofunni on 2011-06-09
paste the O/P of above commands here inside \[CODE\] tags 

also disconnect your USB device and execute

```

sudo udevadm monitor

```

connect it again and see, if that command gives any O/P, if possible paste that O/P too. Try to format them well, so that we can read it

---

### Post by lidex on 2011-06-09
This info would be helpful:
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by syoung27 on 2011-06-10
i had ubuntu 11.04 server before. loaded the proper desktop edition and sound configures simple as windows

---

