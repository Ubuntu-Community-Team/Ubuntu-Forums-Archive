---
title: "Personal File Sharing on Xubuntu"
date: 2012-09-05
forum: Networking &amp; Wireless
---

### Post by kleinempfaenger on 2012-09-05
Hi, I want to share some files with the public folder. One mashine uses Ubuntu, and the other one Xubuntu. On Ubuntu I installed gnome-user-share and some other packages, as described in some tutorials. Afterwards appears the "Personal file sharing"-preferences link in the main menu to activate the public folder in home folder. No problem.
On Xubuntu install ok, but then I cant find the link to activate public folder in main menu. Is there a way to open "Personal file sharing" preferences from the terminal, or where might it be hidden?
No Samba please.

Thanks, kl

---

### Post by Morbius1 on 2012-09-05
Command:
```
gnome-file-share-properties
```The problem with it not being in the menu is that the *.desktop laucher created for it forbids it being in any menu other that Gnome. You can fix that by:
```
gksu leafpad /usr/share/applications/gnome-user-share-properties.desktop
```Find the line:
> OnlyShowIn=GNOME;Unity;And change it to XFCE:
> OnlyShowIn=[COLOR=Blue]**XFCE;**[/COLOR][COLOR=Blue]*Don't forget the trailing ";" after "XFCE"*[/COLOR]

---

### Post by kleinempfaenger on 2012-09-05
Oh, thank you Morbius, it worked very well.
This is solved
Greetings, kl

---

