---
title: "ATI Radeon 9600 on 7.04 Server"
date: 2007-07-26
forum: Multimedia &amp; Video
---

### Post by PDWorsnop on 2007-07-26
Hi, 

I've recently installed a LAMP using the 7.04 installer CD and booting into the standard terminal everything works fine.  However, i also wanted to use the server to play media through my TV as a semi-HTPC. so i installed the ubuntu desktop using sudo apt-get install ubuntu desktop (having already updated and upgraded the repos etc).

On restarting the visual ubuntu load screen appears fine, before i am kicked back to a terminal log on (i disabled auto start as i want to be running without a desktop 95% of the time) but when i type startx at the terminal my monitor screen goes blank and comes up with the error "720 x 400 mode not supported" i've looked through the xorg.conf only to find that res wasn't in there. None the less i set the default depth and res to 16bit and 800x600 but still the problem occurs. Any ideas?

Paul

---

### Post by djxcon on 2007-07-26
Hi Paul,

I'm not familiar with LAMP, but have you tried running the following command:

```
sudo dpkg-reconfigure xserver-xorg -phigh
```


I have had some luck choosing the Generic VESA driver with an ATI 9600.  Once X is able to start you can then modify the xorg.conf.

---

### Post by PDWorsnop on 2007-07-26
Yeah i tried that. No joy. It's not the ability to set the resolution that's the problem, i've done that in the xorg.conf; it's just the fact that it ignores it. I'm going to try a manual install of the latest ati drivers tonight and see if that helps at all.

---

