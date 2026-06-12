---
title: "Coolbits &amp; Nvidia"
date: 2006-03-11
forum: Multimedia &amp; Video
---

### Post by Coolit on 2006-03-11
I'm using coolbits successfully to overclock my Nvidia 6600 GT Ultra, This card is designed to be overclocked being the ultra version and clocks really well (550/1200). 

The thing is I have to manually go into the driver prefs each time I boot my pc and re-apply the settings, is there any way to set the clock settings so they stay set after a re-boot?

Its no biggie but would save me a little hassle as sometimes I forget to make the change before going into on-line games. :cool:

---

### Post by WildTangent on 2006-03-12
Have you checked out the nvclock utility yet?
```
sudo apt-get install nvclock nvclock-gtk
```
You then run it with nvclock-gtk in the terminal, or maybe it puts a launcher in the Applications list. In the later case, do
```
killall gnome-panel
```
to refresh the list without rebooting or logging out.

-Wild

---

