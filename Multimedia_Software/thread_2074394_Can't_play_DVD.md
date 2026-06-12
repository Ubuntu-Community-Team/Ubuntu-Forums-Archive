---
title: "Can't play DVD"
date: 2012-10-21
forum: Multimedia Software
---

### Post by Romu on 2012-10-21
Hi there,
I've just made a fresh install of Ubuntu Gnome Remix 12.10 with the Gnome 3 ppa as well. Installed the restricted package, and run the script to install libdvdread4. And I can't play DVD with Totem, now named "Videos".

Here is the output I get when I run totem in a terminal:

```
libdvdread: Using libdvdcss version 1.2.12 for DVD access
libdvdread: Attempting to use device /dev/sr0 mounted on /media/romu/TARZAN_AND_JANE for CSS authentication
libdvdnav: Using dvdnav version 4.2.0
libdvdread: Using libdvdcss version 1.2.12 for DVD access
libdvdread: Attempting to use device /dev/sr0 mounted on /media/romu/TARZAN_AND_JANE for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000122
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000317
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00006276
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001aff0a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001b0080
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
libdvdnav: Language 'fr' not found, using 'en' instead
libdvdnav: Menu Languages available: en 
libdvdnav: Language 'fr' not found, using 'en' instead
libdvdnav: Menu Languages available: en 
libdvdnav: Language 'fr' not found, using 'en' instead
libdvdnav: Menu Languages available: en 
libdvdnav: Language 'fr' not found, using 'en' instead
libdvdnav: Menu Languages available: en 
libdvdnav: Language 'fr' not found, using 'en' instead
libdvdnav: Menu Languages available: en 
libdvdnav: Language 'fr' not found, using 'en' instead
libdvdnav: Menu Languages available: en 
libdvdnav: Language 'fr' not found, using 'en' instead
libdvdnav: Menu Languages available: en 
libdvdnav: Language 'fr' not found, using 'en' instead
libdvdnav: Menu Languages available: en 

(totem:2662): GStreamer-CRITICAL **: gst_caps_append: assertion `IS_WRITABLE (caps1)' failed

(totem:2662): GStreamer-CRITICAL **: gst_caps_append: assertion `IS_WRITABLE (caps1)' failed

(totem:2662): GStreamer-CRITICAL **: gst_caps_append: assertion `IS_WRITABLE (caps1)' failed

``` 

I also installed and run regionset, same. Note that DVD playback works with VLC.

Thanks for the help.

---

