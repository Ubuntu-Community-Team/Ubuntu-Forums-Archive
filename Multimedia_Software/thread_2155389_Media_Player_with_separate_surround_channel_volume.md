---
title: "Media Player with separate surround channel volume support"
date: 2013-06-18
forum: Multimedia Software
---

### Post by jasper99 on 2013-06-18
Does anybody knows a working Media Player (maybe in Wine) that support separate surround channel volume changing.
Daum Potplayer does, but that isn't working in Wine.

This is the volume control in Daum Potplayer:
[IMG]http://img163.imageshack.us/img163/8071/zy88.jpg[/IMG]

---

### Post by dargaud on 2013-06-18
In the KDE Mixer volume, I can right-click one of the volume bars and select "Split Channel": it gives me left/right balance. Maybe with more channels you'll get separate volumes as well. I don't know if there's an equivalent in Gnome/Unity.

---

### Post by SeijiSensei on 2013-06-18
The PulseAudio mixer **pavucontrol** *might* offer this.  You can install it from the repositories and test it out.

---

### Post by jasper99 on 2013-06-23
The problem is that i do not have a 5.1 device connected, i want to change volume of serperate surround channels to stereo output.
In this situation **pavucontrol **&#8203;do not work.

---

### Post by dargaud on 2013-06-23
Then if you do not have 5.1 sound devices, why do you select it ? Just use standard stereo !

---

### Post by SeijiSensei on 2013-06-23
Maybe he has content with "matrix" audio in the older Dolby Prologic format.  That encodes the 5.1 signal into 2.0 audio.  It was the broadcast stereo standard until HDTV with DD 5.1 came along.  I have some older anime files with Prologic encodings.  When they are passed to my audio receiver, I get surround.

---

### Post by jasper99 on 2013-07-10
> **dargaud said:**
> Then if you do not have 5.1 sound devices, why do you select it ? Just use standard stereo !

Sometimes you can get turn off a (stupid) laugh track and/or some music into a show (or lower volume), by disabling all channels except the center one.

---

