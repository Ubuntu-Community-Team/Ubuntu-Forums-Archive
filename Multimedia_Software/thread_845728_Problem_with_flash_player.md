---
title: "Problem with flash player"
date: 2008-06-30
forum: Multimedia Software
---

### Post by Goklagie on 2008-06-30
Hello guys,

yesterday i installed ubuntu 8.04 on my fathers dv9000 laptop. I tried to configure firefox 3 but -stupid enough- I selected the free flash player plugin and not the macromedia one. As a result i have to click to activate flash objects.

Because of the fact that the computer is going to be used from my parents, i want to achieve minimum user interaction:D.

I tried to delete the plugin from /usr/lib/firefox/plugins and from /usr/lib/firefox-3.0/plugins but i have the same problem. I also tried to remove firefox from the terminal with the same result.

Any idea?

---

### Post by gandaran on 2008-07-01
when you install an application from the repositories, use synaptic to install or remove it, just look up swfdec flash ( and gnash too) and check mark for complete removal, look for the flashplugin-nonfree, mark for install and click the apply button.

---

### Post by Goklagie on 2008-07-01
Thnx:D.

---

