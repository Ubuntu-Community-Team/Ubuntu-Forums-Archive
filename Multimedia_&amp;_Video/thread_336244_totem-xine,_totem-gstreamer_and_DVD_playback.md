---
title: "totem-xine, totem-gstreamer and DVD playback"
date: 2007-01-11
forum: Multimedia &amp; Video
---

### Post by SirYes on 2007-01-11
This is strange. After recent updates on Ubuntu 6.10/x86 **totem-xine** refused to play DVDs. Respective error was:
```
$ totem
libdvdnav: Using dvdnav version 1.1.2 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Attempting to use device /dev/hdd mounted on /media/cdrom0 for CSS authentication
libdvdread: Couldn't find device name.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/gocha/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8

*** libdvdread: CHECK_VALUE failed in ifo_read.c:974 ***
*** for n % 4 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:356 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:356 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:356 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:356 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:356 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:356 ***
*** for dsi->dsi_gi.zero1 == 0 ***


** (totem:5223): CRITICAL **: totem_lang_table_parse_start_tag: assertion `strlen (*attr_values) == 3' failed

*** libdvdread: CHECK_VALUE failed in nav_read.c:356 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:356 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:356 ***
*** for dsi->dsi_gi.zero1 == 0 ***

libdvdnav: Using dvdnav version 1.1.2 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Attempting to use device /dev/hdd mounted on /media/cdrom0 for CSS authentication
libdvdread: Couldn't find device name.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/user/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8

```
I always followed the [RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs") guide. I do have all required packages (like w32codecs and libdvdcss2) and all was working well (for months!)

Additionally, I was able to repeat the problem on two different Ubuntu Edgy installations (which download and install updates independently).

I solved the problem by removing **totem-xine** in favor of **totem-streamer**, and DVD playback is fine since then. However I'd like to ask if anybody has observed such behaviour?

---

