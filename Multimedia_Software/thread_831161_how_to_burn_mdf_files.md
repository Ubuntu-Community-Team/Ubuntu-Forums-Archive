---
title: "how to burn mdf files"
date: 2008-06-16
forum: Multimedia Software
---

### Post by sneeks on 2008-06-16
i am trying to burn a mdf/mds image file to disc,but am having trouble getting any app to do it.
any ideas ????

---

### Post by wolfen69 on 2008-06-16
.mdf and .mds extensions are for Alcohol 120%. probably will not work in linux. Fuseiso will mount these image files, but not sure about burning them.

FUSE module to mount ISO filesystem images
This package provides a module to mount ISO filesystem images
using FUSE.
With FUSE it is possible to implement a fully functional
filesystem in a userspace program.

It can also mount single-tracks .BIN, .MDF, .IMG and .NRG.

 Homepage: [http://fuse.sourceforge.net/wiki/index.php/FuseIso](http://fuse.sourceforge.net/wiki/index.php/FuseIso) can be downloaded via synaptic.

---

### Post by tomhat on 2008-10-12
[b][color=darkblue]I found a guide talking about this issue. I tried it for NRG files & it worked.
It mentioned solutions for other types such as CUE,BIN,MDF & IMG.
Check it out

[http://www.howtodothings.com/computers-internet/how-to-convert-cue-bin-nrg-img-mdf-files-to-iso-files-on-ubuntu-linux](http://www.howtodothings.com/computers-internet/how-to-convert-cue-bin-nrg-img-mdf-files-to-iso-files-on-ubuntu-linux)

Hope it helps :)[/color][/b]

---

### Post by Stratok on 2010-08-13
yeah... mdf2iso did the work...

actually there is a nautilus script to use it...

[http://gnome-look.org/content/show.php/Audio%2BVideo%2BImage%2BText%2BISO+Convert?content=92533](http://gnome-look.org/content/show.php/Audio%2BVideo%2BImage%2BText%2BISO+Convert?content=92533)

will do the job. and of course terminal:
sudo apt-get install mdf2iso


Have anice day...

---

