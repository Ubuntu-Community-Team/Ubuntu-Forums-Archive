---
title: "hey xorg, what's wrong... mergedfb? =("
date: 2006-03-21
forum: Multimedia &amp; Video
---

### Post by toad013 on 2006-03-21
i recently switch from a year of Suse to ubuntu... its been 3 days and my linux-eyebags are getting really bad... anyways i'm running an ati x600 pci-e and i've managed to get the new drivers up and running properly... however i can't get my dual-head to work properly... i can get 2 screens with 2 sessions... but i want a xinerama style where it's one big desktop where each window knows the boundaries of the monitor. 
if i use the option "xinerama" "true"  it will work but i lose 3d accel and i'm no longer running the ATI drivers... i seemed to stumbled on mergedFB which i think is supposed to give me xinerama style with 3d support... but i can't get the damn thing working right... the closest i've gotten to making it work is running the "force-monitor" option but i can't change resolutions...

however... 

if i add "DesktopSetup=horizontal" i can get it to run but only 1 monitor will show the desktop ... the other monitor will show a brown background and a little of the cursor if i try to move it over, the cursor is bounded by the viewable monitor but applications, icons, and whatnot are on the otherside (thank god for hotkeys alt-f7)...  if i run "DesktopSetup=horizontal,reverse" i get the other monitor working and the other one is blank.... the best part is, on the logon screen it works exactly the way i want it to (mouse moves freely between the two)

help me , please...

[my xorg 82 hours later from start]("http://www.gotmindcandy.com/linux/xorg.conf")

---

### Post by toad013 on 2006-03-22
oh. i got it.
just installed dapper and works perfectly.

---

