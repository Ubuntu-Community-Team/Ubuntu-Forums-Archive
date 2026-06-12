---
title: "video error message"
date: 2007-07-31
forum: Multimedia &amp; Video
---

### Post by wpshooter on 2007-07-31
What does the following message that I receive when I run glxgears at the terminal mean ?

[B]glxgears
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try running with LIBGL_THROTTLE_REFRESH and LIBL_SYNC_REFRESH unset.[/B]
 

Am running Feisty 7.04 with an ATI Radeon 7000 video card.

Thanks.

---

### Post by eneko on 2008-02-01
I am also interested. I have got an ATI RADEON RV100 (RADEON 7000/VE too and 3D aceleration working with the ati driver included in gutsy. glxinfo reports at the beginning
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try running with LIBGL_THROTTLE_REFRESH and LIBL_SYNC_REFRESH unset.

direct rendering: Yes

any suggestions?

thanks

---

### Post by muusikko on 2008-02-09
Hardy alpha 4 live cd,  laptop with Via K8M800

ubuntu@ubuntu:~$ glxgears 
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try running with LIBGL_THROTTLE_REFRESH and LIBL_SYNC_REFRESH unset.

---

### Post by scradock on 2008-02-17
Same error message when trying to run Googleearth with R300 Project open-source driver on Hardy 32-bit.  Seems like an OpenGL bug; I'm going to file a launchpad report.

---

