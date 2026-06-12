---
title: "Gnome desktop flickering with Intel 915M"
date: 2008-11-01
forum: Multimedia Software
---

### Post by Roscoe on 2008-11-01
I'm encountering moderate screen flickering with an Intel 915GM.

Known bug?

---

### Post by rotwang888 on 2008-11-01
Same here.  Wasn't a problem before the upgrade to Intrepid.  It's most obvious when starting up apps under Wine.

---

### Post by rotwang888 on 2008-11-07
bump

---

### Post by haloedrain on 2008-11-22
I'm getting weird graphics problems as well--occasional horizontal line flickers, diagonal stretching/skewing as things are drawn, lines along the top and left of images on web pages that are resized with css, parts of the screen occasionally getting refreshed too slowly....  None of that was happening in hardy heron.

---

### Post by gaalaaant on 2008-11-22
yeah, I am getting it alot especially when I drag windows around

---

### Post by haloedrain on 2008-12-18
I found a case where the diagonal stretch/flicker happens consistently, so here's a screenshot, if it helps anyone.  This is taken in google analytics and I've seen it on many other webpages, but it also happens when the desktop loads and with other applications loading/closing.

[IMG]http://i388.photobucket.com/albums/oo321/haloedrain/Screenshot.png[/IMG]

---

### Post by gatekeeper53 on 2008-12-18
Installed kubuntu 8.10 last nite on a system with Intel 915m. Same type of flicker. Driver installed as 915 not 915m. Is there a difference. If it is not already apparent I'm a 14 hr old newbe.

---

### Post by gatekeeper53 on 2008-12-18
Add to xorg.conf under "Device" as shown in xorg.conf.failsafe.

	Driver		"vesa"

Probably not an ideal solution but at least it does not flicker.

---

### Post by Andreas1 on 2009-02-11
Since 8.10 i get flickers when logging into gnome, opening totem, and constantly with KDE (just added kubuntu-desktop). also intel 915 here.




> **gatekeeper53 said:**
> Add to xorg.conf under "Device" as shown in xorg.conf.failsafe.

	Driver		"vesa"

Probably not an ideal solution but at least it does not flicker.

um, what exactly does this do?

---

### Post by binbash on 2009-02-11
i have same card and on this notebook i have fedora 10 and i have same issue : )

---

### Post by rotwang888 on 2009-04-01
Did today's update solve the problem for anyone?  I was excited to see "Intel" "display" and "xorg", but the flickering remains on my laptop.  Oh well...

---

### Post by justutkarsh on 2009-04-07
I had exact similar problems
this worked for me in gnome intrepid ibex may be this could help you guys


1. add this line to your xorg.conf device section.
Option "Monitor-TV" "TV"
2. add a monitor section
Section "Monitor"
        Identifier "TV"
        option "ignore" "true"
EndSection


source:[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/278146](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/278146)

---

