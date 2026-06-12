---
title: "Problem with building gstreamer_ndk_bundle under Ubuntu 12.4"
date: 2012-05-30
forum: Multimedia Software
---

### Post by cipiripper on 2012-05-30
I'm trying to build gstreamer_ndk_bundle under Ubuntu 12.4 and I'm failing miserably! I have installed all "glib-dev" packages (packages that in their name have `glib` and `dev`), and also I have tried to compile/install glib 2.33.1 (latest) from source, but I always get this error:

    ```
/home/marko/gstreamer_ndk_bundle/jni/../glib/gobject/gmarshal.c:149: undefined reference to `g_value_get_schar'
    collect2: ld returned 1 exit status
    make: *** [/home/marko/gstreamer_ndk_bundle/obj/local/armeabi/libgobject-2.0.so] Error 1
```

This means that glib source doesn't have the definition for `g_value_get_schar`, and since that function was introduced in glib somewhere after version 2.30.0, my guess is that I am not using proper glib! 

I tried to force gstremaer_ndk_bundle to build with sources from the folder `/home/marko/glib-2.33.1/` which I compiled/installed by exporting these env vars:

```
    GLIB_GENMARSHAL=/home/marko/glib-2.33.1/gobject/glib-genmarshal 
    GLIB_COMPILE_SCHEMAS=/home/marko/glib-2.33.1/gio/glib-compile-schemas
```


Also I changed `gmarshal.h` so it includes `gmarshal.h` from the installed glib folder:

```
    #ifndef _marko_glib_loaded
    #define _marko_glib_loaded
    #include "/home/marko/glib-2.33.1/gobject/gmarshal.h"
    #endif
```

But failed in both cases.

- How can I know what glib is used while compiling gstreamer and install the proper one?
- How can I force gstreamer_ndk_bundle to use glib sources from the folder I have un-tared/configured/installed and not the system ones, or whatever ones it uses?
- I read somewhere that I need `gstreamer-devel` package if I keep getting this error while compiling. Where can I find that package?! Can't Google it out...
- Has anyone EVER built gstreamer_ndk_bundle and lived to tell the tale?

---

