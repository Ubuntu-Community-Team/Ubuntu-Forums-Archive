---
title: "Xorg update and radeon driver install ends up killing X server"
date: 2008-08-04
forum: Multimedia Software
---

### Post by Coolbreeze... on 2008-08-04
Well this post seems to be what I have been searching for for 2 days...[http://ubuntuforums.org/showthread.php?t=32015&page=1...I](http://ubuntuforums.org/showthread.php?t=32015&page=1...I) followed the steps in post #10 plus a few more for the newest Xorg (6.9 I believe). 

Any way all went well I hit CTRL-ALT-Backspace as he said and it went to a black screen with about 4-5 lines of text saying [OK] afterwards. Then it sat...I let it be for 4-5 mins and decided it was waiting for something(this may have been my mistake) anyway being a windows user I tried CTRL-ALT-DEL sure enough it said some stuff started to restart the it loaded to a command prompt (non-gui) Linux. I restarted again and it looks normal the loading bar went across a bit slow the it says



Starting Up...
Loading, please wait...
Kinit: name_to_dev_t(/dev/disk/by-uuid/4e9ae3bb-6b57-4135-babd-ccad41bbbe90) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/4e9ae3bb-6b57-4135-babd-ccad41bbbe90
kinit: No resume image, doing normal boot...

Ubuntu 8.04.1 AJ-laptop tty1

AJ-laptop login:


I then opened the Xorg.0.log 

Says stuff about different fonts missing from 

/usr/X11R6/lib/X11/fonts/*

* misc,TTF,Type1,CID,75dpi,100dpi

then says "Fatal Server Error: No valid Fontpath could be found"

then 9WW) xf86Close Console:*_______Failed: Bad file descriptor


* VT_GETSTATE, KDSETMODE, VT_GETMODE

Thanks

---

