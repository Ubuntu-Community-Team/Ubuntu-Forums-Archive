---
title: "Sound card works with Modprobe, Sort of."
date: 2005-11-12
forum: Multimedia &amp; Video
---

### Post by No-Brain on 2005-11-12
I have a Dell Optiplex GX1 500Mhz pc with 128meg ram and onboard sound Operating system is WIN98 and Ubutu 5.10.  The onboard sound is Crystal CS4236B.  Works fine from WIN98.

To get the sound to work in Ubuntu, I have to do sudo modprobe snd-cs4236.  I then have to log out, and log back in.  My sound then works.

I have spent hours trying to get it to work automatically.  I have had to reinstall Ubuntu 5.10 several times.  I tried manually installing alsa, but that screwed up my video.

Can someone help this Linux Newbie.
TIA
Roger

---

### Post by ranf on 2005-11-12
[QUOTE=No-Brain]
To get the sound to work in Ubuntu, I have to do sudo modprobe snd-cs4236.  I then have to log out, and log back in.  My sound then works.
[/QUOTE]
You can add snd-cs4236 to the file /etc/modules.

---

### Post by No-Brain on 2005-11-12
Thank you.  I thouht it might be something as simple as that, but in all my hours researching the problem that was one thing I did not come across.

Worked like a charm.  

Roger :D

---

### Post by ranf on 2005-11-13
[QUOTE=No-Brain]
Worked like a charm.  
[/QUOTE]
Great.

---

