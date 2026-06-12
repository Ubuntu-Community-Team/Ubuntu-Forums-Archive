---
title: "Issue with DVD playback"
date: 2008-05-23
forum: Mythbuntu
---

### Post by DucoNihilum on 2008-05-23
When I try to go to Optical Disks and play a DVD, the screen simply flashes. I tried opening up the frontend in the terminal to get error messages, and this is what I got. What can I do to fix this?

```
libdvdnav: Using dvdnav version 0.1.10-xine from http://xine.sf.net
libdvdread: Encrypted DVD support unavailable.
libdvdnav: DVD Title: NOC0NNW1
libdvdnav: DVD Serial Number: 378f425a
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/ducodihilum/.dvdnav/NOC0NNW1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
2008-05-23 16:33:38.011 Opened DVD device at //dev/dvd
2008-05-23 16:33:38.011 There are 29 titles on the disk
2008-05-23 16:33:38.011 Title 0 has 0 parts.
2008-05-23 16:33:38.011 Title 1 has 1 parts.
2008-05-23 16:33:38.012 Title 2 has 1 parts.
2008-05-23 16:33:38.012 Title 3 has 1 parts.
2008-05-23 16:33:38.012 Title 4 has 17 parts.
2008-05-23 16:33:38.012 Title 5 has 1 parts.
2008-05-23 16:33:38.012 Title 6 has 3 parts.
2008-05-23 16:33:38.012 Title 7 has 2 parts.
2008-05-23 16:33:38.012 Title 8 has 2 parts.
2008-05-23 16:33:38.012 Title 9 has 1 parts.
2008-05-23 16:33:38.012 Title 10 has 1 parts.
2008-05-23 16:33:38.012 Title 11 has 1 parts.
2008-05-23 16:33:38.012 Title 12 has 1 parts.
2008-05-23 16:33:38.013 Title 13 has 1 parts.
2008-05-23 16:33:38.013 Title 14 has 6 parts.
2008-05-23 16:33:38.013 Title 15 has 2 parts.
2008-05-23 16:33:38.013 Title 16 has 2 parts.
2008-05-23 16:33:38.013 Title 17 has 2 parts.
2008-05-23 16:33:38.013 Title 18 has 2 parts.
2008-05-23 16:33:38.013 Title 19 has 1 parts.
2008-05-23 16:33:38.013 Title 20 has 1 parts.
2008-05-23 16:33:38.013 Title 21 has 1 parts.
2008-05-23 16:33:38.013 Title 22 has 1 parts.
2008-05-23 16:33:38.013 Title 23 has 1 parts.
2008-05-23 16:33:38.014 Title 24 has 1 parts.
2008-05-23 16:33:38.014 Title 25 has 5 parts.
2008-05-23 16:33:38.014 Title 26 has 2 parts.
2008-05-23 16:33:38.014 Title 27 has 2 parts.
2008-05-23 16:33:38.014 Title 28 has 2 parts.
2008-05-23 16:33:42.041 NVP: Couldn't find a matching decoder for: //dev/dvd
2008-05-23 16:33:42.041 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2008-05-23 16:33:42.041 TV: Changing from None to WatchingPreRecorded
2008-05-23 16:33:42.044 TV: Attempting to change from WatchingPreRecorded to None
2008-05-23 16:33:42.047 TV: Changing from WatchingPreRecorded to None
2008-05-23 16:33:44.943 TV: Attempting to change from None to WatchingPreRecorded
libdvdnav: Using dvdnav version 0.1.10-xine from http://xine.sf.net
libdvdread: Encrypted DVD support unavailable.
libdvdnav: DVD Title: NOC0NNW1
libdvdnav: DVD Serial Number: 378f425a
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/ducodihilum/.dvdnav/NOC0NNW1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
2008-05-23 16:33:44.968 Opened DVD device at //dev/dvd
2008-05-23 16:33:44.969 There are 29 titles on the disk
2008-05-23 16:33:44.969 Title 0 has 0 parts.
2008-05-23 16:33:44.969 Title 1 has 1 parts.
2008-05-23 16:33:44.969 Title 2 has 1 parts.
2008-05-23 16:33:44.969 Title 3 has 1 parts.
2008-05-23 16:33:44.969 Title 4 has 17 parts.
2008-05-23 16:33:44.984 Title 5 has 1 parts.
2008-05-23 16:33:44.984 Title 6 has 3 parts.
2008-05-23 16:33:44.985 Title 7 has 2 parts.
2008-05-23 16:33:44.985 Title 8 has 2 parts.
2008-05-23 16:33:44.985 Title 9 has 1 parts.
2008-05-23 16:33:44.985 Title 10 has 1 parts.
2008-05-23 16:33:44.985 Title 11 has 1 parts.
2008-05-23 16:33:44.985 Title 12 has 1 parts.
2008-05-23 16:33:44.985 Title 13 has 1 parts.
2008-05-23 16:33:44.985 Title 14 has 6 parts.
2008-05-23 16:33:44.985 Title 15 has 2 parts.
2008-05-23 16:33:44.985 Title 16 has 2 parts.
2008-05-23 16:33:44.985 Title 17 has 2 parts.
2008-05-23 16:33:44.986 Title 18 has 2 parts.
2008-05-23 16:33:44.986 Title 19 has 1 parts.
2008-05-23 16:33:44.986 Title 20 has 1 parts.
2008-05-23 16:33:44.986 Title 21 has 1 parts.
2008-05-23 16:33:44.986 Title 22 has 1 parts.
2008-05-23 16:33:44.986 Title 23 has 1 parts.
2008-05-23 16:33:44.986 Title 24 has 1 parts.
2008-05-23 16:33:44.986 Title 25 has 5 parts.
2008-05-23 16:33:44.986 Title 26 has 2 parts.
2008-05-23 16:33:44.986 Title 27 has 2 parts.
2008-05-23 16:33:44.986 Title 28 has 2 parts.
2008-05-23 16:33:45.026 NVP: Couldn't find a matching decoder for: //dev/dvd
2008-05-23 16:33:45.027 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2008-05-23 16:33:45.027 TV: Changing from None to WatchingPreRecorded
2008-05-23 16:33:45.028 TV: Attempting to change from WatchingPreRecorded to None
2008-05-23 16:33:45.030 TV: Changing from WatchingPreRecorded to None
-s /media/cdrom0 /dev/dvd
2008-05-23 16:35:58.190 TV: Attempting to change from None to WatchingPreRecorded
libdvdnav: Using dvdnav version 0.1.10-xine from http://xine.sf.net
libdvdread: Encrypted DVD support unavailable.
libdvdnav: DVD Title: NOC0NNW1
libdvdnav: DVD Serial Number: 378f425a
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/ducodihilum/.dvdnav/NOC0NNW1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
2008-05-23 16:35:58.483 Opened DVD device at //dev/dvd
2008-05-23 16:35:58.484 There are 29 titles on the disk
2008-05-23 16:35:58.484 Title 0 has 0 parts.
2008-05-23 16:35:58.484 Title 1 has 1 parts.
2008-05-23 16:35:58.484 Title 2 has 1 parts.
2008-05-23 16:35:58.486 Title 3 has 1 parts.
2008-05-23 16:35:58.486 Title 4 has 17 parts.
2008-05-23 16:35:58.486 Title 5 has 1 parts.
2008-05-23 16:35:58.486 Title 6 has 3 parts.
2008-05-23 16:35:58.486 Title 7 has 2 parts.
2008-05-23 16:35:58.486 Title 8 has 2 parts.
2008-05-23 16:35:58.486 Title 9 has 1 parts.
2008-05-23 16:35:58.486 Title 10 has 1 parts.
2008-05-23 16:35:58.486 Title 11 has 1 parts.
2008-05-23 16:35:58.487 Title 12 has 1 parts.
2008-05-23 16:35:58.487 Title 13 has 1 parts.
2008-05-23 16:35:58.487 Title 14 has 6 parts.
2008-05-23 16:35:58.487 Title 15 has 2 parts.
2008-05-23 16:35:58.487 Title 16 has 2 parts.
2008-05-23 16:35:58.487 Title 17 has 2 parts.
2008-05-23 16:35:58.487 Title 18 has 2 parts.
2008-05-23 16:35:58.487 Title 19 has 1 parts.
2008-05-23 16:35:58.487 Title 20 has 1 parts.
2008-05-23 16:35:58.487 Title 21 has 1 parts.
2008-05-23 16:35:58.487 Title 22 has 1 parts.
2008-05-23 16:35:58.488 Title 23 has 1 parts.
2008-05-23 16:35:58.488 Title 24 has 1 parts.
2008-05-23 16:35:58.488 Title 25 has 5 parts.
2008-05-23 16:35:58.488 Title 26 has 2 parts.
2008-05-23 16:35:58.488 Title 27 has 2 parts.
2008-05-23 16:35:58.488 Title 28 has 2 parts.
2008-05-23 16:36:02.481 NVP: Couldn't find a matching decoder for: //dev/dvd
2008-05-23 16:36:02.482 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2008-05-23 16:36:02.482 TV: Changing from None to WatchingPreRecorded
2008-05-23 16:36:02.484 TV: Attempting to change from WatchingPreRecorded to None
2008-05-23 16:36:02.498 TV: Changing from WatchingPreRecorded to None
2008-05-23 16:36:04.996 TV: Attempting to change from None to WatchingPreRecorded
libdvdnav: Using dvdnav version 0.1.10-xine from http://xine.sf.net
libdvdread: Encrypted DVD support unavailable.
libdvdnav: DVD Title: NOC0NNW1
libdvdnav: DVD Serial Number: 378f425a
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/ducodihilum/.dvdnav/NOC0NNW1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
2008-05-23 16:36:05.021 Opened DVD device at //dev/dvd
2008-05-23 16:36:05.021 There are 29 titles on the disk
2008-05-23 16:36:05.021 Title 0 has 0 parts.
2008-05-23 16:36:05.021 Title 1 has 1 parts.
2008-05-23 16:36:05.022 Title 2 has 1 parts.
2008-05-23 16:36:05.022 Title 3 has 1 parts.
2008-05-23 16:36:05.022 Title 4 has 17 parts.
2008-05-23 16:36:05.022 Title 5 has 1 parts.
2008-05-23 16:36:05.022 Title 6 has 3 parts.
2008-05-23 16:36:05.022 Title 7 has 2 parts.
2008-05-23 16:36:05.022 Title 8 has 2 parts.
2008-05-23 16:36:05.022 Title 9 has 1 parts.
2008-05-23 16:36:05.022 Title 10 has 1 parts.
2008-05-23 16:36:05.022 Title 11 has 1 parts.
2008-05-23 16:36:05.022 Title 12 has 1 parts.
2008-05-23 16:36:05.023 Title 13 has 1 parts.
2008-05-23 16:36:05.023 Title 14 has 6 parts.
2008-05-23 16:36:05.023 Title 15 has 2 parts.
2008-05-23 16:36:05.023 Title 16 has 2 parts.
2008-05-23 16:36:05.023 Title 17 has 2 parts.
2008-05-23 16:36:05.023 Title 18 has 2 parts.
2008-05-23 16:36:05.023 Title 19 has 1 parts.
2008-05-23 16:36:05.023 Title 20 has 1 parts.
2008-05-23 16:36:05.023 Title 21 has 1 parts.
2008-05-23 16:36:05.023 Title 22 has 1 parts.
2008-05-23 16:36:05.023 Title 23 has 1 parts.
2008-05-23 16:36:05.024 Title 24 has 1 parts.
2008-05-23 16:36:05.024 Title 25 has 5 parts.
2008-05-23 16:36:05.024 Title 26 has 2 parts.
2008-05-23 16:36:05.024 Title 27 has 2 parts.
2008-05-23 16:36:05.024 Title 28 has 2 parts.
2008-05-23 16:36:05.106 NVP: Couldn't find a matching decoder for: //dev/dvd
2008-05-23 16:36:05.106 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2008-05-23 16:36:05.111 TV: Changing from None to WatchingPreRecorded
2008-05-23 16:36:05.113 TV: Attempting to change from WatchingPreRecorded to None
2008-05-23 16:36:05.126 TV: Changing from WatchingPreRecorded to None


```

---

### Post by Trollslayer on 2008-05-24
Search for **libdvdcss2** and **libdvdread**.

---

