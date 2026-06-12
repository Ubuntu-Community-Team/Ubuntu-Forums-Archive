---
title: "can't play DVDs"
date: 2008-06-16
forum: Multimedia Software
---

### Post by melenor on 2008-06-16
I have tried all kinds of move players totem and all others say "An error occurred Could not read from resource" i installed totem Xine and it got the first one to play but then said "An error occurred the source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?" but i have installed libdvdcss already, and doing that i had gotten the first one to play but then that happens. I just want to play a DVD and when i used a terminal it came up with this

libdvdnav: Using dvdnav version 1.1.11.1 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/scd0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/overlord/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000658f2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0006dfbd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00366a79
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
libdvdnav: Using dvdnav version 1.1.11.1 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/scd0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/user/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.

thanks for any help.

---

### Post by Pjotr123 on 2008-06-16
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

---

### Post by melenor on 2008-06-16
thanks it was the w64codecs and regionset

---

