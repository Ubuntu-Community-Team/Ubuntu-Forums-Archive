---
title: "Unable to create new X config file - &quot;/etc/X11/xorg.conf&quot;"
date: 2009-02-04
forum: Multimedia Software
---

### Post by Sillywombat on 2009-02-04
Hi, i have been using ubuntu 8.04 for a while now, and have been using my X server for a dual screen setup for a while. 

But then °°flash, bang, horror:!:°° My graphics card goes. Iv since replaced it, and gave my pc a new install, again, 8.04. Card is a nvidia GeForce 7600 GT. (nvidia drivers installed)

Everything went well, until i tried to change my screens into seperate X screens, which requires the X server to restart. Easy right? But i cant seem to rewrite my xorg.conf file, or my backup xorg.conf file. Meaning if i do restart the computer, im left back at the start.

Error message is [PHP]"Unable to create new X config backup file '/etc/X11/xorg.conf.backup'"[/PHP]

I checked it out, and it seems i can only change the file via root. How would one do that?
Any help on this would be great, iv been fiddling for a few days to no avail.

---

### Post by Harbard on 2009-02-04
I think I can fix that.

Open a terminal
type:  sudo su
enter your password
type:  nvidia-settings

You should be good to go.

---

### Post by jpeddicord on 2009-02-05
This thread or post has been moved from the Desktop Effects & Customization forum as the posted content is considered off-topic.

Desktop Effects & Customization is a forum for discussing:
[LIST]
[*]Compositing managers such as Compiz
[*]Themes (window themes, widget themes, backgrounds, etc)
[*]Appearance preferences
[/LIST]
Your post did not fit any of these categories, so it has been moved.

Common types of off-topic threads include:
[LIST]
[*]GNOME/KDE/XFCE help in general
[*]Hardware problems not directly related to compositing
[/LIST]

Thanks,
Jacob

---

