---
title: "Dual Screens - Intel Q35 Graphics Chipset- Solved Works great"
date: 2008-04-28
forum: Multimedia Software
---

### Post by YTTK on 2008-04-28
I finally put enough pieces together from the bug reports to make this work.

1. Ubuntu by default - correctly configured my screens dual 1440 X 900 but in clone mode. when I ran gksudo displayconfig-gtk it showed I was using VESA driver and the screen settings were correct on one but not the second(even though both where working fine in clone mode). I assumed this meant I had a driver issue problem first - wrong!. If it works don't fix it.

2. using the link [http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html) I figured out I needed to add in my xorg.conf file under Section "Screen" I added
SubSection "Display"

Virtual 2880 2880

EndSubSection
3. shutdown or restart
4. run xrandr --output TMDS-1 --right-of VGA
Everything works great of course step 4 needs to be run at every boot and eventually I will figure out how to add this to my xorg.conf.
This was much easer than I thought and we need and updated sticky for those that are just starting. (like me)

---

