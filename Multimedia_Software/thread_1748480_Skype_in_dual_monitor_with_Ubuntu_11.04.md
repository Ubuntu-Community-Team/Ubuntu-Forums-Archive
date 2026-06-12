---
title: "Skype in dual monitor with Ubuntu 11.04"
date: 2011-05-03
forum: Multimedia Software
---

### Post by Luc484 on 2011-05-03
Hi! I noticed in the new Ubuntu 11.04 with Unity, when in dual monitor the icon of skype is not placed in the tray when "closed". It is only placed in the background, so that I have to kill the process and open a new one.

To be sincere, I see a strange aspect of the entire tray when in dual monitor.

Is anyone else noticing the same?

Thanks!

---

### Post by o0o on 2011-05-03
Just found a fix which worked for me. Are you using "Classic" (eg Gnome) Ubuntu desktop? If so, **killall gnome-panel** in terminal works for me. Found the solution [here]("https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/155412").

---

### Post by Luc484 on 2011-05-04
No, I'm using Unity. I've never noticed this issue with Gnome.

---

### Post by Luc484 on 2011-05-04
In case I wanted to report this as a bug, what process should I pass as the parameter of the ubuntu-bug command?
Thanks!

---

