---
title: "Sound on a TX2 hp touchsmart tab PC laptop"
date: 2009-04-15
forum: Multimedia Software
---

### Post by robinbj on 2009-04-15
i was told to perform this cod
> # ```
Update modprobe.d/alsa-base
``` to make sound work (in my experience has to be done as root -- probably not in the audio group?) "```
sudo echo "options snd-hda-intel model=toshiba" >> /etc/modprobe.d/alsa-base".
```
).

but that according to the code say model=toshiba... however were all running HP Touchsmart... help. Should i change the ```
model=toshiba
``` to ```
model=hp
```? i dont want to screw with anything

brad

---

### Post by robinbj on 2009-04-15
as well if i run that second code, i get a small carrot and am not sure what to do. Ive read many many MANY posts (i would say Ive spent about 5hrs so far on this) and nothing worked.

WHAT DO I DO?!?!?!

---

### Post by bstudios on 2009-08-21
The command you noted has a number of syntax issues. Try this, all on one line:

sudo sh -c "echo options snd-hda-intel model=toshiba >> /etc/modprobe.d/alsa-base.conf"

Then the simplest thing to do is reboot. If your speakers aren't muted (the hardware volume buttons should work by default to turn them up), you should hear sound when it boots up.

---

### Post by doctorfilter on 2009-09-21
That worked for me too Thanks! :)
:guitar:

---

### Post by Ulio on 2009-10-09
Made these changes too... going for reboot... :confused:

I Will post news in a while ;)

---

### Post by Ulio on 2009-10-09
Some stranges news...now i can hear music but system sounds ... it doesn't notice when i plug the earphones.... no digital sound

And still appears the error message at startup.... 

Can somebody help me?

I have a TX2-1020

---

### Post by Favux on 2009-10-09
Hi Ulio,

Welcome to Ubuntu Forums!

You may need to play with the alsa mixer, maybe in the terminal.  Briefly described in 8 ) here:  [http://ubuntuforums.org/showthread.php?t=1252492](http://ubuntuforums.org/showthread.php?t=1252492)

Hope this is helpful.

---

