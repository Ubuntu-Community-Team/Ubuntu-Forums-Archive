---
title: "Can't set screen resolution"
date: 2010-04-02
forum: Multimedia Software
---

### Post by jonathangorsky on 2010-04-02
[COLOR=black][FONT=Verdana][SIZE=3]Hi all[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=3]I'm new with Linux (about 5 days of experience).[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3]I'm having problems adjusting my screen resolution.[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3]I'm using Nvidia Geforce FX5300 video card and Samsung T220P LCD screen with resolution of 1920x1200.[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3]After installing the Nvidia driver I went to system -> preferences -> display in order to change the resolution to 1920x1200. Unfortunately, the available resolutions were only 640x480 and 320x240.[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3]I tried to set the resolution manually, using the advanced button, but when I did this everything was extremely big on my screen.[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3]I'm pretty lost here/[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=3]Can anybody help me with this issue?[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=3]Thanks.[/SIZE][/FONT][/COLOR]

---

### Post by jsmthjsmith83 on 2010-04-02
I think the easiest would be just to edit your XF86Config file in /etc/X11. 
Look for the Screen section and change the mode from 800x600 to 1024x768 or add it in front. Mine for example looks like...
 Section "Screen"
    Identifier  "Screen0"
    Device	 "Videocard0"
    Monitor	"Monitor0"
    DefaultDepth	  24
    SubSection   "Display"
 		   Depth    24
 		   Modes    "1024x768" "800x600" "640x480"
 	EndSubSection
 EndSection
after you will not find proper reason than you can visit Linux website.

---

