---
title: "help with sending audio to usb headset"
date: 2010-03-12
forum: Multimedia Software
---

### Post by mylo9000 on 2010-03-12
ok, i've been searching the forums for 3 hours now and i can't find a solution to this issue.

I've finally got my Tv card working however i can't seem to get the audio to playback in my logitech usb headset (the ps2 one that came with the original socom)

all other system sounds and music playback fine but i can't get the sound from my tvcard (that is connected to the cd-in on my mobo) to route to the headset. its really starting to get frustrating.

any recommendations?

---

### Post by markbuntu on 2010-03-12
If you are using karmic and pulseaudio you can do that with the module-loopback which you will need to load manually. There is a thread around here somewhere on how to do that.

---

### Post by mylo9000 on 2010-03-14
> **markbuntu said:**
> If you are using karmic and pulseaudio you can do that with the module-loopback which you will need to load manually. There is a thread around here somewhere on how to do that.

yes this is right, i searched the forums for module-loopback and found an post that shows how to implement it successfully. 
thanks

---

### Post by mylo9000 on 2010-03-14
ok not so much a fix as i hoped. the loopback module causes a buildup that eventually causes the vt1708/a card to dropout eventually. usually 2 minutes after i boot up. so i guess its back to the drawing board.

---

