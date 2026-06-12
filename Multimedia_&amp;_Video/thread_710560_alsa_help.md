---
title: "alsa help???"
date: 2008-02-28
forum: Multimedia &amp; Video
---

### Post by smarble on 2008-02-28
hi, im way new to linux, and getting everything set up here.

now i need to fix the sound issue. ubuntu 7.10 and alsa has picked up that i have a sound card and i believe it knows what it is, its just that nothing is working and ive checked to see that everything is unmuted...any help would be greatly appreciated.

---

### Post by garolou on 2008-02-28
Hi smarble,
take a look here: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
Its a good start to troubleshooting your situation. Good luck.

---

### Post by Toet on 2008-02-28
You could also have a check into the /etc/modprobe.d/alsa-base file.

---

### Post by smarble on 2008-02-28
what am i looking for in that file?

---

### Post by Toet on 2008-02-29
This is the file where your soundcards get configured. If your soundcard is not correctly listed in this file, it does not work. For example if you have a usb-sound card, you should change the first line into:

install sound-slot-0 /sbin/modprobe snd-usb-audio

and comment out:

#options snd-usb-audio index=-2
#options snd-usb-usx2y index=-2

So look if you card is listed under:

# Prevent abnormal drivers from grabbing index 0

if it is then comment it out.

---

