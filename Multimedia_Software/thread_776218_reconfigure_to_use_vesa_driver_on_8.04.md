---
title: "reconfigure to use vesa driver on 8.04?"
date: 2008-04-30
forum: Multimedia Software
---

### Post by johnny9794 on 2008-04-30
I am using the newest ubuntu, on 7.10 i was able to use dpkg-reconfigure xserver-xorg in recovery mode to manually select vesa, I tried dpkg-reconfigure xserver-xorg in the newest ubuntu and all i can reconfigure is the kboard stuff, how would i go about reconfiguring w/e to use vesa driver instead of vga?

thanx.

EDIT: i nano xorg at recovery and just manually typed in

Driver   "vesa"

into the video part, it works now, in xorg by default, xorg or w/e does not pick anything up by itself by default? not my regular wheel mouse, Not even my monitor, meaning i gotta edit everything by hand in xorg? "don't answer that question, no need to" for the help of this problem, i got none but thats ok, thanx for the support :/.:(

---

### Post by nparayo on 2008-06-25
can anybody help me with this im new at this when i type in

nano xorg

it brings up this text editor and i have no idea how to edit the driver? any help

---

