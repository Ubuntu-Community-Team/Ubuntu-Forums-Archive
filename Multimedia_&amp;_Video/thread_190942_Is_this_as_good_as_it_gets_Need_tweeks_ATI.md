---
title: "Is this as good as it gets? Need tweeks ATI"
date: 2006-06-06
forum: Multimedia &amp; Video
---

### Post by disturbed1 on 2006-06-06
Everything is running good and stable. XGL Compiz works fine if I enable it, hardware video playback, dri and gl rendering works.

I seem to have some really poor frame rates though. I'm comparing my nvidia FX5500 vs ATI x1600. ATI did a great improvement from 8.24 to 8.25, but I'm unimpressed with the *power* behind this card. Using UT2004 as a benchmark, the Nvidia card achieve a score of 337 with Umark, the ATI card scored 340. On the different time demos, the cards were neck and neck, with one besting the other and vice versa. In Windows 2000, the ATI card mops the floor with the FX5500, it is at least 2x as powerfull, if not 3x in most games.

So is this an ATI driver problem, and just hold out for the updates, or is there something I can change to see some improvements? No I don't game with XGL/Compiz enabled ;)

```

 $ glxinfo
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

```

```

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series Generic
OpenGL version string: 2.0.5814 (8.25.18)

```

---

### Post by yatt on 2006-06-23
Its a driver issue. ATI has never really been thrilled about Linux. They do seem to be coming around however.

---

