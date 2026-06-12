---
title: "Mic not working with Skype :S"
date: 2011-12-12
forum: Multimedia Software
---

### Post by isaac12345 on 2011-12-12
Hi!!

I recently switched to Lubuntu from ubuntu 11.10 and my mic has stopped working. I tested it with Skype and the voice recorder and I didnt get any output. I have a feeling that the mic's volume has been somehow turned down but I cant find it's volume control.

Any suggestions to solve this issue? Thanks!

---

### Post by isaac12345 on 2011-12-19
bump

---

### Post by dentaku65 on 2011-12-20
Do you have an intel sound card?

If so, I solved in this way:
Install alsamixer
```
sudo apt-get install alsa-utils
```
Edit this file:
```
sudo leafpad /etc/modprobe.d/alsa-base.conf
```
and add at the end the following lines
> #My Intel
options snd-hda-intel model=auto
Save. Reboot. Open alsamixer
```
alsamixer
```
Press F5 and enable Capture (mic), ESC
Done.

---

### Post by goldshirt9 on 2011-12-20
go into your sound settings and ensure the mic is working.

---

