---
title: "ATI 8.27.10, poor performance with X800XT PE"
date: 2006-08-08
forum: Multimedia &amp; Video
---

### Post by Padraic on 2006-08-08
I hope someone can help, I'm about ready to pull my hair out.

I originally installed the 8.26.18 version of ATI's drivers using method 2 in the instructions found [here]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide").  

Then the 8.27.10 drivers were released and I followed the same instructions (method 2) to install the updated drivers.

With the 8.26.18 drivers I was getting over 10,000 fps (not a typo) using 'glxgears -printfps' but crappy performance with xscreensaver.  I know, I know, glxgears is NOT a benchmarking tool, but bear with me...

Now with the 8.27.10 drivers, I get about 300fps with glxgears and even crappier performance with xscreensaver.  To top it all off, the computer locks up hard when logging out of an account before it gets back to GDM.

fglrxinfo give me this:

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT Platinum Edition Generic
OpenGL version string: 2.0.5946 (8.27.10)
```

and glxinfo gives me this:

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
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT Platinum Edition Generic
OpenGL version string: 2.0.5946 (8.27.10)
<snip>

```

And the worst part, I can't seem to get back to the 8.26.10 drivers...

I would really appreciate any help!  [-o<

Patrick

---

