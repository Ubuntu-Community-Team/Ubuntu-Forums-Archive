---
title: "[SOLVED] Manual Installation of Nvidia Driver Not Working"
date: 2008-06-30
forum: Multimedia Software
---

### Post by toastedcheese on 2008-06-30
Okay, so I recently did a clean install of Hardy Heron, and due to screen resolution problems, decided to install the Nvidia driver manually. The installation went fine, and when I restarted gdm, my resolution was back up to 1024 x 768.

However, the next time I restarted the computer, it was apparently unable to detect the new driver; there were no error messages, but I'm running at low resolution again. I tried reinstalling the driver, but this didn't help. How do I convince the OS that it's supposed to use the new driver?

---

### Post by bijeeshvs on 2008-06-30
for your Driver problem install "envy"
go to "system>administration>synaptic package manager" search for envyng-gtk
and install envy can automatically install and configure gpu drivers for you no worries
run envy from "applications> system tools>envyng"
and select automatic install

it maybe in a different menu in xubuntu any way the info is correct for ubuntu
this is the easy way for newcomers, i think................

---

### Post by xc3RnbFO8P on 2008-06-30
Check if it is a screen problem:
[http://ge.ubuntuforums.com/showthread.php?t=798881]("http://ge.ubuntuforums.com/showthread.php?t=798881")

---

### Post by toastedcheese on 2008-06-30
I just tried Envy; it didn't help.

What would I be looking for in terms of a screen problem? My xorg.conf has 640 x 480 pretty much wherever a screen resolution is called for; would manually changing this make a difference?

---

### Post by xc3RnbFO8P on 2008-06-30
Is your monitor listed in screens and graphics.
There is a problem with some monitors.

---

### Post by toastedcheese on 2008-07-01
My monitor wasn't listed, but I tried selecting the option for a generic 1024 x 768 LCD monitor, and it worked beautifully. I hadn't tried that because it hadn't done anything pre-driver installation.

Thanks!

---

### Post by xc3RnbFO8P on 2008-07-01
Thats great, only if more people would try this
before messing with their graphic card :)

---

