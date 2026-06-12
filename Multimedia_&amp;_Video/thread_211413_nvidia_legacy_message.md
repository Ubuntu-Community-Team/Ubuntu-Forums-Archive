---
title: "nvidia legacy message"
date: 2006-07-08
forum: Multimedia &amp; Video
---

### Post by unisol on 2006-07-08
when i start up dapper i get this message nvidia legacy not found what do i need to do i have an old nvidia tnt2 64 which ran ubuntu without as a last resort i will have to change cards in the meantime any suggestions

---

### Post by Dr. Nick on 2006-07-08
If you get thrown to a command line after the error message try running this command to intall the nvidia-legacy package.

[B] sudo apt-get install nvidia-glx-legacy

[/B]Then run **startx **to try and get back to a graphical interface.

If that doesnt work and you are still in a command line then run

**sudo nano /etc/X11/xorg.conf** and look for the line that says [B]
driver = "nvidia"  [/B]and replace nvidia with "nv" (no quotes) then save and try startx again. The nv driver will not have 3d acceleration but will atleast get you into a gui.

---

