---
title: "Can I Modify Resolution After Edgy Install?"
date: 2007-04-08
forum: Multimedia &amp; Video
---

### Post by greggfathead on 2007-04-08
Hello - I have a widescreen laptop that requires a resolution of 1280 x 768.  A friend of mine just  put a clean install of Edgy on here (he configured KNetwork Manager for me to get my wifi running) and the only resolutions I can get out of the box is 1024 x 768.  Can I edit a file to change this resolution setting to add 1280 x 768, or do i need to do something else?

Note: I have had that 1280 x 768 res supported on this box before, but in Dapper.  I had to do a text-based install to get the resolution set on here correctly.

---

### Post by spin2cool on 2007-04-08
Try editing your /etc/xorg.conf file, and adding the resolution you want to the appropriate places.

When you're done editing, save it, then hit CTRL-ALT-F1 to get a terminal, then type "sudo /etc/init.d/gdm restart"

and to prevent a huge amount of frustration
:) (BACK UP THE XORG.CONF FILE BEFORE SCREWING WITH IT!!)  :)

---

