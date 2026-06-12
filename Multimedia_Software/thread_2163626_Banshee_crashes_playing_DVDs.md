---
title: "Banshee crashes playing DVDs"
date: 2013-07-19
forum: Multimedia Software
---

### Post by ahardy66 on 2013-07-19
I just upgraded to Raring Ringtail and I decided to start using Banshee, it looks great and integrated DVDs and videos is a major plus point.

I've got libdvdcss2 installed and gstreamer-ugly.

I have the option in the Extensions preferences checked to play DVDs and CDs.

Banshee won't list the DVD in its browser panel unless it's mounted, and when I click the entry to play the mounted DVD it just crashes. 

```

libdvdread: Using libdvdcss version 1.2.12 for DVD access
*** Zero check failed in ifo_read.c:570
    for vmgi_mat->zero_3 = 0x00000000010000000000000000000000000000
libdvdnav: Using dvdnav version 4.2.0
libdvdread: Using libdvdcss version 1.2.12 for DVD access
*** Zero check failed in ifo_read.c:570
    for vmgi_mat->zero_3 = 0x00000000010000000000000000000000000000
libdvdnav: DVD Title: Sandmann
libdvdnav: DVD Serial Number: 3b1f5a2b
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/adam/.dvdnav/Sandmann.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000011d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00005d30
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00005f9a
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
libdvdnav: Language 'en' not found, using 'de' instead
libdvdnav: Menu Languages available: de 
libdvdnav: Language 'en' not found, using 'de' instead
libdvdnav: Menu Languages available: de 
libdvdnav: Language 'en' not found, using 'de' instead
libdvdnav: Menu Languages available: de 
libdvdnav: Language 'en' not found, using 'de' instead
libdvdnav: Menu Languages available: de 

*** libdvdread: CHECK_VALUE failed in nav_read.c:264 ***
*** for dsi->dsi_gi.zero1 == 0 ***

libdvdnav: Language 'en' not found, using 'de' instead
libdvdnav: Menu Languages available: de 

(Banshee:988): GStreamer-CRITICAL **: gst_element_query: assertion `GST_IS_ELEMENT (element)' failed

(Banshee:988): GStreamer-CRITICAL **: gst_element_query: assertion `GST_IS_ELEMENT (element)' failed

(Banshee:988): GStreamer-CRITICAL **: gst_element_query: assertion `GST_IS_ELEMENT (element)' failed

*** libdvdread: CHECK_VALUE failed in nav_read.c:264 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:264 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:264 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:264 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:264 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:264 ***
*** for dsi->dsi_gi.zero1 == 0 ***


** (Banshee:988): CRITICAL **: bp_get_subtitle_description: assertion `code != NULL' failed

*** libdvdread: CHECK_VALUE failed in nav_read.c:264 ***
*** for dsi->dsi_gi.zero1 == 0 ***

The program 'Banshee' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 44 error_code 11 request_code 149 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
adam@gondor:~$ 

```

It looks like I need to mount the DVD to see it in the browser panel, but that requires extra interaction with xubuntu outside Banshee. I assumed it would have the same handling as a music CD, i.e. you shouldn't bother mounting it - is that so?

---

### Post by adam-hardy on 2013-08-03
it was the video drivers.

[http://askubuntu.com/questions/320437/banshee-crashing-unable-to-list-a-dvd-in-its-browser-panel-on-xubuntu](http://askubuntu.com/questions/320437/banshee-crashing-unable-to-list-a-dvd-in-its-browser-panel-on-xubuntu)

---

