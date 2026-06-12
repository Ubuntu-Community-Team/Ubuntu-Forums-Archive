---
title: "Ubuntu not recognising mp3 player &amp; phone"
date: 2010-04-06
forum: Multimedia Software
---

### Post by Supermancav on 2010-04-06
For starters I'm running on Ubuntu 9.10

The problem is I can't get the system to recognise my phone(Rant) or my mp3 player(Sansa), it will recognise anything else I put in any of the USB ports, like mouse&keyboard, cooling pad, and modem(the 3 things i currently have connected to it).  It even recognises my Flash Drives, but it won't recognise my phone or my mp3 player.

Some help would be greatly appreciated, does anyone know why it would be doing this or if I'm just doing something wrong?  Also, I've been using Ubuntu for a short time so use beginners jargon if you can please.

I can get any other information you may need about the system if you ask.

Thanks =]

(Edit: I placed it in Multimedia & Video since they're both for music & video, and if it's the devices issue it would belong in here, but if there's still a forum better suited for it I apologise)

---

### Post by andrea000 on 2010-04-08
What kind of phone and mp3 player do you have?Sansa clip fuse etc.
is it on the libmtp list of players you can take a look [here]("http://libmtp.sourceforge.net/compatibility.php") to see.
Also you may look to see if it is a mtp player or if it has to be
mounted as a hard drive.

---

### Post by Chronon on 2010-04-08
I connect each of my Sansas (Clip v1 and e280 v1) via MSC protocol so they just appear as UMS devices on my system.  If you want this you can set the USB mode on the player to MSC.

---

### Post by hugmenot on 2010-04-09
I had the same issue. It somehow doesn’t work if you set USB protocol to »auto« but it works when you choose »mass storage«.

---

