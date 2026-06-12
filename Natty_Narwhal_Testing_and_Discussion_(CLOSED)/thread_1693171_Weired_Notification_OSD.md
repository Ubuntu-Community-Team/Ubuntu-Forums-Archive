---
title: "Weired Notification OSD"
date: 2011-02-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jackallen0714 on 2011-02-22
My notification osd looks weired. see the pic. Anyone know how to solve it?

---

### Post by cariboo on 2011-02-22
That's what I get when I use the function keys to turn the volume up and down

---

### Post by terry_gardener on 2011-02-22
my volume notifications OSD looks normal. 

i am using the nvidia-current driver and xorg 1.9

---

### Post by go7Ul1ai on 2011-02-22
I have this issue too, on an intel integrated graphics chip set.

---

### Post by cariboo on 2011-02-22
I don't think I understand what the problem is, are you saying, that you are getting what is in the op's screenshot when accessing the sound icon in the top panel? See the screenshots shot1.png is using the multi-media keys on my keyboard, shot2.png is accessing the sound icon in the top panel.

---

### Post by gooeykablooey on 2011-02-22
I'm guessing the problem that it looks like the bottom 5 (?) pixels of the notify display have been cut off, so the nice rounded edges have disappeared, and therefore everything isn't centered vertically in the notify bubble.

EDIT: Just updated Unity and encountered the same problem with both the sound "bubble" and the network manager one

---

### Post by Framli on 2011-02-23
Same issue on Intel too, also had it when xorg-edgers was enabled.
It's a pixman bug : [https://bugs.launchpad.net/notify-osd/+bug/670785](https://bugs.launchpad.net/notify-osd/+bug/670785)

---

