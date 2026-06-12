---
title: "How to set VLC as default DVD player in UBuntu 10.04 LTS?"
date: 2010-10-07
forum: Multimedia Software
---

### Post by madmax75 on 2010-10-07
How do I set VLC as the default DVD player in Ubuntu 10.04 LTS?

There seems to be no obvious way to change in which player the DVD's  open up in - you can only choose the default media player, but this is  not what I want to do.

I would like VLC as a default for DVD viewing only - I use Totem for other video files. I used Kaffeine for a while to play DVD's, but found VLC to be superior, especially in DVD menu support.

I know there are threads about how this is done in previous versions (like in 8.04 and so on), but I'm not sure if those still apply for 10.04? Through gconf-editor :confused:

---

### Post by mc4man on 2010-10-07
2 of a half dozen ways
open File Management - Media
ubuntu has decided not to have it as a visible menu item - one way to open, in a terminal
```
nautilus-file-management-properties
```

put a dvd in the drive and hold the shift button down till you get a pop up, vlc should be in the dropdown list

---

### Post by madmax75 on 2010-10-08
Yep, that worked! Problem solved.

Hmm, I wonder why exactly did they hide File Management in the first place? It is in the menus, but it's ticked off (right-click on top of Menu applet -> Edit Menus). If I'm not entirely wrong, File Management used to be visible in the menus before?

It would be nice to include File Management as a default in the menus in upcoming Ubuntu releases. The Default Applications that is in System-> Settings is just too simplistic (*cough*Windows!*cough*). File Management gives you more granular control.

So, problem solved, many thanks mc4man :P

---

