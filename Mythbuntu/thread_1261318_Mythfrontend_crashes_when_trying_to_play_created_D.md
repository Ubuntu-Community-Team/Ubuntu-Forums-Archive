---
title: "Mythfrontend crashes when trying to play created DVD folder"
date: 2009-09-08
forum: Mythbuntu
---

### Post by bcg30506 on 2009-09-08
I created a DVD image using mytharchive.  I did not check create ISO nor burn to disc as I wanted to test it first as I always do before burning and didn't want to spend the time waiting for mkisofs.  I then use the Play Created DVD menu item under Archive Utilities in the frontend.  This has worked well in the past.  Now every time I try it, the frontend app crashes and leaves me on my Desktop.  If I rsync the created dvd directory structure to another machine and play it with another program, it is fine.  Here is the log file activity:
```
libdvdnav: Using dvdnav version 0.1.10-xine from http://xine.sf.net
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/me/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
2009-09-08 15:43:06.831 Opened DVD device at /monolith/tmp/work/dvd/
2009-09-08 15:43:06.831 There are 2 titles on the disk
2009-09-08 15:43:06.831 Title 0 has 0 parts.
2009-09-08 15:43:06.831 Title 1 has 8 parts.
2009-09-08 15:43:06.845 Connecting to backend server: 192.168.7.210:6543 (try 1 of 5)
2009-09-08 15:43:06.846 Using protocol version 40
2009-09-08 15:43:06.877 TV: Attempting to change from None to WatchingPreRecorded
libdvdnav: Using dvdnav version 0.1.10-xine from http://xine.sf.net
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/me/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
2009-09-08 15:43:06.880 Opened DVD device at /monolith/tmp/work/dvd/
2009-09-08 15:43:06.880 There are 2 titles on the disk
2009-09-08 15:43:06.880 Title 0 has 0 parts.
2009-09-08 15:43:06.880 Title 1 has 8 parts.
2009-09-08 15:43:06.979 DPMS Deactivated 
2009-09-08 15:43:07.919 AFD: Opened codec 0x9526290, id(MPEGVIDEO_VDPAU) type(Video)
2009-09-08 15:43:07.919 NVP: Disabling Audio, params(-1,-1,-1)
2009-09-08 15:43:09.660 OSD Theme Dimensions W: 1280 H: 720
2009-09-08 15:43:09.718 Unknown altfont: infofont in textarea: callsign
2009-09-08 15:43:09.893 TV: Changing from None to WatchingPreRecorded
2009-09-08 15:43:09.894 New DB connection, total: 3
2009-09-08 15:43:09.901 Connected to database 'mythconverg' at host: 192.168.7.210

```
That's it.  It ends there until I restart the frontend and get the messages from it starting back up.  Any ideas?

---

### Post by azmyth on 2009-09-10
This has been fixed in the trunk. When I was using 0.21, once the myth intro hit I'd start hitting the right arrow as this would bypass whatever was causing the frontend to crash.

---

