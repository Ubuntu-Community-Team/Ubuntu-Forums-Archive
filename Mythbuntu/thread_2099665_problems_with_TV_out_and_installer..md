---
title: "problems with TV out and installer."
date: 2012-12-30
forum: Mythbuntu
---

### Post by Rob Hodge on 2012-12-30
so, I've picked up a box to build into my mythbuntu server. 

it's got an Nvidea graphics card, although i have not gotten far enough to get the exact model.

the display is a NTSC TV on the S-video port of said graphics adapter.

so, when i boot it, it posts and displays normally to the screen. 
the install CD displays the first 'mythbuntu' splash screen.

it's this one (image lifted from the mythbuntu site)
[http://www.mythbuntu.org/_/rsrc/1353521018179/home/booting.png?width=200](http://www.mythbuntu.org/_/rsrc/1353521018179/home/booting.png?width=200)

resolution and display is perfect. if i press f4 i go into the normal boot option menu and this is fine as well. 

However, if left aone or told to install from the f4 menu, the next splash screen comes up; the one with 'mythbuntu' and 4 dots under it.  
this one is scrolling off the screen, out of sync. as is anything that comes later. 

is there anyway to force it to stick with the resolution and sync settings that it is using when it first boots? i've fiddled with adding VGA=### in on the boot parameters, but nothing seems to change it.

---

### Post by uteck on 2012-12-31
I think the last option has the nomodeset option which you need.  Or you can manually add that to the boot line.  Yo will also have to add that to /etc/default/grub after you install the system.  Look for GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" and add nomodeset after splash.
Then update-grub so it makes the new boot options.

---

