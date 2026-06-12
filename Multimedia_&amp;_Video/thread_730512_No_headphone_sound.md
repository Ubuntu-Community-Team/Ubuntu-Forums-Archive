---
title: "No headphone sound"
date: 2008-03-20
forum: Multimedia &amp; Video
---

### Post by skullins on 2008-03-20
I searched around and couldn't find anything that helped me...

When I plug in my headphones the sound still comes from my laptop speakers but no sound comes through my headphones. I've tried going into volume control and muting the master volume, that cuts out the sound from my speakers but I still have no sound in headphones. I tried right click sound icon>preferences>clicking on headphones... still no sound.

I am using a Toshiba satellite a135-s4656. Running Ubuntu 8.04

---

### Post by Yellow Pasque on 2008-03-21
See if this thread helps with jack sensing:
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

### Post by skullins on 2008-03-21
Ok where it says "Type the first word from the list in /etc/modprobe.d/alsa-base or (if that one does not exist) /etc/modprobe.conf Just try them until you've found the right match. ( you can edit these files with your favourite text editor, for example: sudo gedit /etc/modprobe.d/alsa-base or sudo gedit /etc/modprobe.conf )

For example: If cat /proc/asound/card0/codec#* | grep Codec or : aplay -l return "Realtek ALC260" , Look under "ALC260" in the list and add the following line in your /etc/modprobe.d/alsa-base or (if that one does not exist or is empty) /etc/modprobe.conf

options snd-hda-intel model=hp
"

How would I go about adding that line to it? I checked my card and the first word is 3stack so I'm assuming I have to add "options snd-hda-intel model=3stack" but I have no idea how I would add that.

Sorry, I'm really new to ubuntu and linux in general.

---

### Post by Yellow Pasque on 2008-03-21
> Sorry, I'm really new to ubuntu and linux in general.
No need for apologies. We were all n00bs at one time.
```
gksudo gedit /etc/modprobe.d/alsa-base
```

---

### Post by skullins on 2008-03-21
Ahhh I was close. I added the sudo but left out the gedit haha

I'll try it now and let you know.
Thanks

---

### Post by skullins on 2008-03-21
Ok so now I have sound through my headphones but it still comes out of the speakers at the same time. Getting closer.... haha

---

### Post by skullins on 2008-03-21
So anyone got any ideas?

EDIT: Fixed it!!

I had to add "snd-had-intel model=lenovo" in "/etc/modprobe.d/alsa-base"

---

### Post by Yellow Pasque on 2008-03-22
Awesome!

---

