---
title: "how to manually add programs to ubuntu studio"
date: 2006-06-14
forum: Multimedia &amp; Video
---

### Post by falkenberg_cph on 2006-06-14
Hey
Written this before as a subquestion  under a different topic.

How can i manually add programs that doesnt show up in ubuntu studio.

Carsten

---

### Post by dolson on 2006-06-14
Easiest way that doesn't involve modifying the source code would be to simply put a .desktop file for the app into /usr/share/applications/.

---

### Post by falkenberg_cph on 2006-06-15
Ok. This does not not seem to help me. Im new to linux, so here is how i did, maybe its wrong:

First i went to programs/sound and video in the desktop menu, and created a desktop shortcut to ZunAddSubFX.

Second i did this in terminal:

cd Desktop
sudo cp hadjaha-somenumbers.desktop /usr/share/applications

Was this correct?

Carsten

---

### Post by dolson on 2006-06-15
Yes, but does that app show up in your menu now? It will only show up in the launcher if the category includes Audio.

---

### Post by falkenberg_cph on 2006-06-16
Yes, it is in the audio section. it was there allready before i made the copy of the .desktop file.

Carsten

---

### Post by dolson on 2006-06-17
Just because it was in the menu doesn't mean the file was located in the correct place.

Also, the categories are probably incorrect in the file that you put into /usr/share/applications. There are lots of different categories and not every distro/developer follows the same guidelines for creating a .desktop file.

Look at the file and find the line that looks like this:

Categories=GNOME;GTK;Application;AudioVideo;X-Ximian-Main;X-Red-Hat-Base;

See how many categories are there? The one that the USL looks for is the AudioVideo category. Make sure it's in the file.

The ZynAddSubFX deb puts the .desktop file here:
/usr/share/gnome/apps/Multimedia/zynaddsubfx.desktop

On my system, it doesn't even specify the category:

dana@polly:~$ cat /usr/share/gnome/apps/Multimedia/zynaddsubfx.desktop
[Desktop Entry]
Name=ZynAddSubFX
Comment=ZynAddSubFX Software Synthesizer
Exec=/usr/bin/zynaddsubfx
Terminal=false
Type=Application
Icon=/usr/share/pixmaps/zynaddsubfx.xpm
dana@polly:~$

---

### Post by falkenberg_cph on 2006-06-17
Allright, thank you, that helped.

---

### Post by oldgoat on 2006-08-15
this helped me as well - thank you

---

### Post by dolson on 2006-08-17
I have put an updated version on the app's homepage in the wiki, which will read in other locations other than the single location I had before. Not sure how to get it updated in Dapper though.. Soon I will ask some of the guys for help on that... When I have free time for it.

---

### Post by pjrodz on 2007-11-09
> **falkenberg_cph said:**
> Hey
Written this before as a subquestion  under a different topic.

How can i manually add programs that doesnt show up in ubuntu studio.

Carsten

may i ask how you installed the rhds in ubuntu? i already have the jar file but i dunno what to do with it..thanks!

---

