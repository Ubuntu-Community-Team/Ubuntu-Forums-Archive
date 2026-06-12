---
title: "usb speaker help"
date: 2009-07-14
forum: Multimedia Software
---

### Post by vkeifreek on 2009-07-14
ok so im running kubuntu 9.04  on an acer aspire one and i have logitech s150 usb speakers well i plug them into the usb port and it shows that there connected in the kmix mixer but the only option in there on volume control is pcm i have no idea how to switch it over to those and everything just continues to play on the onboard speakers some help would greatly be appreciated thanks

---

### Post by igorzwx on 2009-07-14
actually, solution is very simple.
you have already pulse-audio installed, I presume.
Open Synaptic, install all the Pulse tools.
There should be something like pulse control, or pavucontol, or else.
with this thing you can move audio stream where you want with one
click of the mouse.
There should be howto. I tried it, it works.
I cannot help more, because I have already removed both Pulse and ALSA,
and installed an alternative sound system.

google -> ubuntu pulseaudio
google -> markbuntu pulseaudio

---

### Post by igorzwx on 2009-07-14
system -> preferences -> sound
change everything to pulse

---

### Post by erikthedrink on 2009-09-08
I've got logitech usb speakers too.  In Xubuntu, go to Applications, then Accessories, then Terminal.  In Terminal, type

[FONT=Georgia][SIZE=4]asoundconf set-default-card 1[/SIZE][/FONT]

Then close and re-open your browser (Mozilla Firefox) or restart your system.
:guitar:
Note, if you unplug your usb speakers, your laptop speakers will take over.  In order to re-establish contact with the usb speakers, you will need to (plug them back in) restart the system.

---

