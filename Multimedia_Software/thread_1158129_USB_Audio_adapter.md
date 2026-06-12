---
title: "USB Audio adapter"
date: 2009-05-13
forum: Multimedia Software
---

### Post by Astrangeman on 2009-05-13
Hello,
 The jack socket in my laptop is damaged so I would like to use an USB adapter rather than pay a new soundcard. I bought one, based on the C Media CM108 chip but the GNOME volume-control (I use Heron and plan to upgrade to Jaunty one of these days) would only recognise Speaker ant Micro channels. There is no driver for CM108 on Alsa project site.
 Is there any way of getting this thing to work? And if not (which seems to be more probable) could anyone advise me on how to choose an adapter that will work?

---

### Post by markbuntu on 2009-05-15
What exactly are you trying to do?

---

### Post by erikthedrink on 2009-09-08
I've got logitech usb speakers.  In Xubuntu, go to Applications, then Accessories, then Terminal.  In Terminal, type

[FONT=Georgia][SIZE=4]asoundconf set-default-card 1[/SIZE][/FONT]

Then close and re-open your browser (Mozilla Firefox) or restart your system.
:P
Note, if you unplug your usb audio adapter, your laptop speakers will take over.  In order to re-establish contact with the usb audio adapter, you will need to (plug it back in) restart the system.

---

### Post by AnotherDave on 2010-06-30
> **markbuntu said:**
> What exactly are you trying to do?

I believe he is trying to use the highly-popular CM108-based $10 USB sound adapter.

I haven't had much luck with mine either, not on Ubuntu, not on Debian.

Works fine on XP.

---

