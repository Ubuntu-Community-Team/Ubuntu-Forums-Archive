---
title: "Help with xrandr after xgl uninstall"
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by tlawson on 2007-11-01
I have a Lenovo X61 tablet with an installation of Gutsy (an upgrade from Feisty) and set up automatic screen rotation based on the instructions in:
[http://luke.no-ip.org/x60tablet/]("http://luke.no-ip.org/x60tablet/")
However, I was simply using the intel video drivers at the time.

I then tried installing xgl to get compiz fusion working, but this broke xrandr (with the same problem as [http://ubuntuforums.org/showthread.php?t=571366]("http://ubuntuforums.org/showthread.php?t=571366")) and I tried to back out by uninstalling it.

However, now there are a multitude of graphical glitches which appear whenever I use xrandr to rotate the screen - windows are not fully drawn.  I have tried switching down to the i810 drivers (which had problems detecting my monitor properly), but no luck.

I'm fairly new to Ubuntu and am not really even sure how to "clean the slate" and start over.  Can anyone let me know how to do this?

---

### Post by tlawson on 2007-11-02
update: after doing a clean install of gutsy, the same problem still crops up.  it appears I may have not investigated thoroughly enough before 

according to lspci, the graphics card is an Intel Mobile GM965/GL960 Integrated Graphics Controller (rev 0c).

attempting to edit my xorg.conf to use the i810 driver instead of the intel driver leads to multiple screen flashes when X starts, followed by me being forced into low-resolution mode.

any workaround would be really appreciated; it's difficult to to be happy using the tablet horizontally.

--
Tyler.

---

