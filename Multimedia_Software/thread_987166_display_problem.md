---
title: "display problem"
date: 2008-11-19
forum: Multimedia Software
---

### Post by no1zaman on 2008-11-19
I am having lot of trouble with my GUI :(:(:( some time it will not disply the tool bar,somtimes it will dot display the icons it is creating hell lot of problems plz tell what to do????

---

### Post by sadiqdude on 2008-11-19
I think ur xorg.conf file is not configured properly.to u can repair this in command line press ctrl+alt+f1 u will b taken into a command line interface login with ur name and type following commands:
	$ sudo /etc/init.d/gdm stop (To stop &#8220;Graphics Device Manager&#8221;)
	$ dpkg-reconfigure -phigh xserver-xorg(to reset ur xorg.conf file)
this might help u i hope so........:):):)

---

