---
title: "vlc broken and it does not help to completly remove"
date: 2010-10-24
forum: Multimedia Software
---

### Post by Azyx on 2010-10-24
Someting went wrong with vlc and the window is totally maximated and take up the hole desktop. I can not make it smaller with esc, or trying to grab windows border to make it smaller.
I have made a complet removal in synaptic and downloaded it again with apt-get install vlc, but the problem is still there. When I open vlc, it take up the hole desktop and sceen.

I have 10.04LTS

/cheers

---

### Post by sikander3786 on 2010-10-24
> I can not make it smaller with esc, or trying to grab windows border to make it smaller.

That is something really weird.

Sometimes my VLC also starts in maximised mode or even bigger than my single desktop but that is due to the resolution of my videos.

Does starting VLC alone from Sounds & Video also start it maximised? Are you able to restore and resize it? Or the arrow for resizing does show up when you hover at the borders?

---

### Post by Azyx on 2010-10-24
> **sikander3786 said:**
> That is something really weird.

Sometimes my VLC also starts in maximised mode or even bigger than my single desktop but that is due to the resolution of my videos.

Does starting VLC alone from Sounds & Video also start it maximised? Are you able to restore and resize it? Or the arrow for resizing does show up when you hover at the borders?

Yes. It is even maximized (or super-maximized) with no file added to play and I'm not able to make it smaller. The normal gnome border button, Up and down arrow- and the red exit button up to the left are not there, only vlc-menus are at the top.

I'm not able to make it look like this on a working PC, cos the gnome-menue are always there if I'm not in fullscreen, but then I don't see the vlc-menu.

---

### Post by Azyx on 2010-10-24
Screenshot attached

---

### Post by sikander3786 on 2010-10-24
From terminal, try

```
vlc --reset
```

---

### Post by Azyx on 2010-10-24
> **sikander3786 said:**
> From terminal, try

```
vlc --reset
```

No, It does not help :(, seems only affect how vlc should get album art?  I think the problem maybe are out-side vlc, cos the problems are still there even after a complete removal and a new install. I have notice that there are no hidden .vlc-folder in home in 10.04 or 10.10 as i was on 8.04LTS.

---

### Post by mc4man on 2010-10-24
try either
```
vlc --reset-config
```
or go to home folder (view -> show hidden files) - .config -> vlc  and delete vlc-qt-interface.conf or just delete the vlc folder itself

---

### Post by Azyx on 2010-10-24
> **mc4man said:**
> try either
```
vlc --reset-config
```or go to home folder (view -> show hidden files) - .config -> vlc  and delete vlc-qt-interface.conf or just delete the vlc folder itself

Thanx, It worked :) I erased vlc-folder in home/Azyx/.config/
It seems that the .vlc-folder have move from /home/Azyx to /home/Azyx/.config since 8.04 and the config-files does not disappear when with 'complete remove, including config-files' in synaptic is applied.

/Cheers

---

### Post by trooperchix on 2011-01-11
> **mc4man said:**
> try either
```
vlc --reset-config
```
or go to home folder (view -> show hidden files) - .config -> vlc  and delete vlc-qt-interface.conf or just delete the vlc folder itself

Works!!  Thanks!!

---

### Post by Bill Gates Foundation on 2012-03-07
12.04 it didnt work for me....:lolflag:

---

