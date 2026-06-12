---
title: "ATI driver problems"
date: 2006-09-01
forum: Multimedia &amp; Video
---

### Post by liberona on 2006-09-01
When i installed the ATI drivers from ati.com i get a lower fps in glxgears then with the mesa drivers.. is this normal? i was getting 300 with mesa and now im getting 125 with the ati drivers... 

sebastian@sebastian-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.6011 (8.28.8)


ohh also is that a bit low to get with this card? thanks for any help!

---

### Post by liberona on 2006-09-01
ok i just found out by someone that my client and server vendor strings should match in glxinfo but they dont... can someone help me fix this?

sebastian@sebastian-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3

---

### Post by andb on 2006-09-03
Where did you find that they should match? Mine definately dont, and all runs fine. Im running an ATI 9250, so not exactly a powerhouse... I had some headaches with the driver, specifically geting the kernel module going. My solution was heavy handed, I booted to another kernel, removed the old kernel, reinstalled, booted back into the ubuntu default kernel, then rebuilt and reinstalled the ati drivers. All is well.

---

