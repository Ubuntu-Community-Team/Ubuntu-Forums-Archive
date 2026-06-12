---
title: "no sound in ubuntu"
date: 2006-06-18
forum: Multimedia &amp; Video
---

### Post by unisol on 2006-06-18
i have no sound in dapper i tried lspci |grep audio and it diaplayed Creative Labs SB Live EMU10k0, i tried sudo modprobe snd-emu10k0 no luck i going to try alsa-config and sudo gst-register-0.8

---

### Post by unisol on 2006-06-18
i click on the volume control it tells meno volume control gstreamer plugins and/or devices found

---

### Post by davidebond on 2006-06-18
Sorry, but....  Have You proven in alsa-mixer to turn on every slider witn the command 'm'? Then, you must only adjust the volume.

hi,


                                            davide

---

### Post by Teroedni on 2006-06-18
try with ```
modprobe snd-emu10k1
``` 

More alsa information here
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+5.1.&chip=emu10k1&module=emu10k1](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+5.1.&chip=emu10k1&module=emu10k1)

---

### Post by unisol on 2006-06-19
thanks for your help i have sound working except for audio cds which ill try to figure out today again thanks its good to know you have people like you and others keep up the good work

---

### Post by chrisccoulson on 2006-06-19
I had no sound in Dapper after my initial install, and I also got an error when attempting to play audio CD's. After spending ages trying to understand what the problem was, I stumbled across an option in users-admin within my profile properties to enable me to use audio devices. This box was unchecked for some reason (probably because I added myself via useradd as opposed to using users-admin). Once I checked this box, all of my audio problems went away.

It might seem a silly thing to suggest, but it could be easily overlooked.

---

