---
title: "Ambiance/Radiance Panel Transparency"
date: 2010-09-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by simonchimera on 2010-09-09
[FONT=Arial]Has anyone figured out how to give full transparency to the Ambiance and Radiance panels? [The old quick fix]("http://ubuntuforums.org/newthread.php?do=newthread&f=385") for this on Lucid was by commenting out the line

[/FONT][FONT=Arial]bg_pixmap[NORMAL] = "panel_bg.png"

[/FONT][FONT=Arial]in /usr/share/themes/Ambiance/gtk-2.0/gtkrc but this does not seem to work now  as the themes have been updated. Any help would be appreciated.

[Picture of problem]("http://www.rebelzero.com/wp-content/uploads/2010/03/lucid_panel_ambiance_transparency_broken.png")



[/FONT]

---

### Post by nilarimogard on 2010-09-09
Now it's a different file. See in /usr/share/themes/Ambiance/gtk-2.0/apps - edit the gnome_panel.rc file (remove "bg_pixmap[NORMAL] = "img/panel.png"")

---

### Post by simonchimera on 2010-09-09
> **nilarimogard said:**
> Now it's a different file. See in /usr/share/themes/Ambiance/gtk-2.0/apps - edit the gnome_panel.rc file (remove "bg_pixmap[NORMAL] = "img/panel.png"")

Thank you, works perfectly!

---

### Post by nilarimogard on 2010-09-11
You're welcome!

---

### Post by simpleblue on 2010-09-11
> **nilarimogard said:**
> Now it's a different file. See in /usr/share/themes/Ambiance/gtk-2.0/apps - edit the gnome_panel.rc file (remove "bg_pixmap[NORMAL] = "img/panel.png"")

I've been wondering how to do this for a long time.

Thank you!

---

### Post by Sand &amp; Mercury on 2010-09-11
If you're using Compiz for compositing, install and open compizconfig-settings-manager, enable 'opacity brightness and saturation', go into its settings, add a new rule under 'window specific settings', set the rule as 'class=Gnome-panel' and the opacity to whatever you like.

I find this is a better solution than using fake PNG transparency because it makes the panel truly transparent (ie. windows will show through it and everything)

---

### Post by x-shaney-x on 2010-09-12
> **Sand & Mercury said:**
> If you're using Compiz for compositing, install and open compizconfig-settings-manager, enable 'opacity brightness and saturation', go into its settings, add a new rule under 'window specific settings', set the rule as 'class=Gnome-panel' and the opacity to whatever you like.

I find this is a better solution than using fake PNG transparency because it makes the panel truly transparent (ie. windows will show through it and everything)

But the problem with that is that it also makes any panel icons, indicators etc transparent.
Even with only a little transparency the icons look faded at least.

---

