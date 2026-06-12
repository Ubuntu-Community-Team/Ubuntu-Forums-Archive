---
title: "laptop to tv.. help"
date: 2008-05-29
forum: Multimedia Software
---

### Post by no1cares on 2008-05-29
ok, so i tried connecting my laptop to tv via vga cable. and it ended up with my screen resolution getting stuck on 640x480 and could not change.... had to  re-format... dont want to do that again..
 when i connected my laptop to my tv (vga cable). i tried ctrl+atl+backspace, but it did not show up on tv, so i went to "sudo displayconfig-gtk" "screen 1" is set on default and the resolution is set "1600x1024"....... i choose "screen 2" it is "disabled" so go to make it "secondary screen" and "mirror default screen" when i choose that (i get an error ill post at bottem), and if click back to "screen 1" it is also set on "secondary screen" "mirror default screen", the resolution is not listed and cant select one.... first time i ignored it and got it to show up on my tv, but when i went back to computer it was stuck on that messed up resolution and no other resolution was listed..

question... when i choose "screen 2" and make that "default" 800x600 is highest resolution listed so i have to use that. :( . (is 800x600 supported?lol) but it makes "screen 1" "disabled" this is ok. because i can change it back to "screen 1" from my tv when done. when i change it back to "screen 1" from tv, can i put it back on my good resolution or will it screw up again??... will that work? im a little hesistate to try... 

error when i get when i choose "screen2" "secondary screen" "mirror default screen"
```
laptop:~$ sudo displayconfig-gtk
[]
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/displayconfiggtk/DisplayConfig.py", line 620, in on_radiobutton_clone_toggled
    self.xsetup.setLayout(XSetup.LAYOUT_CLONE)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 972, in setLayout
    gfxcard.setLayout(XSetup.LAYOUT_CLONE)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1184, in setLayout
    screen._resyncResolution()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1861, in _resyncResolution
    self.gfx_card.setup.getPrimaryScreen()._resyncResolution()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1817, in _resyncResolution
    (preferred_width,preferred_height) = self.getAvailableResolutions()[-1]
IndexError: list index out of range




```

---

