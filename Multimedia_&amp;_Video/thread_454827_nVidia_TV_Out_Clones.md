---
title: "nVidia TV Out: Clones?"
date: 2007-05-25
forum: Multimedia &amp; Video
---

### Post by osxdude on 2007-05-25
Is it currently possible to show a clone instead of a desktop extension? I want to have my desktop show on two screens; the same image on both, however.

Anyone know how?

---

### Post by fenian on 2007-05-25
If you have the latest nvidia drivers open a terminall and type...

> sudo nvidia-settings

this will bring up a gui where you can set up twinview or seperate x (allows you to use each screen independently, watch video on tv while surfing the web on the monitor).Click the  X server Display configuration iin the list on the left click the configure button in the main screen and choose twinview,then go to the pull down menu next to positions and choose clones.Click the save to xconfiguration button exit the program and restart x (ctrl+alt+backspace).

if you dont have the newer nvidia drivers use the [envy script]("http://www.albertomilone.com/nvidia_scripts1.html") to get them

---

### Post by osxdude on 2007-05-27
uh oh...

A nVidia driver install ruined X. It is the driver's kernel.

EDIT: I uninstalled it, and tried to clean it too. Now it's downloading restricted modules.

---

